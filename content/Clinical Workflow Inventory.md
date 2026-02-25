## Philippine Tertiary Ophthalmology Department (OpenEyes Context)

### **Scope**: 
Tertiary eye care facility with outpatient majority, diagnostic/laser center, 4-bed inpatient ward, and remote satellite clinic.

### **Methodology**: 
Workflows defined by clinical intent, separate from UI implementation. Data objects mapped to OpenEyes event-based architecture.

---

## 1. ACTORS

### Clinical Actors

| Actor | Role | Scope | Responsibilities |
|-------|------|-------|------------------|
| **Patient** | Care recipient | All workflows | Provides history, undergoes examination/treatment, receives care plan |
| **Ophthalmologist (Consultant)** | Primary clinician | All clinical workflows | Diagnosis, treatment planning, surgical decision-making, complex cases |
| **Ophthalmology Resident** | Junior clinician | Examination, diagnostics, follow-up | Initial examination, data entry, resident-supervised procedures |
| **Ophthalmic Nurse** | Clinical support | Examination, procedures, inpatient | Patient preparation, vital signs, procedure assistance, patient education |
| **Ophthalmic Technician** | Diagnostic specialist | Diagnostics, laser | Operates diagnostic equipment (OCT, visual fields, biometry), laser procedures |
| **Orthoptist** | Vision specialist | Examination, diagnostics | Vision assessment, orthoptic evaluation, visual field testing |

### Administrative Actors

| Actor | Role | Scope | Responsibilities |
|-------|------|-------|------------------|
| **Receptionist/Clerical Staff** | Front desk | Registration, scheduling | Patient registration, appointment booking, document management |
| **Billing Officer** | Financial admin | Billing, claims | PhilHealth claim preparation, fee calculation, reimbursement tracking |
| **IT/System Administrator** | Technical support | System maintenance | Server management, mesh VPN oversight, data backup, offline sync |
| **Department Head** | Leadership | Oversight | Workflow approval, resource allocation, PhilHealth compliance |

---

## 2. CORE CLINICAL JOURNEYS

### 2.1 New Patient Outpatient Consultation

**Clinical Intent**: Establish baseline eye health status, document presenting complaint, perform comprehensive examination, formulate initial diagnosis and management plan.

| Aspect | Details |
|--------|---------|
| **Purpose** | Complete ophthalmic assessment for new patient; establish baseline; rule out sight-threatening pathology |
| **Triggering Event** | Patient presents to reception with appointment or walk-in; registration completed |
| **Typical Duration** | 45-90 minutes (including diagnostics) |
| **Primary Actor** | Ophthalmologist or resident (supervised) |

**Inputs**:
- Patient demographics (name, age, contact, PhilHealth ID)
- Chief complaint/presenting symptom
- Referral source (if referred)
- Previous medical/surgical history (if available)

**Process Flow**:

1. **Pre-examination** (Nurse/Technician)
   - Vital signs (blood pressure, pulse, temperature)
   - Visual acuity measurement (both eyes, with/without correction)
   - Intraocular pressure (IOP) screening
   - Preliminary diagnostic imaging if indicated (OCT, fundus photography)

2. **Clinical Examination** (Ophthalmologist/Resident)
   - Anterior segment examination (slit lamp)
   - Posterior segment examination (dilated fundus exam)
   - Biometry if cataract suspected
   - Additional testing as indicated (visual fields, gonioscopy, etc.)

3. **Diagnosis & Planning** (Ophthalmologist)
   - Document findings using EyeDraw for anatomical notation
   - Formulate working diagnosis
   - Determine management pathway (medical, laser, surgical, referral)

4. **Patient Communication** (Ophthalmologist)
   - Explain diagnosis in understandable terms
   - Discuss treatment options
   - Obtain informed consent if procedure planned

**Outputs**:
- Examination event record (structured clinical note)
- EyeDraw diagrams (anterior/posterior segment findings)
- Diagnostic imaging results
- Management plan (medication, follow-up, procedure booking)
- PhilHealth-compliant diagnosis code (ICD-10)
- Patient education materials

**Data Objects Created**:
- `Encounter` (visit record)
- `Observation` (visual acuity, IOP, clinical findings)
- `Condition` (diagnosis with ICD-10 code)
- `CarePlan` (management recommendations)

**Clinical Workflow Diagram** (Conceptual):
```
Patient Arrival → Pre-exam (VA, IOP) → Examination → Diagnosis → Plan → Patient Counseling → Appointment/Referral
```

---

### 2.2 Follow-up/Review Consultation

**Clinical Intent**: Monitor disease progression, assess treatment response, adjust management, ensure compliance with care plan.

| Aspect | Details |
|--------|---------|
| **Purpose** | Track clinical course; assess intervention efficacy; modify treatment as needed |
| **Triggering Event** | Scheduled follow-up appointment or patient self-referral for symptoms |
| **Typical Duration** | 20-45 minutes |
| **Primary Actor** | Ophthalmologist or resident |

**Inputs**:
- Previous examination records (from current episode or prior visits)
- Interval history (symptoms, medication adherence, side effects)
- Previous imaging/diagnostics for comparison
- Current medications/treatments

