# OpenEyes Technical Workflow Design Document
## Philippine Tertiary Ophthalmology Implementation

**Version**: 1.0  
**Date**: February 2026  
**Audience**: DevOps engineers, backend developers, system architects  
**Context**: Tertiary eye care facility (Philippines) with department-owned server, mesh VPN, intermittent internet, limited IT support

---

## 1. SYSTEM OVERVIEW

### 1.1 Deployment Architecture

The system operates in a **resource-constrained, intermittently-connected environment** with the following constraints:

| Constraint | Implication | Design Response |
|-----------|------------|-----------------|
| **No hospital IT support** | Department-owned server; no dedicated IT staff | Simplified deployment; automated backups; self-service troubleshooting |
| **Intermittent internet** | Cannot rely on cloud connectivity | Offline-first architecture; local data storage; asynchronous sync |
| **Limited workstations** | Personal devices (resident/consultant laptops) via mesh VPN | Lightweight client; mesh VPN integration; multi-device support |
| **Department-owned server** | Second-hand business CPU; limited resources | Minimal server footprint; efficient database design; local caching |
| **Power outages** | Electricity unreliable | Graceful degradation; local data persistence; minimal state on server |
| **Limited bandwidth** | Intermittent, low-speed connections | Compressed data transfer; batch operations; offline-first workflows |

### 1.2 Core System Components

```
┌─────────────────────────────────────────────────────────────────┐
│                    OpenEyes Philippine Edition                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                   │
│  ┌──────────────────┐         ┌──────────────────┐              │
│  │  Client Layer    │         │  Mesh VPN        │              │
│  │  (Workstations)  │◄────────┤  (Access Layer)  │              │
│  │                  │         │                  │              │
│  │ • Web App        │         │ • Device Auth    │              │
│  │ • Local Cache    │         │ • Encryption     │              │
│  │ • Offline Mode   │         │ • Routing        │              │
│  └──────────────────┘         └──────────────────┘              │
│           │                                                      │
│           │ (HTTP/HTTPS)                                        │
│           ▼                                                      │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │         Application Server (Department Server)           │   │
│  │                                                          │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │   │
│  │  │ API Layer    │  │ Sync Engine  │  │ Auth Service │  │   │
│  │  │              │  │              │  │              │  │   │
│  │  │ • REST API   │  │ • Conflict   │  │ • Mesh VPN   │  │   │
│  │  │ • Event Bus  │  │   Resolution │  │ • Local Auth │  │   │
│  │  │ • Webhooks   │  │ • Batch Sync │  │ • Audit Log  │  │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  │   │
│  │                                                          │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │   │
│  │  │ Coding Engine│  │ Offline Mgmt │  │ Backup Mgmt  │  │   │
│  │  │              │  │              │  │              │  │   │
│  │  │ • SNOMED→ICD │  │ • Local DB   │  │ • Incremental│  │   │
│  │  │ • Procedure→ │  │ • Sync Queue │  │ • Versioning│  │   │
│  │  │   RVS        │  │ • Conflict   │  │ • Restore    │  │   │
│  │  │ • Validation │  │   Log        │  │ • Encryption │  │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  │   │
│  └──────────────────────────────────────────────────────────┘   │
│           │                                                      │
│           │ (JDBC/Native)                                       │
│           ▼                                                      │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │         Data Layer (Local Database)                      │   │
│  │                                                          │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │   │
│  │  │ Patient DB   │  │ Clinical DB  │  │ Config DB    │  │   │
│  │  │              │  │              │  │              │  │   │
│  │  │ • Patients   │  │ • Encounters │  │ • ICD-10 Map │  │   │
│  │  │ • Contact    │  │ • Exams      │  │ • RVS Map    │  │   │
│  │  │ • Insurance  │  │ • Procedures │  │ • Drug List  │  │   │
│  │  │ • Billing    │  │ • Imaging    │  │ • Workflows  │  │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  │   │
│  │                                                          │   │
│  │  ┌──────────────────────────────────────────────────┐   │   │
│  │  │ Sync Log (Offline Change Tracking)               │   │   │
│  │  │ • Pending changes (when offline)                 │   │   │
│  │  │ • Sync status (queued, synced, failed)           │   │   │
│  │  │ • Conflict resolution log                        │   │   │
│  │  └──────────────────────────────────────────────────┘   │   │
│  └──────────────────────────────────────────────────────────┘   │
│           │                                                      │
│           │ (Optional: External Integration)                    │
│           ▼                                                      │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │         External Integration Layer (When Online)         │   │
│  │                                                          │   │
│  │  • PhilHealth eClaims API (batch submission)            │   │
│  │  • National Health Insurance database                   │   │
│  │  • Pharmacy supplier APIs (if available)                │   │
│  │  • Laboratory information systems (if available)        │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                   │
└─────────────────────────────────────────────────────────────────┘
```

### 1.3 Deployment Model

**Primary Deployment**: Single department-owned server running OpenEyes application server and local database.

**Access Model**: 
- Residents and consultants access via personal workstations (laptops)
- Connection via mesh VPN (e.g., Tailscale, Wireguard)
- Fallback to direct IP access if VPN unavailable
- Satellite clinic accesses via same mesh VPN or periodic data sync

**Data Storage**:
- Primary: Local database on department server (PostgreSQL or MySQL)
- Backup: Encrypted external drive (manual weekly backup)
- Offline cache: Local browser storage on each workstation (IndexedDB or SQLite)

**Internet Connectivity**:
- Used for: PhilHealth eClaims submission, external API calls, software updates
- Not required for: Clinical workflows, patient data access, local reporting
- Batch operations: Sync and eClaims submission when connectivity available

---

## 2. ACTOR DIAGRAM (TEXTUAL)

### 2.1 System Actors and Interactions