**Process Flow**:

1. **Interval History** (Nurse/Resident)
   - Document symptom changes
   - Medication compliance assessment
   - Adverse effects inquiry

2. **Targeted Examination** (Ophthalmologist)
   - Focused on relevant findings from prior visit
   - Repeat key measurements (VA, IOP, OCT) for comparison
   - Assess treatment response

3. **Clinical Assessment** (Ophthalmologist)
   - Compare current findings to baseline/prior visits
   - Determine disease trajectory
   - Assess treatment efficacy

4. **Plan Modification** (Ophthalmologist)
   - Continue, modify, or escalate treatment
   - Adjust medication dosing/frequency
   - Schedule next intervention (laser, surgery, imaging)

**Outputs**:
- Follow-up examination event record
- Comparison analysis (prior vs. current findings)
- Updated management plan
- Medication adjustments (if applicable)
- Next appointment date
- PhilHealth claim data (if billable intervention)

**Data Objects Created**:
- `Encounter` (follow-up visit)
- `Observation` (repeat measurements with timestamps)
- `Condition` (updated diagnosis status)
- `MedicationStatement` (current medications)
- `CarePlan` (revised plan)

---

### 2.3 Diagnostic Imaging & Testing

**Clinical Intent**: Obtain objective quantitative data to support diagnosis, monitor disease, guide treatment decisions.

| Aspect | Details |
|--------|---------|
| **Purpose** | Capture diagnostic data (OCT, visual fields, biometry, fundus photography, etc.) for clinical decision-making |
| **Triggering Event** | Ordered during examination or as part of pre-operative workup |
| **Typical Duration** | 15-30 minutes per test |
| **Primary Actor** | Ophthalmic technician; interpreted by ophthalmologist |

**Inputs**:
- Patient identification
- Clinical indication for test
- Test parameters/protocol
- Prior imaging (if comparison needed)

**Process Flow**:

1. **Test Requisition** (Ophthalmologist/Resident)
   - Specify test type and clinical indication
   - Determine urgency

2. **Patient Preparation** (Technician)
   - Explain procedure to patient
   - Position patient at equipment
   - Perform calibration/alignment

3. **Image Acquisition** (Technician)
   - Capture images/data per protocol
   - Ensure image quality
   - Repeat if necessary

4. **Preliminary Review** (Technician)
   - Verify image quality
   - Flag obvious abnormalities

5. **Clinical Interpretation** (Ophthalmologist)
   - Analyze images/data
   - Compare to prior studies if available
   - Generate report with findings and recommendations

**Outputs**:
- Diagnostic imaging file (DICOM or proprietary format)
- Quantitative measurements (OCT thickness, visual field indices, biometry values)
- Interpreted report with clinical significance
- Recommendations for management

**Data Objects Created**:
- `DiagnosticReport` (imaging report with findings)
- `ImagingStudy` (imaging metadata and files)
- `Observation` (quantitative measurements from imaging)

**Common Tests in Philippine Tertiary Ophthalmology**:
- Optical Coherence Tomography (OCT) - retinal imaging
- Visual Field Testing (Humphrey, Goldmann) - glaucoma, neuro-ophthalmology
- A-scan/B-scan Biometry - cataract surgery planning
- Fundus Photography - documentation, diabetic retinopathy screening
- Anterior Segment Photography - corneal pathology, anterior chamber evaluation
- Gonioscopy - glaucoma angle assessment

---

### 2.4 Laser Procedure

**Clinical Intent**: Deliver therapeutic laser energy to ocular tissues for treatment (photocoagulation, iridotomy, cyclophotocoagulation, etc.).

| Aspect | Details |
|--------|---------|
| **Purpose** | Therapeutic intervention using laser technology (e.g., retinal photocoagulation for DR, PRP; iridotomy for angle closure) |
| **Triggering Event** | Planned during examination; documented in care plan |
| **Typical Duration** | 15-45 minutes |
| **Primary Actor** | Ophthalmologist (consultant or trained resident); technician support |

**Inputs**:
- Pre-operative examination findings
- Indication for laser (diagnosis, location, extent)
- Patient consent documentation
- Baseline imaging (OCT, fundus photos)
- Medication list (relevant for laser safety)

**Process Flow**:

1. **Pre-laser Assessment** (Ophthalmologist)
   - Confirm diagnosis and indication
   - Assess suitability for laser
   - Identify target tissue
   - Plan laser parameters (wavelength, power, duration, spot size)

2. **Patient Preparation** (Nurse/Technician)
   - Obtain informed consent
   - Instill topical anesthesia (if needed)
   - Position patient at laser
   - Apply contact lens (if required for procedure)

3. **Laser Delivery** (Ophthalmologist)
   - Align laser beam to target
   - Apply laser energy per protocol
   - Monitor tissue response
   - Adjust parameters as needed
   - Document extent of treatment

4. **Post-laser Assessment** (Ophthalmologist)
   - Evaluate immediate response
   - Check for complications
   - Instill post-operative medications

5. **Post-operative Care** (Nurse)
   - Provide post-operative instructions
   - Schedule follow-up imaging/examination