```
┌─────────────────────────────────────────────────────────────────┐
│                      SYSTEM ACTORS                              │
└─────────────────────────────────────────────────────────────────┘

CLINICAL ACTORS (Primary System Users)
├─ Ophthalmologist (Consultant)
│  ├─ Initiates: Examinations, diagnoses, treatment plans
│  ├─ Performs: Procedures (laser, surgery)
│  ├─ Reviews: Resident examinations, imaging reports
│  ├─ Assigns: ICD-10 codes, RVS codes
│  └─ Accesses: All patient data, all workflows
│
├─ Ophthalmology Resident
│  ├─ Performs: Initial examinations, pre-operative workup
│  ├─ Records: Clinical findings, measurements
│  ├─ Requests: Imaging, procedures
│  ├─ Requires: Consultant review/approval for procedures
│  └─ Accesses: Patient data, examination templates
│
├─ Ophthalmic Nurse
│  ├─ Performs: Pre-examination (VA, IOP)
│  ├─ Prepares: Patients for procedures
│  ├─ Records: Vital signs, patient education
│  ├─ Assists: Procedures, inpatient care
│  └─ Accesses: Patient data, procedure schedules
│
├─ Ophthalmic Technician
│  ├─ Operates: Diagnostic equipment (OCT, VF, biometry)
│  ├─ Acquires: Images and measurements
│  ├─ Records: Test parameters, image quality
│  ├─ Performs: Laser procedures (under supervision)
│  └─ Accesses: Patient data, imaging storage
│
├─ Orthoptist
│  ├─ Performs: Visual field testing, orthoptic evaluation
│  ├─ Records: Test results, measurements
│  ├─ Assists: Specialist examinations
│  └─ Accesses: Patient data, test templates
│
└─ Patient
   ├─ Provides: History, symptoms, consent
   ├─ Receives: Diagnosis, treatment plan, education
   ├─ Accesses: (Optional) Patient portal for appointments, results
   └─ Interacts: With all clinical staff

ADMINISTRATIVE ACTORS (Supporting Users)
├─ Receptionist/Clerical Staff
│  ├─ Performs: Patient registration, appointment scheduling
│  ├─ Records: Demographics, contact information
│  ├─ Manages: Appointment calendar
│  ├─ Prints: Appointment cards, referral forms
│  └─ Accesses: Patient registry, appointment system
│
├─ Billing Officer
│  ├─ Performs: PhilHealth claim preparation
│  ├─ Assigns: ICD-10 and RVS codes (verification)
│  ├─ Submits: eClaims (when online)
│  ├─ Tracks: Claim status, denials, reimbursement
│  ├─ Calculates: Patient charges, payment collection
│  └─ Accesses: Encounter data, coding tables, claim system
│
├─ IT Administrator
│  ├─ Manages: Server, database, backups
│  ├─ Maintains: Mesh VPN, network connectivity
│  ├─ Performs: System updates, troubleshooting
│  ├─ Monitors: System health, data integrity
│  ├─ Manages: User access, authentication
│  └─ Accesses: All system components, logs, configuration
│
└─ Department Head
   ├─ Reviews: Workflow compliance, quality metrics
   ├─ Approves: PhilHealth accreditation requirements
   ├─ Manages: Resource allocation, staff scheduling
   ├─ Oversees: System configuration, policy updates
   └─ Accesses: Administrative dashboards, reports

EXTERNAL ACTORS (System Integrations)
├─ PhilHealth System
│  ├─ Receives: eClaims (ICD-10 + RVS codes)
│  ├─ Validates: Claim format, codes, patient eligibility
│  ├─ Returns: Claim status, approval/denial
│  └─ Integration: Batch API calls (when online)
│
├─ Satellite Clinic
│  ├─ Receives: Referral data, patient records
│  ├─ Sends: Examination data, imaging
│  ├─ Syncs: Patient data (periodic or on-demand)
│  └─ Integration: Data sync protocol (manual or automated)
│
├─ Pharmacy Supplier
│  ├─ Receives: Medication orders (optional)
│  ├─ Provides: Drug availability, pricing
│  └─ Integration: Optional API or manual lookup
│
└─ Laboratory System
   ├─ Receives: Test orders (optional)
   ├─ Provides: Test results
   └─ Integration: Optional API or manual entry

┌─────────────────────────────────────────────────────────────────┐
│                    ACTOR INTERACTION MATRIX                     │
└─────────────────────────────────────────────────────────────────┘

                    ┌─────────────────────────────────────────┐
                    │      Data Flow Direction                │
                    ├─────────────────────────────────────────┤
Consultant          │ ◄─ Resident, Nurse, Tech, Patient      │
                    │ ─► Resident, Patient, Billing Officer  │
                    │                                         │
Resident            │ ◄─ Consultant, Nurse, Tech, Patient    │
                    │ ─► Consultant, Nurse, Patient          │
                    │                                         │
Nurse               │ ◄─ Consultant, Resident, Patient       │
                    │ ─► Consultant, Resident, Tech, Patient │
                    │                                         │
Technician          │ ◄─ Consultant, Resident, Patient       │
                    │ ─► Consultant, Resident, Nurse         │
                    │                                         │
Billing Officer     │ ◄─ Consultant, Resident, Receptionist  │
                    │ ─► PhilHealth, Patient                 │
                    │                                         │
Receptionist        │ ◄─ Patient, Billing Officer            │
                    │ ─► Patient, Consultant, Billing Officer│
                    │                                         │
IT Administrator    │ ◄─ All actors (logs, monitoring)       │
                    │ ─► All actors (system availability)    │
                    └─────────────────────────────────────────┘
```

### 2.2 Role-Based Access Control (RBAC)

The system implements role-based access control with the following permission model:

| Role | Patient Data | Clinical Data | Imaging | Billing | System Config | Notes |
|------|---|---|---|---|---|---|
| **Consultant** | Full | Full | Full | Read | Read | Lead clinician; all clinical decisions |
| **Resident** | Full | Full (own + supervised) | Full | Read | None | Supervised; can't approve own exams |
| **Nurse** | Full | Limited (vital signs, prep) | Limited | None | None | Pre-exam and procedure support |
| **Technician** | Limited (ID only) | Limited (imaging only) | Full | None | None | Diagnostic equipment operation |
| **Orthoptist** | Limited (ID only) | Limited (VF tests) | Limited | None | None | Vision testing specialist |
| **Receptionist** | Limited (demo only) | None | None | Limited | None | Registration and scheduling |
| **Billing Officer** | Limited (demo + insurance) | Limited (codes only) | None | Full | None | Claims and billing |
| **IT Admin** | Full (audit only) | Full (audit only) | Full (audit only) | Full (audit only) | Full | System maintenance; audit trail |
| **Department Head** | None | Read (reports only) | None | Read (reports only) | Read | Administrative oversight |

---

## 3. CORE WORKFLOWS

### 3.1 Workflow State Machine

Each clinical workflow follows a state machine pattern with defined transitions and data requirements:

```
┌─────────────────────────────────────────────────────────────────┐
│              UNIVERSAL WORKFLOW STATE MACHINE                   │
└─────────────────────────────────────────────────────────────────┘

                        ┌──────────────┐
                        │   CREATED    │
                        │ (Initial)    │
                        └──────┬───────┘
                               │
                    (Validation passed)
                               │
                        ┌──────▼───────┐
                        │   PENDING    │
                        │ (Awaiting    │
                        │  execution)  │
                        └──────┬───────┘
                               │
                    (Execution started)
                               │
                        ┌──────▼───────┐
                        │   IN_PROGRESS│
                        │ (Being       │
                        │  executed)   │
                        └──────┬───────┘
                               │
                    (Execution completed)
                               │
                        ┌──────▼───────┐
                        │   COMPLETED  │
                        │ (Success)    │
                        └──────┬───────┘
                               │
                    (Billing/coding)
                               │
                        ┌──────▼───────┐
                        │   BILLED     │
                        │ (PhilHealth  │
                        │  claim ready)│
                        └──────────────┘

ALTERNATIVE PATHS:
- CREATED ──(Validation failed)──► REJECTED
- IN_PROGRESS ──(Error)──► FAILED ──(Retry)──► IN_PROGRESS
- COMPLETED ──(Complication)──► AMENDED
- Any state ──(User cancels)──► CANCELLED
```

### 3.2 New Patient Consultation Workflow

**Workflow ID**: `WF_NEW_CONSULT`  
**Actors**: Receptionist, Nurse, Resident/Consultant, Billing Officer  
**Data Objects**: Encounter, Patient, Observation, Condition, CarePlan  
**PhilHealth Billable**: Yes (consultation + diagnostics)

**State Transitions**:

```
REGISTRATION
├─ State: CREATED
├─ Input: Patient demographics, referral source
├─ Validation: Required fields present
├─ Output: Patient record created, appointment assigned
└─ Next: PRE_EXAMINATION

PRE_EXAMINATION
├─ State: IN_PROGRESS
├─ Actors: Nurse, Technician (if available)
├─ Measurements: VA, IOP, vital signs
├─ Optional: Photography, OCT (if available)
├─ Storage: Observations linked to encounter
├─ Fallback: Manual recording if system unavailable
└─ Next: CLINICAL_EXAMINATION

CLINICAL_EXAMINATION
├─ State: IN_PROGRESS
├─ Actor: Resident or Consultant
├─ Examination: Slit lamp, posterior segment
├─ Optional: Dilation (if indicated and safe)
├─ Documentation: Structured clinical note
├─ EyeDraw: Optional; text description acceptable
├─ Fallback: Handwritten notes if system unavailable
└─ Next: DIAGNOSIS_PLANNING

DIAGNOSIS_PLANNING
├─ State: IN_PROGRESS
├─ Actor: Consultant (if resident performed exam)
├─ Tasks:
│  ├─ Review examination findings
│  ├─ Formulate working diagnosis
│  ├─ Assign ICD-10 primary diagnosis code
│  ├─ Document secondary diagnoses (if any)
│  ├─ Determine management pathway
│  └─ Assign RVS code (if procedure planned)
├─ Validation: ICD-10 code valid; RVS code (if applicable) valid
├─ Fallback: Manual coding if system unavailable
└─ Next: PATIENT_COMMUNICATION

PATIENT_COMMUNICATION
├─ State: IN_PROGRESS
├─ Actor: Consultant
├─ Tasks:
│  ├─ Explain diagnosis in understandable terms
│  ├─ Discuss treatment options with costs
│  ├─ Obtain informed consent (verbal acceptable)
│  ├─ Provide patient education (if available)
│  └─ Document consent in notes
├─ Fallback: Verbal communication with documentation
└─ Next: PAYMENT_SCHEDULING

PAYMENT_SCHEDULING
├─ State: IN_PROGRESS
├─ Actor: Billing Officer, Receptionist
├─ Tasks:
│  ├─ Determine payment method (PhilHealth/OOP/Mixed)
│  ├─ Explain charges for consultation + diagnostics
│  ├─ Collect payment (advance or post-visit)
│  ├─ Assign PhilHealth claim (if eligible)
│  └─ Schedule follow-up appointment
├─ Fallback: Manual payment record if system unavailable
└─ Next: COMPLETED

COMPLETED
├─ State: COMPLETED
├─ Encounter closed; ready for billing
├─ All required data captured
└─ Next: BILLED (when PhilHealth claim submitted)
```

**Data Capture Requirements**:

| Phase | Data Object | Required Fields | Optional Fields | Storage |
|-------|---|---|---|---|
| Registration | Patient | Name, DOB, Sex, Address, Contact | Insurance, Employer | Patient table |
| Pre-exam | Observation | VA (both eyes), IOP (both eyes), BP, HR, Temp | Photography, OCT | Observation table |
| Exam | Encounter | Examination findings, EyeDraw (or text) | Dilated exam notes | Encounter table |
| Diagnosis | Condition | ICD-10 code, description, onset date | Secondary diagnoses | Condition table |
| Plan | CarePlan | Management pathway, medications, follow-up | Procedure plan | CarePlan table |
| Billing | PhilHealthClaim | ICD-10 code, RVS code (if applicable), charges | Insurance details | Claim table |

**Offline Considerations**:

- All data entry occurs on local workstation; syncs to server when online
- Pre-exam measurements recorded locally; synced when online
- Diagnosis and coding can occur offline; synced when online
- PhilHealth claim queued for submission when online
- Paper backup: All steps have manual documentation alternative

**Error Handling**:

| Error | Handling |
|-------|----------|
| Patient not found in system | Create new patient record; proceed with registration |
| ICD-10 code invalid | Display validation error; suggest alternatives from lookup table |
| RVS code invalid | Display validation error; suggest alternatives from lookup table |
| Payment collection fails | Allow visit to proceed; flag for billing follow-up |
| System unavailable | Fall back to paper-based documentation; manual entry when online |

---

### 3.3 Follow-up Consultation Workflow

**Workflow ID**: `WF_FOLLOWUP_CONSULT`  
**Actors**: Receptionist, Nurse, Resident/Consultant, Billing Officer  
**Data Objects**: Encounter, Observation, Condition, MedicationStatement, CarePlan  
**PhilHealth Billable**: Yes (consultation; additional diagnostics if performed)

**State Transitions**:

```
APPOINTMENT_VERIFICATION
├─ State: CREATED
├─ Input: Patient ID, appointment date
├─ Lookup: Prior encounters, current medications, baseline findings
├─ Validation: Patient exists; prior encounter found
├─ Output: Prior encounter data retrieved; ready for comparison
└─ Next: INTERVAL_HISTORY

INTERVAL_HISTORY
├─ State: IN_PROGRESS
├─ Actor: Nurse or Resident
├─ Data Collection:
│  ├─ Symptom changes since last visit
│  ├─ Medication compliance (if prescribed)
│  ├─ Medication side effects (if reported)
│  ├─ Affordability issues (if present)
│  └─ Vital signs (BP, HR, Temp)
├─ Storage: Interval history linked to encounter
└─ Next: TARGETED_EXAMINATION

TARGETED_EXAMINATION
├─ State: IN_PROGRESS
├─ Actor: Resident or Consultant
├─ Examination: Focused on relevant findings from prior visit
├─ Measurements: VA, IOP (if clinically indicated)
├─ Imaging: Repeat OCT/VF (if indicated and available)
├─ Documentation: Structured clinical note
├─ Comparison: Prior findings retrieved for side-by-side review
└─ Next: CLINICAL_ASSESSMENT

CLINICAL_ASSESSMENT
├─ State: IN_PROGRESS
├─ Actor: Consultant
├─ Analysis:
│  ├─ Compare current to baseline findings
│  ├─ Determine disease trajectory (stable/improving/worsening)
│  ├─ Assess treatment efficacy
│  └─ Identify complications (if any)
├─ Decision: Continue/modify/escalate treatment
└─ Next: PLAN_MODIFICATION

PLAN_MODIFICATION
├─ State: IN_PROGRESS
├─ Actor: Consultant
├─ Tasks:
│  ├─ Update diagnosis (if changed)
│  ├─ Adjust medications (if needed)
│  ├─ Schedule procedures (if indicated)
│  ├─ Assign updated ICD-10 code (if diagnosis changed)
│  ├─ Assign RVS code (if procedure planned)
│  └─ Discuss costs with patient
├─ Validation: Codes valid; plan documented
└─ Next: PAYMENT_SCHEDULING

PAYMENT_SCHEDULING
├─ State: IN_PROGRESS
├─ Actor: Billing Officer, Receptionist
├─ Tasks:
│  ├─ Collect payment for current visit
│  ├─ Arrange payment for planned procedures
│  ├─ Assign PhilHealth claim (if eligible)
│  └─ Schedule next appointment
├─ Fallback: Manual payment record if system unavailable
└─ Next: COMPLETED

COMPLETED
├─ State: COMPLETED
├─ Encounter closed; ready for billing
├─ All required data captured
└─ Next: BILLED (when PhilHealth claim submitted)
```

**Comparison Logic**:

The system implements a comparison engine that retrieves prior encounter data and enables side-by-side analysis:

```
COMPARISON_ENGINE
├─ Input: Current encounter ID, prior encounter ID
├─ Retrieval:
│  ├─ Prior observations (VA, IOP, OCT measurements)
│  ├─ Prior diagnosis (ICD-10 code)
│  ├─ Prior imaging (if digitized)
│  └─ Prior medications
├─ Processing:
│  ├─ Calculate change in measurements (VA, IOP, OCT thickness)
│  ├─ Determine trend (improving/stable/worsening)
│  ├─ Flag significant changes (>5% change in OCT, >3 mmHg IOP change)
│  └─ Identify new findings
├─ Output:
│  ├─ Comparison report (text or visual)
│  ├─ Trend analysis
│  ├─ Flagged changes
│  └─ Recommendations for management
└─ Fallback: Manual comparison if prior data not digitized
```