**Outputs**:
- Operation notes documenting laser parameters and extent
- EyeDraw diagrams showing treated areas
- Post-operative imaging (OCT, fundus photos)
- Complication assessment
- Follow-up plan
- PhilHealth RVS procedure code (e.g., 65820 for goniotomy; retinal photocoagulation codes)

**Data Objects Created**:
- `Procedure` (laser procedure record)
- `Observation` (laser parameters: wavelength, power, spots, duration)
- `Condition` (updated status post-procedure)
- `CarePlan` (post-operative follow-up)

**Common Laser Procedures**:
- Panretinal photocoagulation (PRP) - proliferative diabetic retinopathy
- Focal/grid photocoagulation - diabetic macular edema
- Peripheral iridotomy - angle-closure glaucoma
- Cyclophotocoagulation - refractory glaucoma
- Posterior capsulotomy - YAG laser for PCO

---

### 2.5 Minor Surgical Procedure (In-office)

**Clinical Intent**: Perform surgical intervention in outpatient setting (e.g., intravitreal injection, anterior chamber tap, conjunctival biopsy).

| Aspect | Details |
|--------|---------|
| **Purpose** | Therapeutic or diagnostic surgical intervention in office setting |
| **Triggering Event** | Planned during examination; documented in care plan |
| **Typical Duration** | 15-30 minutes |
| **Primary Actor** | Ophthalmologist (consultant); nurse support |

**Inputs**:
- Pre-operative examination and imaging
- Surgical indication and plan
- Informed consent
- Sterility requirements
- Emergency protocols

**Process Flow**:

1. **Pre-operative Preparation** (Ophthalmologist/Nurse)
   - Verify patient identity and procedure
   - Obtain informed consent
   - Perform time-out (safety checklist)
   - Prepare sterile field
   - Instill topical anesthesia

2. **Surgical Procedure** (Ophthalmologist)
   - Execute surgical steps
   - Document findings and technique
   - Use EyeDraw to diagram procedure site
   - Handle specimens (if applicable)

3. **Post-operative Assessment** (Ophthalmologist)
   - Evaluate immediate outcome
   - Assess for complications
   - Instill post-operative medications
   - Apply dressing (if needed)

4. **Patient Recovery & Discharge** (Nurse)
   - Monitor vital signs
   - Provide post-operative instructions
   - Schedule follow-up

**Outputs**:
- Operation notes with detailed procedure description
- EyeDraw diagrams of procedure site
- Specimen information (if applicable)
- Complication documentation
- Post-operative imaging (if indicated)
- PhilHealth RVS code for procedure

**Data Objects Created**:
- `Procedure` (surgical procedure record)
- `Specimen` (if tissue obtained)
- `Observation` (findings, complications)
- `CarePlan` (post-operative follow-up)

**Common In-office Procedures**:
- Intravitreal injection (anti-VEGF, steroid, antibiotic)
- Anterior chamber paracentesis
- Conjunctival biopsy
- Chalazion incision and drainage
- Pterygium excision (minor)

---

### 2.6 Major Surgical Procedure (Operating Theatre)

**Clinical Intent**: Perform complex surgical intervention requiring operating theatre, anesthesia, and sterile environment (cataract surgery, glaucoma surgery, retinal surgery, corneal transplant).

| Aspect | Details |
|--------|---------|
| **Purpose** | Definitive surgical treatment for advanced pathology |
| **Triggering Event** | Planned during consultation; scheduled in operating theatre |
| **Typical Duration** | 30-120 minutes (varies by procedure) |
| **Primary Actor** | Ophthalmologist (consultant); anesthesiologist; OR nurses; technicians |

**Inputs**:
- Pre-operative workup (examination, imaging, biometry, systemic assessment)
- Surgical plan and indication
- Informed consent
- Anesthesia clearance
- Equipment and implant specifications
- Baseline imaging for comparison

**Process Flow**:

1. **Pre-operative Assessment** (Ophthalmologist/Anesthesiologist)
   - Verify surgical indication
   - Review imaging and biometry
   - Confirm implant selection (e.g., IOL for cataract)
   - Obtain final consent
   - Assess anesthesia risk

2. **Pre-operative Preparation** (OR Staff)
   - Prepare operating theatre
   - Verify equipment and implants
   - Position patient
   - Administer anesthesia

3. **Surgical Procedure** (Ophthalmologist)
   - Execute surgical steps per protocol
   - Document key steps and findings
   - Use EyeDraw to diagram surgical anatomy
   - Manage intraoperative complications
   - Place implants as needed

4. **Post-operative Assessment** (Ophthalmologist)
   - Evaluate immediate outcome
   - Document final appearance
   - Assess visual potential
   - Instill post-operative medications

5. **Post-operative Care** (Nursing/Recovery)
   - Monitor vital signs
   - Manage pain
   - Provide post-operative instructions
   - Schedule follow-up examination

**Outputs**:
- Detailed operation notes with surgical technique
- EyeDraw diagrams of surgical anatomy and findings
- Implant details (IOL power, type, position)
- Intraoperative complications (if any)
- Post-operative imaging (if indicated)
- PhilHealth RVS code for procedure
- Discharge summary with post-operative restrictions