---

### 3.4 PhilHealth Claim Workflow

**Workflow ID**: `WF_PHILHEALTH_CLAIM`  
**Actors**: Billing Officer, Consultant (coding verification)  
**Data Objects**: Encounter, Condition, Procedure, PhilHealthClaim  
**Trigger**: Encounter completed; ready for billing  
**Output**: eClaims submission (when online) or queued for submission

**State Transitions**:

```
DATA_EXTRACTION
├─ State: CREATED
├─ Input: Completed encounter record
├─ Extraction:
│  ├─ Patient demographics (name, DOB, PhilHealth ID)
│  ├─ Encounter date and type
│  ├─ Diagnosis (ICD-10 code)
│  ├─ Procedures (RVS codes, if any)
│  ├─ Imaging/diagnostics (RVS codes, if any)
│  ├─ Charges (consultation, procedures, imaging)
│  └─ Insurance information
├─ Validation: All required fields present
└─ Next: CODING_VERIFICATION

CODING_VERIFICATION
├─ State: IN_PROGRESS
├─ Actor: Billing Officer (with Consultant review if needed)
├─ Verification:
│  ├─ ICD-10 code matches diagnosis (lookup table validation)
│  ├─ RVS code matches procedure (lookup table validation)
│  ├─ Charges align with PhilHealth rates (if applicable)
│  ├─ Patient PhilHealth eligibility verified
│  └─ No duplicate claims for same encounter
├─ Validation: All codes valid; no errors
├─ Error Handling: Invalid codes → suggest alternatives from lookup table
└─ Next: CLAIM_ASSEMBLY

CLAIM_ASSEMBLY
├─ State: IN_PROGRESS
├─ Actor: Billing Officer
├─ Assembly:
│  ├─ Populate PhilHealth eClaims form (or paper form if offline)
│  ├─ Include all required fields per PhilHealth specification
│  ├─ Attach supporting documentation (if required):
│  │  ├─ Operative notes (for procedures)
│  │  ├─ Imaging reports (for imaging procedures)
│  │  └─ Pathology reports (if applicable)
│  ├─ Calculate total charges
│  ├─ Verify form completeness
│  └─ Generate claim ID (internal tracking)
├─ Validation: Form complete; all required fields present
└─ Next: SUBMISSION_QUEUE

SUBMISSION_QUEUE
├─ State: PENDING
├─ Storage: Claim queued in submission queue (local database)
├─ Trigger: Internet connectivity available
├─ Retry Logic: 
│  ├─ Retry failed submissions (max 3 attempts)
│  ├─ Exponential backoff (1 min, 5 min, 15 min)
│  └─ Alert on persistent failures
└─ Next: SUBMISSION

SUBMISSION
├─ State: IN_PROGRESS
├─ Trigger: Internet connectivity available
├─ Action: Submit claim via PhilHealth eClaims API
├─ Request: POST to PhilHealth endpoint with claim data
├─ Response: Claim ID, validation status, errors (if any)
├─ Retry: On network error or server error (5xx)
├─ Error Handling:
│  ├─ Validation error (4xx) → Correct and resubmit
│  ├─ Network error → Retry when online
│  └─ Server error (5xx) → Retry with backoff
└─ Next: SUBMITTED or FAILED

SUBMITTED
├─ State: SUBMITTED
├─ Storage: Claim ID recorded; submission timestamp recorded
├─ Status: Awaiting PhilHealth processing
├─ Next: TRACKING

FAILED
├─ State: FAILED
├─ Storage: Error details recorded
├─ Action: Alert billing officer; flag for manual review
├─ Retry: Manual retry after correction
└─ Next: SUBMISSION_QUEUE (after correction)

TRACKING
├─ State: IN_PROGRESS
├─ Polling: Query PhilHealth API for claim status (daily)
├─ Status Updates:
│  ├─ APPROVED → Claim accepted; reimbursement pending
│  ├─ DENIED → Claim rejected; reason recorded
│  ├─ PENDING → Claim under review
│  └─ AMENDED → Claim requires amendment
├─ Denial Handling:
│  ├─ Record denial reason
│  ├─ Alert billing officer
│  ├─ Prepare amendment (if applicable)
│  └─ Resubmit amended claim
└─ Next: COMPLETED (when approved or denied final)

COMPLETED
├─ State: COMPLETED
├─ Final Status: Approved, Denied, or Amended
├─ Reimbursement: Tracked separately
└─ Archive: Claim record retained for audit
```

**Coding Lookup Tables**:

The system maintains local lookup tables for ICD-10 and RVS codes:

```
ICD-10_LOOKUP_TABLE
├─ Columns: ICD10_CODE, DESCRIPTION, SNOMED_CODE, ACTIVE
├─ Example Rows:
│  ├─ H25.9 | Unspecified cataract | 3841006 | TRUE
│  ├─ H40.9 | Unspecified glaucoma | 23986001 | TRUE
│  ├─ E11.3 | Type 2 diabetes with eye complications | 44054006 | TRUE
│  └─ H35.3 | Diabetic retinopathy | 4855003 | TRUE
├─ Updates: Manual or via API (when online)
└─ Validation: Lookup on code assignment; reject if not found

RVS_LOOKUP_TABLE
├─ Columns: RVS_CODE, DESCRIPTION, PROCEDURE_TYPE, RATE_PHP, ACTIVE
├─ Example Rows:
│  ├─ 99213 | Office visit, established patient | CONSULTATION | 500 | TRUE
│  ├─ 66840 | Removal of lens material; aspiration technique | CATARACT_SURGERY | 15000 | TRUE
│  ├─ 92004 | Comprehensive eye exam, new patient | EXAMINATION | 800 | TRUE
│  └─ 76512 | Ophthalmic ultrasound, B-scan | IMAGING | 1200 | TRUE
├─ Updates: Manual or via API (when online)
└─ Validation: Lookup on code assignment; reject if not found

SNOMED_TO_ICD10_MAPPING
├─ Columns: SNOMED_CODE, ICD10_CODE, MAPPING_TYPE, CONFIDENCE
├─ Example Rows:
│  ├─ 3841006 | H25.9 | EXACT | HIGH
│  ├─ 23986001 | H40.9 | EXACT | HIGH
│  ├─ 4855003 | H35.3 | EXACT | HIGH
│  └─ 44054006 | E11.3 | APPROXIMATE | MEDIUM
├─ Usage: Automatic SNOMED→ICD-10 conversion
├─ Fallback: Manual selection if no mapping found
└─ Updates: Manual or via API (when online)
```

**Offline Claim Preparation**:

The system supports offline claim preparation with queued submission:

```
OFFLINE_CLAIM_WORKFLOW
├─ Phase 1: Data Entry (Offline)
│  ├─ Billing officer extracts encounter data
│  ├─ Assigns ICD-10 and RVS codes (using local lookup tables)
│  ├─ Populates claim form (local database)
│  ├─ Generates internal claim ID
│  └─ Stores in SUBMISSION_QUEUE table
│
├─ Phase 2: Waiting for Connectivity
│  ├─ Claim remains in SUBMISSION_QUEUE
│  ├─ Status: PENDING
│  └─ No action required
│
├─ Phase 3: Online Submission (When Connectivity Available)
│  ├─ System detects internet connectivity
│  ├─ Retrieves all pending claims from SUBMISSION_QUEUE
│  ├─ Submits each claim via PhilHealth eClaims API
│  ├─ Records submission timestamp and claim ID
│  ├─ Moves claim to SUBMITTED status
│  └─ Begins polling for status updates
│
└─ Phase 4: Status Tracking
   ├─ Daily polling of PhilHealth API
   ├─ Updates claim status (APPROVED, DENIED, PENDING, AMENDED)
   ├─ Alerts on denials or amendments
   └─ Tracks reimbursement
```

---

### 3.5 Laser Procedure Workflow

**Workflow ID**: `WF_LASER_PROCEDURE`  
**Actors**: Consultant, Nurse, Technician  
**Data Objects**: Encounter, Procedure, Observation  
**PhilHealth Billable**: Yes (RVS code assigned)

**State Transitions**:

```
PRE_LASER_ASSESSMENT
├─ State: CREATED
├─ Actor: Consultant
├─ Tasks:
│  ├─ Confirm diagnosis and indication
│  ├─ Assess suitability for laser
│  ├─ Identify target tissue
│  ├─ Plan laser parameters (wavelength, power, duration, spot size)
│  └─ Assign RVS procedure code
├─ Validation: Indication valid; RVS code valid
├─ Output: Procedure plan created
└─ Next: PATIENT_PREPARATION

PATIENT_PREPARATION
├─ State: IN_PROGRESS
├─ Actor: Nurse
├─ Tasks:
│  ├─ Verify patient identity
│  ├─ Verify procedure type
│  ├─ Obtain informed consent (verbal acceptable; documented)
│  ├─ Instill topical anesthesia (if available)
│  ├─ Position patient at laser
│  └─ Apply contact lens (if required)
├─ Fallback: Manual consent form if system unavailable
└─ Next: LASER_DELIVERY

LASER_DELIVERY
├─ State: IN_PROGRESS
├─ Actor: Consultant
├─ Tasks:
│  ├─ Align laser beam to target tissue
│  ├─ Apply laser energy per planned parameters
│  ├─ Monitor tissue response (visual inspection)
│  ├─ Adjust parameters if needed (optional)
│  ├─ Document extent of treatment (number of burns, location, parameters)
│  └─ Record any complications
├─ Data Capture:
│  ├─ Laser parameters (wavelength, power, duration, spot size)
│  ├─ Number of burns/applications
│  ├─ Treatment location (right eye, left eye, specific area)
│  ├─ Tissue response (appearance, color change)
│  └─ Complications (if any)
├─ Fallback: Manual documentation if system unavailable
└─ Next: POST_LASER_ASSESSMENT

POST_LASER_ASSESSMENT
├─ State: IN_PROGRESS
├─ Actor: Consultant
├─ Tasks:
│  ├─ Evaluate immediate response
│  ├─ Check for immediate complications
│  ├─ Instill post-operative medications (if available)
│  └─ Provide post-operative instructions
├─ Complications Recorded:
│  ├─ Corneal abrasion
│  ├─ Hyphema
│  ├─ Iris burn
│  ├─ Retinal burn (if inadvertent)
│  └─ Other
└─ Next: POST_OPERATIVE_CARE

POST_OPERATIVE_CARE
├─ State: IN_PROGRESS
├─ Actor: Nurse
├─ Tasks:
│  ├─ Provide post-operative instructions
│  ├─ Schedule follow-up examination (1-4 weeks)
│  ├─ Provide written instructions (if available)
│  └─ Record follow-up appointment
├─ Fallback: Verbal instructions with documentation
└─ Next: BILLING

BILLING
├─ State: IN_PROGRESS
├─ Actor: Billing Officer
├─ Tasks:
│  ├─ Collect payment for procedure
│  ├─ Assign PhilHealth RVS code
│  ├─ Create PhilHealth claim (if eligible)
│  └─ Queue for submission (when online)
├─ Fallback: Manual payment record if system unavailable
└─ Next: COMPLETED

COMPLETED
├─ State: COMPLETED
├─ Procedure documented; ready for billing
├─ All required data captured
└─ Next: BILLED (when PhilHealth claim submitted)
```

**Laser Parameter Validation**:

The system validates laser parameters against safe ranges:

```
LASER_PARAMETER_VALIDATION
├─ Wavelength: Valid for laser type (e.g., 532nm for green laser)
├─ Power: Within safe range for tissue type
│  ├─ Retinal photocoagulation: 100-500 mW
│  ├─ Iridotomy: 1000-2000 mW
│  └─ Cyclophotocoagulation: 1000-2000 mW
├─ Duration: Within safe range (typically 10-200 ms)
├─ Spot Size: Appropriate for target tissue
│  ├─ Retinal photocoagulation: 50-500 μm
│  ├─ Iridotomy: 50-100 μm
│  └─ Cyclophotocoagulation: 50-100 μm
├─ Number of Burns: Logged and tracked
├─ Treatment Area: Documented (right eye, left eye, specific location)
└─ Validation: Alert if parameters outside safe range
```

---

## 4. DATA LIFECYCLE

### 4.1 Data Model Overview

The system implements a normalized relational data model optimized for clinical workflows and PhilHealth compliance:

```
CORE DATA ENTITIES
├─ Patient (patient demographics, insurance, contact)
├─ Encounter (visit/admission record)
├─ Observation (measurements: VA, IOP, vital signs)
├─ Condition (diagnosis with ICD-10 code)
├─ Procedure (surgical/laser procedure with RVS code)
├─ Medication (medication prescription and dispensing)
├─ DiagnosticReport (imaging report with findings)
├─ ImagingStudy (imaging metadata and files)
├─ CarePlan (management plan, follow-up)
├─ PhilHealthClaim (claim record with codes and status)
└─ SyncLog (offline change tracking)

SUPPORTING ENTITIES
├─ User (staff member with role and permissions)
├─ Appointment (scheduled appointment)
├─ Referral (referral to other facility)
├─ Device (diagnostic equipment)
├─ Organization (facility information)
└─ AuditLog (system audit trail)
```

### 4.2 Data Flow Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                   DATA FLOW: NEW PATIENT CONSULT                │
└─────────────────────────────────────────────────────────────────┘

1. REGISTRATION
   ┌──────────────────┐
   │ Receptionist     │
   │ (Workstation 1)  │
   └────────┬─────────┘
            │ (Input: Name, DOB, Contact)
            ▼
   ┌──────────────────────────────────────┐
   │ LOCAL CACHE (IndexedDB)              │
   │ ├─ Patient record (temporary)        │
   │ └─ Sync status: PENDING              │
   └────────┬─────────────────────────────┘
            │ (Sync when online)
            ▼
   ┌──────────────────────────────────────┐
   │ SERVER DATABASE                      │
   │ ├─ Patient table (INSERT)            │
   │ ├─ Generate Patient ID               │
   │ └─ Sync log entry (SYNCED)           │
   └──────────────────────────────────────┘

2. PRE-EXAMINATION
   ┌──────────────────┐
   │ Nurse            │
   │ (Workstation 2)  │
   └────────┬─────────┘
            │ (Input: VA, IOP, BP, HR, Temp)
            ▼
   ┌──────────────────────────────────────┐
   │ LOCAL CACHE (IndexedDB)              │
   │ ├─ Observation record (temporary)    │
   │ └─ Sync status: PENDING              │
   └────────┬─────────────────────────────┘
            │ (Sync when online)
            ▼
   ┌──────────────────────────────────────┐
   │ SERVER DATABASE                      │
   │ ├─ Observation table (INSERT)        │
   │ ├─ Link to Encounter                 │
   │ └─ Sync log entry (SYNCED)           │
   └──────────────────────────────────────┘