**Data Objects Created**:
- `Procedure` (surgical procedure record)
- `Observation` (surgical findings, implant details, complications)
- `Device` (implanted device: IOL, glaucoma tube, etc.)
- `CarePlan` (post-operative follow-up, restrictions)
- `MedicationStatement` (post-operative medications)

**Common Major Procedures**:
- Phacoemulsification with IOL implantation (cataract)
- Trabeculectomy (glaucoma)
- Vitrectomy (retinal pathology)
- Penetrating keratoplasty (corneal disease)
- Pterygium excision with graft
- Retinal detachment repair
- Diabetic vitrectomy

---

### 2.7 Emergency Eye Presentation

**Clinical Intent**: Rapidly assess and stabilize sight-threatening emergency (trauma, acute angle closure, retinal detachment, endophthalmitis, chemical burn).

| Aspect | Details |
|--------|---------|
| **Purpose** | Urgent evaluation and management to prevent vision loss |
| **Triggering Event** | Patient presents to emergency department or calls for urgent appointment |
| **Typical Duration** | 15-45 minutes (assessment + initial management) |
| **Primary Actor** | On-call ophthalmologist; ER staff |

**Inputs**:
- Chief complaint (trauma, pain, vision loss, etc.)
- Mechanism of injury (if trauma)
- Time of onset
- Current vision
- Relevant medical history
- Medications (especially anticoagulants)

**Process Flow**:

1. **Rapid Triage** (ER/Nurse)
   - Assess severity (vision-threatening vs. non-urgent)
   - Measure visual acuity if possible
   - Assess pain level
   - Alert ophthalmology if emergent

2. **Emergency Examination** (Ophthalmologist)
   - Rapid assessment of anterior segment
   - Assess visual function
   - Identify sight-threatening pathology
   - Determine urgency of intervention

3. **Initial Management** (Ophthalmologist)
   - Stabilize eye (shield if necessary)
   - Instill medications
   - Arrange urgent imaging if needed
   - Determine disposition (discharge, admission, OR)

4. **Definitive Management** (Ophthalmologist)
   - Proceed to OR if surgical emergency
   - Admit if requiring observation
   - Discharge with close follow-up if stable

**Outputs**:
- Emergency examination note
- Urgent imaging (if indicated)
- Initial treatment documentation
- Disposition (discharge, admission, OR)
- Follow-up plan
- Emergency contact information

**Data Objects Created**:
- `Encounter` (emergency visit)
- `Observation` (urgent findings)
- `Condition` (emergency diagnosis)
- `Procedure` (emergency intervention if performed)

**Common Emergencies**:
- Ocular trauma (blunt, penetrating)
- Acute angle-closure glaucoma
- Retinal detachment
- Endophthalmitis
- Chemical/thermal burn
- Hyphema
- Globe rupture

---

### 2.8 Inpatient Admission & Management

**Clinical Intent**: Provide 24-hour monitoring and care for complex cases requiring hospitalization (post-operative, complicated infection, severe trauma, systemic eye disease).

| Aspect | Details |
|--------|---------|
| **Purpose** | Intensive monitoring and management of complex ophthalmic conditions |
| **Triggering Event** | Planned admission (post-op) or emergency admission (trauma, infection) |
| **Typical Duration** | 1-7 days |
| **Primary Actor** | Ophthalmologist; inpatient nursing staff; residents |

**Inputs**:
- Admission diagnosis and indication
- Pre-admission examination and imaging
- Surgical report (if post-operative)
- Relevant medical history
- Current medications
- Allergies

**Process Flow**:

1. **Admission** (Nursing/Resident)
   - Complete admission documentation
   - Obtain vital signs
   - Perform baseline examination
   - Document baseline vision and IOP

2. **Daily Rounds** (Ophthalmologist)
   - Assess clinical progress
   - Examine eye (vision, IOP, anterior/posterior segment)
   - Review imaging/diagnostics
   - Adjust medications
   - Plan next intervention

3. **Nursing Care** (Inpatient Nurses)
   - Administer medications on schedule
   - Monitor vital signs
   - Maintain eye care (drops, hygiene)
   - Monitor for complications
   - Provide patient education

4. **Discharge Planning** (Ophthalmologist)
   - Assess readiness for discharge
   - Provide discharge medications
   - Arrange follow-up appointments
   - Provide discharge instructions

**Outputs**:
- Admission note
- Daily progress notes
- Medication administration record
- Imaging/diagnostic results
- Discharge summary
- Follow-up plan
- PhilHealth claim documentation

**Data Objects Created**:
- `Encounter` (inpatient admission)
- `Observation` (daily assessments, vital signs)
- `MedicationAdministration` (medication administration record)
- `CarePlan` (inpatient management plan)
- `Condition` (admission diagnosis and progress)

---

## 3. SUPPORTING OPERATIONAL WORKFLOWS

### 3.1 Patient Registration & Demographics

**Clinical Intent**: Establish patient identity, capture essential demographic and contact information, link to PhilHealth insurance, enable appointment scheduling and billing.

| Aspect | Details |
|--------|---------|
| **Purpose** | Create patient record; verify insurance eligibility; enable billing and follow-up |
| **Triggering Event** | Patient first presents to facility or returns after extended absence |
| **Typical Duration** | 5-10 minutes |
| **Primary Actor** | Receptionist/clerical staff |