3. CLINICAL EXAMINATION
   ┌──────────────────┐
   │ Resident         │
   │ (Workstation 3)  │
   └────────┬─────────┘
            │ (Input: Slit lamp findings, posterior exam)
            ▼
   ┌──────────────────────────────────────┐
   │ LOCAL CACHE (IndexedDB)              │
   │ ├─ Encounter record (temporary)      │
   │ ├─ Clinical notes (text)             │
   │ └─ Sync status: PENDING              │
   └────────┬─────────────────────────────┘
            │ (Sync when online)
            ▼
   ┌──────────────────────────────────────┐
   │ SERVER DATABASE                      │
   │ ├─ Encounter table (INSERT/UPDATE)   │
   │ ├─ Store clinical notes              │
   │ └─ Sync log entry (SYNCED)           │
   └──────────────────────────────────────┘

4. DIAGNOSIS & CODING
   ┌──────────────────┐
   │ Consultant       │
   │ (Workstation 1)  │
   └────────┬─────────┘
            │ (Input: Diagnosis, ICD-10 code)
            ▼
   ┌──────────────────────────────────────┐
   │ LOCAL CACHE (IndexedDB)              │
   │ ├─ Condition record (temporary)      │
   │ ├─ ICD-10 code (lookup validated)    │
   │ └─ Sync status: PENDING              │
   └────────┬─────────────────────────────┘
            │ (Sync when online)
            ▼
   ┌──────────────────────────────────────┐
   │ SERVER DATABASE                      │
   │ ├─ Condition table (INSERT)          │
   │ ├─ ICD-10 code stored                │
   │ └─ Sync log entry (SYNCED)           │
   └──────────────────────────────────────┘

5. BILLING & CLAIMS
   ┌──────────────────┐
   │ Billing Officer  │
   │ (Workstation 4)  │
   └────────┬─────────┘
            │ (Input: Payment method, PhilHealth ID)
            ▼
   ┌──────────────────────────────────────┐
   │ LOCAL CACHE (IndexedDB)              │
   │ ├─ PhilHealthClaim record (temp)     │
   │ ├─ Codes validated (ICD-10, RVS)     │
   │ ├─ Sync status: PENDING              │
   │ └─ Submission status: QUEUED         │
   └────────┬─────────────────────────────┘
            │ (Sync when online)
            ▼
   ┌──────────────────────────────────────┐
   │ SERVER DATABASE                      │
   │ ├─ PhilHealthClaim table (INSERT)    │
   │ ├─ Submission queue entry            │
   │ └─ Sync log entry (SYNCED)           │
   └────────┬─────────────────────────────┘
            │ (When internet available)
            ▼
   ┌──────────────────────────────────────┐
   │ PHILHEALTH ECLAIMS API               │
   │ ├─ POST claim data                   │
   │ ├─ Receive claim ID                  │
   │ └─ Update claim status: SUBMITTED    │
   └──────────────────────────────────────┘
```

### 4.3 Sync Protocol (Offline-First)

The system implements a robust sync protocol for offline-first operation:

```
SYNC_PROTOCOL
├─ Trigger: Internet connectivity detected
├─ Phase 1: Conflict Detection
│  ├─ Query local SYNC_LOG for PENDING changes
│  ├─ Query server for changes since last sync
│  ├─ Identify conflicts (same record modified locally and on server)
│  └─ Log conflicts for manual resolution
│
├─ Phase 2: Conflict Resolution
│  ├─ Strategy 1: Last-write-wins (default)
│  │  └─ Server version overwrites local if server is newer
│  ├─ Strategy 2: Manual resolution (for critical data)
│  │  └─ Alert user; present both versions; user selects
│  └─ Strategy 3: Merge (for certain data types)
│     └─ Combine changes (e.g., medication list)
│
├─ Phase 3: Upload Local Changes
│  ├─ For each PENDING change in SYNC_LOG:
│  │  ├─ Serialize to JSON
│  │  ├─ POST to server API
│  │  ├─ On success: Mark as SYNCED in SYNC_LOG
│  │  ├─ On conflict: Mark as CONFLICT; alert user
│  │  └─ On error: Retry with exponential backoff
│  └─ Batch uploads (max 100 changes per batch)
│
├─ Phase 4: Download Server Changes
│  ├─ Query server for changes since last sync
│  ├─ For each server change:
│  │  ├─ Check for local conflicts
│  │  ├─ If no conflict: Update local cache
│  │  ├─ If conflict: Apply resolution strategy
│  │  └─ Update SYNC_LOG
│  └─ Batch downloads (max 1000 records per batch)
│
├─ Phase 5: Completion
│  ├─ Update last sync timestamp
│  ├─ Log sync completion
│  ├─ Alert user of any conflicts or errors
│  └─ Trigger UI refresh if needed
│
└─ Error Handling:
   ├─ Network error: Retry on next connectivity
   ├─ Server error (5xx): Retry with exponential backoff
   ├─ Validation error (4xx): Alert user; manual correction needed
   └─ Conflict: Alert user; present resolution options
```

### 4.4 Data Retention and Archival

The system implements a data retention policy compliant with Philippine healthcare regulations:

```
DATA_RETENTION_POLICY
├─ Active Records (Patients with ongoing care)
│  ├─ Retention: Indefinite (or until patient requests deletion)
│  ├─ Location: Primary database + backup
│  └─ Access: Full access for authorized users
│
├─ Inactive Records (No visit in 5+ years)
│  ├─ Retention: 10 years (per PhilHealth requirement)
│  ├─ Location: Archive database (read-only)
│  ├─ Access: Limited access (audit only)
│  └─ Compression: Compressed to reduce storage
│
├─ Deleted Records (Patient requests deletion)
│  ├─ Retention: 7 years (per data protection law)
│  ├─ Location: Encrypted archive (separate from active data)
│  ├─ Access: No access (audit trail only)
│  └─ Purge: Automatic deletion after 7 years
│
├─ Audit Logs
│  ├─ Retention: 3 years (per PhilHealth requirement)
│  ├─ Location: Separate audit database
│  ├─ Access: IT admin and department head only
│  └─ Compression: Compressed after 1 year
│
└─ Backup Retention
   ├─ Daily backups: 7 days
   ├─ Weekly backups: 4 weeks
   ├─ Monthly backups: 12 months
   └─ Encryption: All backups encrypted
```

---

## 5. INTEGRATION POINTS

### 5.1 PhilHealth eClaims Integration

**Endpoint**: PhilHealth eClaims API (batch submission)  
**Authentication**: PhilHealth credentials (facility ID, password)  
**Protocol**: HTTPS POST  
**Frequency**: Daily (when online)

**Request Format**:

```json
{
  "facility_id": "PH-FACILITY-12345",
  "claims": [
    {
      "claim_id": "LOCAL-CLAIM-001",
      "patient_id": "PH-PATIENT-98765",
      "patient_name": "Juan Dela Cruz",
      "patient_dob": "1960-05-15",
      "encounter_date": "2026-02-06",
      "diagnosis_codes": ["H25.9"],
      "procedure_codes": ["99213"],
      "charges": 1500.00,
      "insurance_id": "PH-INSURANCE-55555"
    }
  ]
}
```

**Response Format**:

```json
{
  "status": "SUCCESS",
  "claims_processed": 1,
  "claims_approved": 1,
  "claims_denied": 0,
  "results": [
    {
      "claim_id": "LOCAL-CLAIM-001",
      "philhealth_claim_id": "PH-CLAIM-99999",
      "status": "APPROVED",
      "approved_amount": 1200.00
    }
  ]
}
```

**Error Handling**:

| Error Code | Meaning | Handling |
|-----------|---------|----------|
| 400 | Invalid request format | Log error; alert billing officer; manual correction needed |
| 401 | Authentication failed | Check credentials; alert IT admin |
| 403 | Facility not authorized | Check facility accreditation; alert department head |
| 404 | Patient not found in PhilHealth system | Verify patient ID; manual correction needed |
| 422 | Validation error (invalid codes, etc.) | Log error; suggest corrections; resubmit |
| 500 | Server error | Retry with exponential backoff |
| 503 | Service unavailable | Retry when service available |

### 5.2 Satellite Clinic Data Sync

**Sync Method**: Periodic data export/import (manual or automated)  
**Frequency**: Daily (or on-demand)  
**Protocol**: Encrypted file transfer (SFTP or secure email)

**Data Sync Workflow**:

```
SATELLITE_CLINIC_SYNC
├─ Phase 1: Export from Tertiary Center
│  ├─ Query: Encounters since last sync
│  ├─ Include: Patient data, encounter data, imaging (if small)
│  ├─ Exclude: Sensitive data (passwords, audit logs)
│  ├─ Format: JSON or CSV
│  ├─ Encryption: Encrypt with shared key
│  └─ Transfer: SFTP or secure email
│
├─ Phase 2: Import at Satellite Clinic
│  ├─ Receive: Encrypted file
│  ├─ Decrypt: Using shared key
│  ├─ Validate: Check data integrity
│  ├─ Merge: Integrate with local database
│  ├─ Conflict Resolution: Last-write-wins
│  └─ Notification: Alert staff of new data
│
├─ Phase 3: Export from Satellite Clinic
│  ├─ Query: Encounters since last sync
│  ├─ Include: Patient data, examination data, imaging (if small)
│  ├─ Format: JSON or CSV
│  ├─ Encryption: Encrypt with shared key
│  └─ Transfer: SFTP or secure email
│
└─ Phase 4: Import at Tertiary Center
   ├─ Receive: Encrypted file
   ├─ Decrypt: Using shared key
   ├─ Validate: Check data integrity
   ├─ Merge: Integrate with central database
   ├─ Conflict Resolution: Last-write-wins
   └─ Notification: Alert staff of new data
```

### 5.3 Mesh VPN Integration

**VPN Software**: Tailscale or Wireguard (recommended)  
**Authentication**: Device-based (no user credentials)  
**Encryption**: End-to-end encrypted tunnel

**Configuration**:

```
MESH_VPN_CONFIGURATION
├─ Server (Department Server)
│  ├─ VPN IP: 100.64.0.1 (Tailscale subnet)
│  ├─ Port: 41641 (Wireguard) or auto (Tailscale)
│  ├─ Firewall: Allow only OpenEyes port (8080 or 443)
│  └─ Monitoring: Alert on VPN disconnection
│
├─ Client (Workstations)
│  ├─ VPN IP: 100.64.0.x (assigned per device)
│  ├─ Connection: Auto-connect on startup
│  ├─ Fallback: Direct IP access if VPN unavailable
│  └─ Monitoring: Display VPN status in UI
│
└─ Security
   ├─ Key rotation: Automatic (Tailscale) or manual (Wireguard)
   ├─ Access control: Device-based ACL
   ├─ Audit: Log all VPN connections
   └─ Incident response: Revoke device keys if compromised