**Inputs**:
- Patient name, date of birth, gender
- Contact information (phone, address)
- PhilHealth ID or insurance information
- Emergency contact
- Referral source (if applicable)

**Process Flow**:

1. **Verification** (Receptionist)
   - Check if patient is in system
   - If new patient, proceed to registration

2. **Data Entry** (Receptionist)
   - Enter demographics into system
   - Verify PhilHealth eligibility
   - Assign patient ID
   - Create patient record

3. **Documentation** (Receptionist)
   - Print patient ID card or sticker
   - File registration form
   - Create appointment slot

**Outputs**:
- Patient record with unique identifier
- PhilHealth eligibility confirmation
- Patient contact information
- Appointment scheduled

**Data Objects Created**:
- `Patient` (demographic record)
- `Identifier` (patient ID, PhilHealth ID)
- `ContactPoint` (phone, email, address)

---

### 3.2 Appointment Scheduling

**Clinical Intent**: Allocate clinic time efficiently, manage patient flow, ensure appropriate specialist assignment, reduce wait times.

| Aspect | Details |
|--------|---------|
| **Purpose** | Schedule patient appointments based on clinical priority, specialist availability, and clinic capacity |
| **Triggering Event** | Patient requests appointment; clinician recommends follow-up; referral received |
| **Typical Duration** | 2-5 minutes per appointment |
| **Primary Actor** | Receptionist/scheduling staff; clinician (for priority determination) |

**Inputs**:
- Patient identification
- Clinical indication for appointment
- Preferred dates/times
- Specialist preference (if applicable)
- Urgency level

**Process Flow**:

1. **Triage** (Receptionist/Clinician)
   - Determine clinical urgency (routine, urgent, emergency)
   - Assign appropriate specialist
   - Estimate appointment duration

2. **Scheduling** (Receptionist)
   - Check specialist availability
   - Offer available time slots
   - Confirm appointment with patient
   - Send appointment reminder (SMS, phone)

3. **Documentation** (Receptionist)
   - Record appointment in system
   - Flag if pre-operative workup needed
   - Prepare appointment letter

**Outputs**:
- Scheduled appointment with date/time/specialist
- Appointment reminder sent to patient
- Pre-operative workup scheduled (if applicable)

**Data Objects Created**:
- `Appointment` (scheduled visit)
- `Schedule` (specialist availability)

**Philippine Context - Appointment Prioritization** (PAO Guidelines):
- **Urgent (same day/next day)**: Trauma, acute vision loss, acute angle closure, endophthalmitis
- **Priority (1-2 weeks)**: Retinal detachment, advanced glaucoma, corneal ulcer
- **Routine (2-4 weeks)**: Cataract, refractive error, routine follow-up
- **Satellite clinic**: Community screening, follow-up for stable conditions

---

### 3.3 Referral Management

**Clinical Intent**: Facilitate appropriate patient routing between primary/secondary/tertiary care; ensure continuity of care; document referral pathway for billing and coordination.

| Aspect | Details |
|--------|---------|
| **Purpose** | Route patients to appropriate level of care; document referral for coordination and billing |
| **Triggering Event** | Patient requires specialist care; satellite clinic refers to main facility; external facility refers for second opinion |
| **Typical Duration** | 5-10 minutes |
| **Primary Actor** | Referring clinician; receptionist (coordination) |

**Inputs**:
- Patient identification
- Referring facility/clinician
- Clinical indication for referral
- Relevant clinical information (diagnosis, imaging, prior treatment)
- Urgency level

**Process Flow**:

1. **Referral Generation** (Referring Clinician)
   - Document clinical indication
   - Attach relevant imaging/reports
   - Specify urgency
   - Provide contact information

2. **Referral Transmission** (Referring Facility)
   - Send referral letter to receiving facility
   - Include clinical summary and imaging
   - Provide patient contact information

3. **Referral Reception** (Receiving Facility)
   - Receive referral documentation
   - Verify patient information
   - Schedule appointment based on urgency
   - Confirm with patient

4. **Follow-up** (Receiving Facility)
   - Provide care as indicated
   - Send feedback to referring clinician
   - Document referral pathway for billing

**Outputs**:
- Referral letter with clinical summary
- Scheduled appointment at receiving facility
- Feedback communication to referring clinician
- Referral documentation for billing

**Data Objects Created**:
- `ServiceRequest` (referral request)
- `Appointment` (scheduled at receiving facility)
- `Communication` (feedback to referring clinician)

**Philippine Context - Referral Pathways**:
- **Satellite clinic → Main tertiary facility**: Screening cases, complex pathology, surgical candidates
- **Primary health unit → Tertiary facility**: Suspected serious eye disease, referral for surgery
- **Private clinic → Tertiary facility**: Second opinion, complex cases, PhilHealth-eligible patients
- **Tertiary facility → Satellite clinic**: Stable follow-up, community screening

---

### 3.4 PhilHealth Claim Preparation & Submission

**Clinical Intent**: Generate accurate reimbursement claims for PhilHealth; ensure compliance with coding standards; track claim status; maximize facility revenue.

| Aspect | Details |
|--------|---------|
| **Purpose** | Prepare and submit PhilHealth claims for reimbursement; ensure ICD-10 and RVS code accuracy |
| **Triggering Event** | Patient encounter completed; billable service provided |
| **Typical Duration** | 10-20 minutes per claim |
| **Primary Actor** | Billing officer; clinician (for coding verification) |

**Inputs**:
- Encounter details (date, facility, provider)
- Diagnosis (ICD-10 code)
- Procedures performed (RVS codes)
- Patient demographics and PhilHealth ID
- Facility level (tertiary, secondary, primary)
- Cost breakdown

**Process Flow**:

1. **Data Extraction** (Billing Officer)
   - Extract encounter data from EMR
   - Identify billable diagnosis and procedures
   - Verify PhilHealth eligibility

2. **Coding** (Billing Officer/Clinician)
   - Assign ICD-10 diagnosis codes
   - Assign RVS procedure codes
   - Verify code accuracy with clinician
   - Document clinical justification

3. **Claim Assembly** (Billing Officer)
   - Populate PhilHealth eClaims form
   - Attach supporting documentation (clinical notes, imaging, operative reports)
   - Calculate reimbursement amount based on PhilHealth rates
   - Review for completeness

4. **Submission** (Billing Officer)
   - Submit claim via PhilHealth eClaims system
   - Record submission date and claim ID
   - Monitor claim status

5. **Follow-up** (Billing Officer)
   - Track claim approval/denial
   - Address any claim denials or requests for additional information
   - Reconcile reimbursement with facility records

**Outputs**:
- PhilHealth eClaims submission
- Claim ID and submission date
- Reimbursement amount
- Claim status tracking
- Denial/approval documentation

**Data Objects Created**:
- `Claim` (PhilHealth claim record)
- `ClaimResponse` (approval/denial status)
- `Coding` (ICD-10 and RVS codes)

**Philippine Context - Coding Requirements**:
- **ICD-10 Diagnosis**: Primary diagnosis + secondary diagnoses (comorbidities)
- **RVS Procedure Codes**: Specific codes for ophthalmology procedures (e.g., 65820 for goniotomy)
- **Case Rates**: PhilHealth reimburses by case rate (fixed amount per diagnosis/procedure combination)
- **Facility Level**: Tertiary facilities receive higher reimbursement than secondary/primary
- **Documentation**: Clinical notes, operative reports, imaging must support coding

**Common Ophthalmology RVS Codes (Philippines)**:
- Cataract surgery with IOL: ~23,300-25,000 PHP (first case rate, tertiary)
- Retinal photocoagulation: ~5,000-8,000 PHP
- Glaucoma surgery (trabeculectomy): ~15,000-20,000 PHP
- Intravitreal injection: ~3,000-5,000 PHP
- Anterior chamber paracentesis: ~2,000-3,000 PHP

---

### 3.5 Prescription & Medication Management

**Clinical Intent**: Document prescribed medications; ensure safe dispensing; track medication adherence; manage side effects and drug interactions.

| Aspect | Details |
|--------|---------|
| **Purpose** | Generate prescriptions; track medication use; monitor adherence and side effects |
| **Triggering Event** | Clinician determines medication necessary during examination or procedure |
| **Typical Duration** | 2-5 minutes per prescription |
| **Primary Actor** | Ophthalmologist/resident; pharmacist (dispensing) |

**Inputs**:
- Patient identification
- Medication name and formulation
- Dosage and frequency
- Route of administration (topical, oral, injection)
- Duration of therapy
- Indication for medication
- Allergies and contraindications

**Process Flow**:

1. **Prescription Generation** (Ophthalmologist)
   - Select medication from formulary
   - Specify dosage, frequency, duration
   - Document indication
   - Check for drug interactions
   - Sign prescription

2. **Prescription Review** (Pharmacist)
   - Verify prescription legibility and completeness
   - Check for drug interactions and allergies
   - Confirm dosage appropriateness
   - Verify PhilHealth coverage (if applicable)

3. **Dispensing** (Pharmacist)
   - Prepare medication
   - Label with patient name, medication, dosage, frequency
   - Provide patient education on administration
   - Document dispensing

4. **Patient Education** (Pharmacist/Nurse)
   - Explain medication purpose
   - Demonstrate administration technique (especially for eye drops)
   - Discuss side effects and when to seek help
   - Provide written instructions

**Outputs**:
- Prescription record
- Dispensed medication with label
- Patient education materials
- Medication adherence tracking

**Data Objects Created**:
- `MedicationRequest` (prescription)
- `MedicationDispense` (dispensing record)
- `MedicationStatement` (current medications)

**Philippine Context - Medication Considerations**:
- **PhilHealth Coverage**: Limited to essential medicines list; many newer agents not covered
- **Local Availability**: Some medications may be unavailable; alternatives needed
- **Cost**: Patient may need to purchase medications out-of-pocket if not PhilHealth-covered
- **Common Ophthalmology Medications**:
  - Topical antibiotics (moxifloxacin, ofloxacin)
  - Topical antiglaucoma agents (timolol, dorzolamide, latanoprost)
  - Topical steroids (dexamethasone, prednisolone)
  - Oral antibiotics (ciprofloxacin, doxycycline)
  - Systemic antiglaucoma (acetazolamide)