```

### 5.4 External APIs (Optional)

The system can integrate with external APIs when available:

| API | Purpose | Trigger | Frequency |
|-----|---------|---------|-----------|
| **PhilHealth eClaims** | Claim submission | Encounter completed | Daily (when online) |
| **PhilHealth Eligibility** | Verify patient coverage | Patient registration | On-demand |
| **Pharmacy Supplier** | Check drug availability | Prescription creation | On-demand |
| **Laboratory System** | Submit test orders | Test ordered | On-demand |
| **National Health Insurance** | Verify insurance status | Patient registration | On-demand |

---

## 6. CONFIGURATION VS CUSTOMIZATION

### 6.1 Configuration (No Code Changes)

Configuration allows adaptation to local context without code changes:

| Configuration Item | Options | Default | Impact |
|---|---|---|---|
| **Facility Name** | Text | "Department of Ophthalmology" | UI display, reports |
| **Facility Address** | Text | "" | Patient communication, referrals |
| **PhilHealth Facility ID** | Text | "" | eClaims submission |
| **Consultation Fee** | Currency | 500 PHP | Billing, patient communication |
| **Procedure Fees** | Table | Per RVS code | Billing, patient communication |
| **ICD-10 Codes** | Lookup table | Standard ICD-10 | Diagnosis coding |
| **RVS Codes** | Lookup table | Standard RVS | Procedure coding |
| **Drug Formulary** | Lookup table | Common ophthalmology drugs | Medication prescribing |
| **Appointment Slots** | Time slots | 08:00-17:00 | Scheduling |
| **Follow-up Intervals** | Days | Diagnosis-specific | Appointment scheduling |
| **PhilHealth Submission Schedule** | Cron expression | Daily at 02:00 | eClaims submission |
| **Backup Schedule** | Cron expression | Daily at 23:00 | Data protection |
| **Language** | English, Filipino | English | UI display |

### 6.2 Customization (Code Changes)

Customization requires code changes and should be minimized:

| Customization | Reason | Effort | Risk |
|---|---|---|---|
| **Custom workflow** | Department-specific process | High | High |
| **Custom data field** | Additional data capture | Medium | Medium |
| **Custom report** | Department-specific reporting | Medium | Low |
| **Custom integration** | External system integration | High | High |
| **Custom UI** | Department-specific interface | High | High |

**Recommendation**: Use configuration for all possible adaptations; reserve customization for truly unique requirements.

### 6.3 Configuration File Format

Configuration stored in JSON format (version-controlled):

```json
{
  "facility": {
    "name": "Department of Ophthalmology",
    "address": "123 Health Street, Metro Manila",
    "philhealth_facility_id": "PH-FACILITY-12345",
    "contact": "+63-2-1234-5678"
  },
  "billing": {
    "consultation_fee_php": 500,
    "currency": "PHP",
    "philhealth_submission_enabled": true,
    "procedure_fees": {
      "99213": 500,
      "66840": 15000,
      "92004": 800
    }
  },
  "coding": {
    "icd10_lookup_table": "icd10_ph.csv",
    "rvs_lookup_table": "rvs_ph.csv",
    "snomed_to_icd10_mapping": "snomed_icd10_mapping.csv"
  },
  "scheduling": {
    "clinic_hours_start": "08:00",
    "clinic_hours_end": "17:00",
    "appointment_slot_duration_minutes": 30,
    "default_followup_intervals": {
      "cataract": 7,
      "glaucoma": 14,
      "diabetic_retinopathy": 30
    }
  },
  "system": {
    "language": "en",
    "timezone": "Asia/Manila",
    "backup_schedule": "0 23 * * *",
    "philhealth_submission_schedule": "0 2 * * *"
  }
}
```

---

## 7. LOCALIZATION TOUCHPOINTS

### 7.1 Language Localization

The system supports multiple languages via localization framework:

| Touchpoint | English | Filipino | Notes |
|---|---|---|---|
| **UI Labels** | "Visual Acuity" | "Paningin" | Consistent terminology |
| **Menu Items** | "New Patient" | "Bagong Pasyente" | Clear navigation |
| **Error Messages** | "Invalid ICD-10 code" | "Hindi wastong ICD-10 code" | Actionable feedback |
| **Patient Education** | English materials | Filipino materials | Culturally appropriate |
| **Reports** | English | Filipino | Bilingual reports |
| **Correspondence** | English | Filipino | Patient communication |

**Implementation**: Gettext or i18n framework; translation strings in separate files.

### 7.2 Terminology Localization

NHS terminology translated to Philippine healthcare context:

| NHS Term | Philippine Equivalent | Notes |
|---|---|---|
| **Consultant** | Oftalmólogo (Consultant) | Senior ophthalmologist |
| **Registrar** | Resident | Junior ophthalmologist in training |
| **SHO** | Intern | Medical graduate in training |
| **Nurse** | Nars | Registered nurse |
| **Technician** | Teknikal | Diagnostic equipment operator |
| **GP** | Pamilyang Doktor | General practitioner |
| **Referral** | Referral | Same concept |
| **Outpatient** | Outpatient | Same concept |
| **Inpatient** | Inpatient | Same concept |
| **Admission** | Admission | Same concept |
| **Discharge** | Discharge | Same concept |

### 7.3 Coding Localization

ICD-10 and RVS codes specific to Philippine context:

| Coding System | Localization | Source |
|---|---|---|
| **ICD-10** | WHO ICD-10 (English) | WHO official |
| **RVS** | Philippine RVS codes | PhilHealth official |
| **SNOMED CT** | SNOMED CT International (English) | SNOMED International |
| **Drug Names** | Philippine approved drug names | FDA Philippines |
| **Procedure Names** | Philippine standard procedure names | PhilHealth official |

### 7.4 Regulatory Localization

Philippine-specific regulatory requirements:

| Requirement | Implementation |
|---|---|
| **PhilHealth Accreditation** | Facility ID, credentials, compliance tracking |
| **PhilHealth eClaims Format** | ICD-10 + RVS codes, specific data fields |
| **Patient Privacy** | Data Privacy Act compliance, audit logging |
| **Medical Records** | Retention policy (10 years minimum) |
| **Informed Consent** | Simplified consent forms in Filipino |
| **Prescription Standards** | Philippine drug formulary, dosing standards |
| **Billing Standards** | PhilHealth rates, out-of-pocket tracking |

### 7.5 Cultural Localization

Adaptations for Philippine healthcare culture:

| Aspect | Adaptation |
|---|---|
| **Payment Methods** | Cash, PhilHealth, mixed (common in Philippines) |
| **Appointment Compliance** | High no-show rates expected; walk-in accommodation |
| **Follow-up Compliance** | Low follow-up rates expected; reminder system important |
| **Medication Affordability** | Cost discussion explicit; generic alternatives offered |
| **Specialist Availability** | Consultant may not be present daily; resident-led workflows |
| **Referral Pathways** | Informal pathways common; hand-carried referrals |
| **Patient Communication** | Simplified language; visual aids; family involvement |
| **Documentation** | Paper backup essential; handwritten notes acceptable |

---

## 8. IMPLEMENTATION ROADMAP

### Phase 1: Foundation (Weeks 1-4)
- Patient registration and appointment scheduling
- New patient consultation workflow
- Basic PhilHealth claim preparation
- Local database setup
- Mesh VPN configuration

### Phase 2: Clinical Support (Weeks 5-8)
- Follow-up consultation workflow
- Diagnostic imaging and testing
- Laser procedure workflow
- Offline sync implementation
- eClaims submission integration

### Phase 3: Advanced Workflows (Weeks 9-12)
- Minor and major surgical procedures
- Inpatient admission and management
- Emergency presentations
- Referral management
- Prescription management

### Phase 4: Optimization (Weeks 13-16)
- Performance optimization
- User interface refinement
- Staff training and documentation
- Pilot testing with real data
- Go-live preparation

---

## 9. DEPLOYMENT CHECKLIST

- [ ] Server hardware procured and configured
- [ ] Database installed and initialized
- [ ] Mesh VPN configured and tested
- [ ] Backup system configured and tested
- [ ] PhilHealth credentials obtained
- [ ] ICD-10 and RVS lookup tables loaded
- [ ] Drug formulary configured
- [ ] User accounts created and permissions set
- [ ] Staff training completed
- [ ] Pilot testing completed
- [ ] Go-live approval obtained
- [ ] Incident response plan documented

---

## 10. TROUBLESHOOTING GUIDE

### Common Issues

**Issue**: Offline sync fails after going online
- **Cause**: Network connectivity interrupted during sync
- **Solution**: Retry sync; check network connectivity; review sync logs

**Issue**: ICD-10 code not found in lookup table
- **Cause**: Code not in local lookup table; table not updated
- **Solution**: Update lookup table; use closest matching code; manual entry if necessary

**Issue**: PhilHealth claim rejected
- **Cause**: Invalid codes, patient not eligible, duplicate claim
- **Solution**: Review rejection reason; correct codes; verify patient eligibility; resubmit

**Issue**: Imaging files not syncing
- **Cause**: Large file size; network bandwidth limited
- **Solution**: Compress images; sync during off-peak hours; manual transfer if necessary

**Issue**: VPN disconnection
- **Cause**: Network instability; VPN server down
- **Solution**: Reconnect VPN; check network; use direct IP access as fallback

---

## 11. SECURITY CONSIDERATIONS

- **Authentication**: Mesh VPN device-based; local user authentication
- **Authorization**: Role-based access control (RBAC)
- **Encryption**: All data in transit encrypted (HTTPS, VPN); data at rest encrypted (database, backups)
- **Audit Logging**: All user actions logged; audit trail retained 3 years
- **Data Privacy**: Compliant with Philippine Data Privacy Act
- **Incident Response**: Documented procedure for security incidents
- **Backup Security**: Encrypted backups; separate storage location

---

## 12. PERFORMANCE TARGETS

- **Page Load Time**: < 2 seconds (local network)
- **API Response Time**: < 500ms (local network)
- **Sync Time**: < 5 minutes for typical workday data
- **Database Query Time**: < 1 second for typical queries
- **Concurrent Users**: Support 10 simultaneous users
- **Data Storage**: < 100GB for 5 years of data (with compression)

---

## 13. SUPPORT AND MAINTENANCE

- **IT Administrator**: On-call for system issues
- **Database Backups**: Automated daily; manual weekly verification
- **Software Updates**: Quarterly security updates; annual major updates
- **User Support**: In-person training; documentation; email support
- **Incident Response**: 24-hour response time for critical issues

---

## APPENDIX A: API ENDPOINTS

### Patient Management

```
GET /api/patients/{id}
POST /api/patients
PUT /api/patients/{id}
GET /api/patients?search=name
```

### Encounters

```
GET /api/encounters/{id}
POST /api/encounters
PUT /api/encounters/{id}
GET /api/encounters?patient_id={id}
```

### Observations

```
GET /api/observations/{id}
POST /api/observations
GET /api/observations?encounter_id={id}
```

### Conditions (Diagnoses)

```
GET /api/conditions/{id}
POST /api/conditions
GET /api/conditions?patient_id={id}
```

### PhilHealth Claims

```
GET /api/claims/{id}
POST /api/claims
PUT /api/claims/{id}/submit
GET /api/claims?status=PENDING
```

### Sync

```
POST /api/sync
GET /api/sync/status
```

---

## APPENDIX B: DATABASE SCHEMA

See separate database schema document (`DATABASE_SCHEMA.md`)

---

## APPENDIX C: CONFIGURATION EXAMPLES

See separate configuration examples document (`CONFIGURATION_EXAMPLES.md`)

---

**Document Version**: 1.0  
**Last Updated**: February 2026  
**Next Review**: August 2026