---

### 3.6 Correspondence & Communication

**Clinical Intent**: Communicate clinical findings and recommendations to referring clinicians, patients, and other stakeholders; ensure continuity of care; document communication for medicolegal purposes.

| Aspect | Details |
|--------|---------|
| **Purpose** | Generate clinical correspondence; communicate findings to referring clinicians and patients |
| **Triggering Event** | Patient completes consultation or procedure; referral received; follow-up needed |
| **Typical Duration** | 5-15 minutes |
| **Primary Actor** | Ophthalmologist/resident; clerical staff (formatting/sending) |

**Inputs**:
- Patient identification
- Clinical findings from examination/procedure
- Diagnosis and management plan
- Referring clinician contact information
- Patient contact information

**Process Flow**:

1. **Letter Generation** (Ophthalmologist)
   - Dictate or type clinical summary
   - Include relevant findings and diagnosis
   - Specify management plan and follow-up
   - Address to referring clinician or patient

2. **Review & Formatting** (Clerical Staff)
   - Format letter per institutional standards
   - Verify patient and clinician information
   - Proofread for accuracy
   - Prepare for signature

3. **Signature & Dispatch** (Ophthalmologist/Clerical)
   - Ophthalmologist signs letter
   - Send to referring clinician (fax, email, post)
   - Provide copy to patient
   - File copy in patient record

**Outputs**:
- Clinical correspondence letter
- Copy to referring clinician
- Copy to patient
- Filed in patient record

**Data Objects Created**:
- `Communication` (correspondence record)
- `DocumentReference` (letter document)

---

## 4. DATA OBJECTS & MAPPING TO OPENEYES

### 4.1 Core Data Objects

| OpenEyes Event/Object | Clinical Meaning | Typical Data Elements |
|----------------------|------------------|----------------------|
| **Encounter** | Single patient visit (outpatient, emergency, inpatient admission) | Date, time, location, provider, chief complaint, visit type |
| **Examination Event** | Comprehensive ophthalmic examination | VA, IOP, anterior segment findings, posterior segment findings, EyeDraw diagrams |
| **Observation** | Measured or assessed clinical finding | VA, IOP, OCT thickness, visual field indices, biometry values |
| **Condition** | Diagnosis with clinical status | ICD-10 code, onset date, status (active, resolved), severity |
| **Procedure** | Therapeutic or diagnostic intervention | Procedure code (RVS), date, indication, findings, complications |
| **DiagnosticReport** | Interpreted imaging or test result | Report text, findings, recommendations, associated images |
| **ImagingStudy** | Imaging data (OCT, photography, etc.) | Modality, acquisition date, image files, measurements |
| **Medication** | Prescribed medication | Drug name, formulation, strength |
| **MedicationRequest** | Prescription | Medication, dosage, frequency, duration, indication |
| **MedicationDispense** | Dispensed medication | Medication, quantity, date dispensed, patient instructions |
| **Device** | Implanted or used medical device | Device type (IOL, glaucoma tube), specifications, implant date |
| **ServiceRequest** | Request for service (referral, appointment) | Requested service, indication, urgency, requesting clinician |
| **Appointment** | Scheduled patient visit | Date, time, provider, location, reason |
| **Patient** | Individual receiving care | Demographics, contact, PhilHealth ID, allergies |
| **Practitioner** | Healthcare provider | Name, credentials, specialty, contact |
| **Organization** | Healthcare facility | Name, address, PhilHealth accreditation, facility level |

### 4.2 Coding & Classification

| Classification System | Purpose | Philippine Context |
|----------------------|---------|-------------------|
| **ICD-10** | Diagnosis coding | Mandatory for PhilHealth claims; maps to SNOMED CT concepts |
| **RVS (Relative Value Scale)** | Procedure coding | Philippine-specific; determines PhilHealth reimbursement |
| **SNOMED CT** | Clinical terminology | OpenEyes internal representation; must map to ICD-10 for claims |
| **CPT (Current Procedural Terminology)** | Procedure coding | Not used in Philippines; RVS used instead |
| **HL7 FHIR** | Data exchange standard | Potential for inter-facility data exchange |

### 4.3 SNOMED-to-ICD-10 Mapping Examples (Ophthalmology)

| Clinical Concept | SNOMED CT | ICD-10 | Philippine Context |
|------------------|-----------|--------|-------------------|
| Cataract, age-related | 193570009 | H25.9 | Common; high surgical volume |
| Diabetic retinopathy, proliferative | 4855003 | E11.35 | Common; PhilHealth covered |
| Primary open-angle glaucoma | 63650-0 | H40.10 | Screening priority; PhilHealth covered |
| Myopia, moderate | 57190000 | H52.1 | Refractive error; may not be PhilHealth-covered |
| Corneal ulcer, bacterial | 441974008 | H16.001 | Urgent; PhilHealth covered |
| Retinal detachment | 42059000 | H33.9 | Surgical emergency; PhilHealth covered |

---

## 5. WORKFLOW DEPENDENCIES & DATA FLOW

### 5.1 Typical Patient Journey (New Outpatient with Cataract)

```
Registration 
  ↓
Appointment Scheduling 
  ↓
Pre-exam (VA, IOP, Photography) 
  ↓
Examination Event (Ophthalmologist) 
  ↓
Diagnosis: Age-related Cataract (ICD-10: H25.9) 
  ↓
Biometry & IOL Selection (Diagnostic Event) 
  ↓
Informed Consent & Surgical Planning 
  ↓
PhilHealth Claim Preparation (RVS: Cataract surgery code) 
  ↓
Scheduled for Cataract Surgery 
  ↓
Pre-operative Workup (Labs, Anesthesia clearance) 
  ↓
Major Surgical Procedure (Operation Notes, EyeDraw) 
  ↓
Post-operative Examination (Day 1, Week 1, Month 1) 
  ↓
PhilHealth Claim Submission 
  ↓
Long-term Follow-up (Routine visits, Refraction)
```

### 5.2 Data Objects Created During Cataract Surgery Pathway

| Step | Data Objects Created | Coding Required |
|------|----------------------|-----------------|
| Registration | Patient, Identifier, ContactPoint | - |
| Appointment | Appointment, Schedule | - |
| Examination | Encounter, Observation (VA, IOP), Condition (H25.9) | ICD-10: H25.9 |
| Biometry | DiagnosticReport, ImagingStudy, Observation (biometry values) | - |
| Surgical Planning | Procedure, Device (IOL specifications) | RVS: Cataract code |
| Surgery | Procedure, Observation (surgical findings), Device (IOL implant) | RVS: Cataract code |
| Post-op Follow-up | Encounter, Observation (VA, IOP), Condition (post-op status) | - |
| Claim | Claim, ClaimResponse | ICD-10 + RVS |

---

## 6. CLINICAL INTENT SUMMARY TABLE

| Workflow | Clinical Intent | Key Actors | Primary Data Objects | Coding |
|----------|-----------------|-----------|----------------------|--------|
| New Outpatient Consult | Establish baseline, diagnose | Ophthalmologist, Nurse | Encounter, Examination, Condition | ICD-10 |
| Follow-up Consult | Monitor progress, adjust treatment | Ophthalmologist, Nurse | Encounter, Observation, CarePlan | ICD-10 |
| Diagnostic Imaging | Obtain objective data | Technician, Ophthalmologist | DiagnosticReport, ImagingStudy, Observation | - |
| Laser Procedure | Therapeutic intervention | Ophthalmologist, Technician | Procedure, Observation, Condition | RVS |
| Minor Surgery | Therapeutic/diagnostic intervention | Ophthalmologist, Nurse | Procedure, Specimen, Observation | RVS |
| Major Surgery | Definitive surgical treatment | Ophthalmologist, Anesthesiologist, OR staff | Procedure, Device, Observation | RVS |
| Emergency | Urgent stabilization | Ophthalmologist, ER staff | Encounter, Observation, Procedure | ICD-10 + RVS |
| Inpatient | Intensive monitoring | Ophthalmologist, Nursing staff | Encounter, Observation, MedicationAdministration | ICD-10 + RVS |
| Registration | Patient identity & insurance | Receptionist | Patient, Identifier, ContactPoint | - |
| Scheduling | Appointment allocation | Receptionist, Clinician | Appointment, Schedule | - |
| Referral | Patient routing & coordination | Referring clinician, Receptionist | ServiceRequest, Appointment, Communication | - |
| PhilHealth Claim | Reimbursement | Billing officer, Clinician | Claim, Coding | ICD-10 + RVS |
| Prescription | Medication management | Ophthalmologist, Pharmacist | MedicationRequest, MedicationDispense | - |
| Correspondence | Communication & continuity | Ophthalmologist, Clerical | Communication, DocumentReference | - |

---

## 7. OFFLINE CAPABILITY CONSIDERATIONS

Given the Philippine context (intermittent internet, department-owned server, mesh VPN):

### 7.1 Data Synchronization Points

**Online-required operations**:
- PhilHealth eClaims submission (must have internet)
- External referral communication (email/fax)
- Satellite clinic data sync to main facility

**Offline-capable operations**:
- Patient registration and demographics
- Appointment scheduling (local)
- Examination documentation
- Prescription generation
- Imaging storage (local)
- Billing calculations

### 7.2 Offline-First Workflow

1. **Examination**: Conducted offline; data stored locally
2. **Imaging**: Acquired and stored locally (OCT, photography)
3. **Coding**: ICD-10 and RVS codes assigned offline
4. **Claim Preparation**: Assembled offline
5. **Sync**: When internet available, sync to main server and submit PhilHealth claims
6. **Satellite Clinic**: Sync with main facility when connectivity available

---

## 8. NEXT STEPS FOR ITERATION

1. **Refine workflow details** based on actual facility workflows
2. **Map SNOMED-to-ICD-10** for common ophthalmology diagnoses
3. **Define RVS procedure code** integration points
4. **Design data synchronization** protocol for offline operation
5. **Specify user roles & permissions** for each actor
6. **Create UI mockups** for key workflows (examination, billing, referral)
