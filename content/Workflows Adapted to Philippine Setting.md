# Philippine-Adapted Clinical Workflows
## OpenEyes for Tertiary Ophthalmology in Low-Resource Settings

**Context**: Mixed public/private tertiary eye care facility with majority outpatient, diagnostic/laser center, 4-bed inpatient ward, satellite clinic. Department-owned server, mesh VPN access, intermittent internet, limited IT support, physician-led processes, out-of-pocket payment realities.

---

## 1. NEW PATIENT OUTPATIENT CONSULTATION

### Original (NHS Context)
- Technician performs complete pre-exam (VA, IOP, photography)
- Consultant or senior resident examines patient
- Dilated fundus exam performed routinely
- EyeDraw used for anatomical documentation
- Single diagnosis assigned
- Standardized management pathways
- Informed consent obtained before intervention
- ICD-10 diagnosis code assigned for billing

### Localized (Philippine Context)

**Triggering Event**: Patient presents to reception with appointment, referral, or walk-in.

**Pre-Examination Phase** (Nurse or Resident - Technician if available)
- **Required**: Vital signs (BP, pulse, temperature)
- **Required**: Visual acuity measurement (both eyes, with/without correction) - performed by nurse or resident if technician unavailable
- **Required**: Intraocular pressure screening - performed by nurse or resident using available tonometer
- **Optional**: Fundus photography - only if equipment available and functional
- **Optional**: OCT imaging - only if equipment available and patient can afford
- **Paper backup**: Manual VA/IOP recording on paper form if system unavailable

**Clinical Examination Phase** (Ophthalmologist or Resident)
- **Required**: Anterior segment examination (slit lamp)
- **Required**: Posterior segment examination - undilated initially; dilation only if indicated and safe
- **Optional**: Dilated fundus exam - performed only if:
  - Angle closure not suspected (or gonioscopy performed first)
  - Patient consents and can afford mydriatic drops
  - Follow-up examination possible within 1-2 weeks
- **Optional**: Biometry - only if cataract surgery planned and patient can afford
- **Optional**: Additional testing (visual fields, gonioscopy) - only if indicated and available

**Diagnosis & Planning Phase** (Ophthalmologist)
- **Required**: Clinical findings documented in structured note
- **Optional**: EyeDraw diagrams - used if time permits; text description acceptable
- **Required**: Working diagnosis formulated (may be provisional/differential)
- **Required**: Management pathway determined (medical, laser, surgical, referral, watchful waiting)
- **Required**: ICD-10 primary diagnosis code assigned (for PhilHealth billing)
- **Optional**: Secondary diagnoses documented (comorbidities, findings)

**Patient Communication Phase** (Ophthalmologist)
- **Required**: Diagnosis explained in understandable terms (Filipino/Tagalog if needed)
- **Required**: Treatment options discussed with cost implications
- **Required**: Informed consent obtained (verbal acceptable; documented in notes)
- **Optional**: Written consent form - used for procedures; verbal consent acceptable for consultation
- **Optional**: Patient education materials - provided if available in local language

**Payment & Scheduling Phase** (Receptionist/Billing Officer)
- **Required**: Determine payment method:
  - PhilHealth (if eligible and accredited)
  - Out-of-pocket (private pay)
  - Mixed (PhilHealth + out-of-pocket for non-covered items)
- **Required**: Explain costs for consultation, diagnostics, treatment
- **Required**: Arrange payment (advance payment or post-visit billing)
- **Required**: Schedule follow-up appointment or procedure
- **Optional**: Provide written appointment card
- **Paper backup**: Manual appointment record if system unavailable

**Data Objects Created**:
- `Encounter` (visit record with payment method)
- `Observation` (VA, IOP, clinical findings)
- `Condition` (diagnosis with ICD-10 code)
- `CarePlan` (management recommendations)
- `PhilHealthClaim` (if eligible for PhilHealth)
- `PatientEducation` (if provided)

### Rationale

**What Changes**:
1. **Pre-exam flexibility**: Technician role made optional; nurse or resident can perform if technician unavailable
2. **Dilation optional**: Not performed routinely; only when indicated and safe
3. **EyeDraw optional**: Text documentation acceptable when time-constrained
4. **Multiple diagnoses supported**: Comorbidities common; secondary diagnoses documented
5. **Payment integration**: Payment method determined during visit; cost discussion explicit
6. **Verbal consent acceptable**: Simplified consent process; written form optional
7. **Paper backup**: All steps have paper-based alternative

**What Stays**:
1. Vital signs assessment (required)
2. Visual acuity and IOP measurement (required)
3. Slit lamp examination (required)
4. Posterior segment assessment (required)
5. Diagnosis formulation and ICD-10 coding (required)
6. Management plan determination (required)
7. Patient communication and consent (required)

**New Roles Introduced**:
1. **Billing Officer**: Determines payment method, explains costs, arranges payment
2. **Resident (if no technician)**: Performs pre-exam measurements
3. **Nurse (if no technician)**: Performs pre-exam measurements

**Optional vs Required Steps**:
- **Required**: Vital signs, VA, IOP, slit lamp exam, posterior segment exam, diagnosis, ICD-10 code, management plan, patient communication, payment arrangement
- **Optional**: Fundus photography, OCT imaging, biometry, dilation, EyeDraw diagrams, written consent, patient education materials, written appointment card

---

## 2. FOLLOW-UP/REVIEW CONSULTATION

### Original (NHS Context)
- Structured interval history obtained
- Repeat key measurements (VA, IOP, OCT) for comparison
- Prior imaging automatically retrieved and displayed
- Treatment escalation follows standardized protocols
- Medication adherence assessed
- Next appointment scheduled

### Localized (Philippine Context)

**Triggering Event**: Scheduled follow-up appointment or patient self-referral for symptoms.

**Interval History Phase** (Nurse or Resident)
- **Required**: Document symptom changes since last visit
- **Required**: Assess medication compliance (if medications prescribed)
- **Optional**: Assess medication side effects (only if patient reports issues)
- **Optional**: Assess affordability of medications (to identify non-compliance due to cost)
- **Paper backup**: Manual history form if system unavailable

**Targeted Examination Phase** (Ophthalmologist or Resident)
- **Required**: Focused examination on relevant findings from prior visit
- **Optional**: Repeat VA measurement - only if clinically indicated
- **Optional**: Repeat IOP measurement - only if clinically indicated
- **Optional**: Repeat OCT imaging - only if available and clinically indicated
- **Paper backup**: Manual measurements recorded if system unavailable

**Clinical Assessment Phase** (Ophthalmologist)
- **Required**: Compare current findings to baseline/prior visits (using available records)
- **Required**: Determine disease trajectory (stable, improving, worsening)
- **Required**: Assess treatment efficacy
- **Optional**: Retrieve prior imaging for side-by-side comparison (only if digitized)
- **Paper backup**: Manual comparison using paper records if digital unavailable

**Plan Modification Phase** (Ophthalmologist)
- **Required**: Decide on treatment continuation, modification, or escalation
- **Required**: Adjust medication dosing/frequency if needed
- **Optional**: Schedule next intervention (laser, surgery, imaging) - only if planned
- **Required**: Determine next appointment interval
- **Required**: Discuss cost implications of any treatment changes

**Payment & Follow-up Phase** (Receptionist/Billing Officer)
- **Required**: Collect payment for current visit
- **Required**: Arrange payment for any planned procedures/imaging
- **Required**: Schedule next appointment
- **Optional**: Provide written appointment card
- **Paper backup**: Manual appointment record if system unavailable

**Data Objects Created**:
- `Encounter` (follow-up visit)
- `Observation` (repeat measurements if obtained)
- `Condition` (updated diagnosis status)
- `MedicationStatement` (current medications, adherence status)
- `CarePlan` (revised plan)
- `PhilHealthClaim` (if billable intervention)

### Rationale

**What Changes**:
1. **Repeat measurements optional**: Only performed if clinically indicated; not routine
2. **Prior imaging retrieval optional**: Only if digitized; paper records used otherwise
3. **Medication adherence assessment**: Includes affordability assessment
4. **Cost discussion explicit**: Treatment changes discussed with cost implications
5. **Flexible appointment intervals**: Based on disease status and patient ability to return

**What Stays**:
1. Interval history assessment (required)
2. Focused examination (required)
3. Clinical assessment and comparison (required)
4. Plan modification decision (required)
5. Patient communication (required)
6. Next appointment scheduling (required)

**New Roles Introduced**:
1. **Billing Officer**: Arranges payment for current visit and planned procedures
2. **Nurse/Resident**: May perform interval history and targeted examination

**Optional vs Required Steps**:
- **Required**: Interval history, focused examination, clinical assessment, plan modification, patient communication, appointment scheduling
- **Optional**: Repeat VA/IOP, repeat OCT imaging, prior imaging retrieval, written appointment card

---

## 3. DIAGNOSTIC IMAGING & TESTING

### Original (NHS Context)
- Technician performs standardized protocol with quality control
- Preliminary review by technician flags abnormalities
- Ophthalmologist interprets images and generates report
- Quantitative measurements provided
- Comparison to prior studies automatic

### Localized (Philippine Context)

**Test Requisition Phase** (Ophthalmologist or Resident)
- **Required**: Specify test type (OCT, visual fields, biometry, photography)
- **Required**: Document clinical indication
- **Optional**: Specify urgency (routine, urgent, stat)
- **Paper backup**: Manual requisition form if system unavailable

**Patient Preparation Phase** (Technician or Nurse)
- **Required**: Identify patient and verify test type
- **Required**: Explain procedure to patient in understandable terms
- **Optional**: Provide written procedure instructions (if available)
- **Required**: Position patient at equipment
- **Optional**: Perform equipment calibration (if technician available)

**Image Acquisition Phase** (Technician or Trained Staff)
- **Required**: Capture images/data per available protocol
- **Required**: Ensure image quality (repeat if obviously poor quality)
- **Optional**: Perform quality control check (only if trained technician available)
- **Paper backup**: Manual documentation of test parameters if system unavailable

**Preliminary Review Phase** (Technician or Nurse)
- **Optional**: Verify image quality (only if trained technician available)
- **Optional**: Flag obvious abnormalities (only if trained technician available)
- **Required if flagged**: Communicate urgent findings to ophthalmologist immediately

**Clinical Interpretation Phase** (Ophthalmologist)
- **Required**: Analyze images/data
- **Optional**: Compare to prior studies (only if prior images available and digitized)
- **Required**: Generate report with findings and clinical significance
- **Required**: Provide recommendations for management
- **Paper backup**: Handwritten report acceptable if system unavailable

**Data Objects Created**:
- `DiagnosticReport` (imaging report with findings)
- `ImagingStudy` (imaging metadata and files)
- `Observation` (quantitative measurements from imaging)

### Rationale

**What Changes**:
1. **Technician quality control optional**: Only if trained technician available
2. **Prior imaging comparison optional**: Only if images digitized and accessible
3. **Standardized protocols flexible**: Adapted to available equipment capabilities
4. **Report generation flexible**: Handwritten acceptable; structured report preferred
5. **Urgent findings communication**: Direct notification to ophthalmologist if abnormality detected

**What Stays**:
1. Test requisition with clinical indication (required)
2. Patient preparation and explanation (required)
3. Image acquisition (required)
4. Clinical interpretation (required)
5. Report generation with recommendations (required)

**New Roles Introduced**:
1. **Trained Staff (Nurse or Technician)**: May perform image acquisition if technician unavailable
2. **Ophthalmologist**: Performs clinical interpretation and report generation

**Optional vs Required Steps**:
- **Required**: Test requisition, patient preparation, image acquisition, clinical interpretation, report generation
- **Optional**: Equipment calibration, quality control check, prior image comparison, written procedure instructions, urgency specification

---

## 4. LASER PROCEDURE

### Original (NHS Context)
- Consultant confirms indication and plans procedure
- Standardized laser parameters used
- Ophthalmologist monitors tissue response and adjusts parameters
- Post-operative medications instilled
- Follow-up imaging scheduled

### Localized (Philippine Context)

**Pre-laser Assessment Phase** (Ophthalmologist)
- **Required**: Confirm diagnosis and indication for laser
- **Required**: Assess suitability for laser (safety, patient cooperation)
- **Required**: Identify target tissue and plan laser parameters
- **Required**: Verify patient consent (verbal acceptable; documented in notes)
- **Optional**: Baseline imaging (OCT, fundus photos) - only if available

**Patient Preparation Phase** (Nurse or Technician)
- **Required**: Verify patient identity and procedure type
- **Required**: Explain procedure in understandable terms
- **Required**: Obtain informed consent (verbal acceptable; documented)
- **Required**: Instill topical anesthesia (if available and indicated)
- **Required**: Position patient at laser
- **Optional**: Apply contact lens (if required and available)
- **Paper backup**: Manual consent form if system unavailable

**Laser Delivery Phase** (Ophthalmologist)
- **Required**: Align laser beam to target tissue
- **Required**: Apply laser energy per planned parameters
- **Required**: Monitor tissue response (visual inspection)
- **Optional**: Adjust parameters based on tissue response (if trained to do so)
- **Required**: Document extent of treatment (number of burns, location, parameters)
- **Paper backup**: Manual documentation of treatment if system unavailable

**Post-laser Assessment Phase** (Ophthalmologist)
- **Required**: Evaluate immediate response to laser
- **Required**: Check for immediate complications (corneal abrasion, hyphema, etc.)
- **Optional**: Instill post-operative medications (if available)
- **Required**: Provide post-operative instructions

**Post-operative Care Phase** (Nurse)
- **Required**: Provide post-operative instructions (activity restrictions, medication use, warning signs)
- **Optional**: Schedule follow-up imaging (only if indicated and patient can afford)
- **Required**: Schedule follow-up examination (1-4 weeks depending on procedure)

**Payment Phase** (Receptionist/Billing Officer)
- **Required**: Collect payment for laser procedure
- **Required**: Assign PhilHealth RVS procedure code (if eligible)
- **Required**: Document payment method (PhilHealth, out-of-pocket, mixed)

**Data Objects Created**:
- `Procedure` (laser procedure with parameters and extent)
- `Observation` (tissue response, complications)
- `CarePlan` (post-operative care instructions)
- `PhilHealthClaim` (if eligible for PhilHealth)

### Rationale

**What Changes**:
1. **Baseline imaging optional**: Only if available; procedure not delayed for imaging
2. **Parameter adjustment optional**: Only if ophthalmologist trained; fixed parameters acceptable
3. **Post-operative medications optional**: Only if available; alternative instructions provided
4. **Follow-up imaging optional**: Only if indicated and patient can afford
5. **RVS code assignment required**: For PhilHealth billing
6. **Verbal consent acceptable**: Documented in notes; written form optional

**What Stays**:
1. Pre-laser assessment and indication confirmation (required)
2. Patient preparation and consent (required)
3. Laser delivery with documentation (required)
4. Post-laser assessment (required)
5. Post-operative instructions (required)
6. Follow-up appointment scheduling (required)

**New Roles Introduced**:
1. **Billing Officer**: Assigns RVS code, collects payment
2. **Nurse**: Provides post-operative instructions

**Optional vs Required Steps**:
- **Required**: Pre-laser assessment, patient preparation, consent, laser delivery, post-laser assessment, post-operative instructions, follow-up scheduling, RVS code assignment, payment collection
- **Optional**: Baseline imaging, parameter adjustment, post-operative medications, follow-up imaging, written consent form

---

## 5. MINOR SURGICAL PROCEDURE (IN-OFFICE)

### Original (NHS Context)
- Time-out performed; sterile field prepared
- Standardized surgical steps documented
- Specimen collected and sent for pathology
- Immediate outcome evaluated
- Complications assessed

### Localized (Philippine Context)

**Pre-operative Preparation Phase** (Ophthalmologist and Nurse)
- **Required**: Verify patient identity and procedure type
- **Required**: Verify informed consent (verbal acceptable; documented)
- **Required**: Obtain baseline vision and IOP (if indicated)
- **Optional**: Perform time-out (name, procedure, site) - simplified version acceptable
- **Required**: Prepare sterile field (basic sterile technique)
- **Optional**: Administer topical anesthesia (if available)
- **Paper backup**: Manual consent form if system unavailable

**Surgical Procedure Phase** (Ophthalmologist)
- **Required**: Perform surgical procedure per planned technique
- **Optional**: Use EyeDraw to diagram procedure site (if time permits; optional)
- **Required**: Document key steps of procedure
- **Optional**: Collect specimen (if indicated; send for pathology if available)
- **Required**: Monitor for intraoperative complications
- **Paper backup**: Manual documentation of procedure if system unavailable

**Post-operative Assessment Phase** (Ophthalmologist)
- **Required**: Evaluate immediate outcome
- **Required**: Check for immediate complications (bleeding, infection, etc.)
- **Optional**: Instill post-operative medications (if available)
- **Required**: Provide post-operative instructions

**Post-operative Care Phase** (Nurse)
- **Required**: Provide post-operative instructions (activity restrictions, medication use, warning signs)
- **Required**: Schedule follow-up examination (1-2 weeks)
- **Optional**: Arrange pathology follow-up (if specimen sent)

**Payment Phase** (Receptionist/Billing Officer)
- **Required**: Collect payment for procedure
- **Required**: Assign PhilHealth RVS procedure code (if eligible)
- **Required**: Document payment method

**Data Objects Created**:
- `Procedure` (surgical procedure with technique and findings)
- `Observation` (outcome, complications)
- `Specimen` (if collected; pathology report if available)
- `CarePlan` (post-operative care instructions)
- `PhilHealthClaim` (if eligible for PhilHealth)

### Rationale

**What Changes**:
1. **Time-out simplified**: Verbal confirmation acceptable; formal time-out optional
2. **EyeDraw optional**: Text documentation acceptable
3. **Specimen handling optional**: Only if pathology services available
4. **Sterile technique flexible**: Basic sterile technique acceptable; full OR-level sterility optional
5. **RVS code assignment required**: For PhilHealth billing
6. **Verbal consent acceptable**: Documented in notes

**What Stays**:
1. Patient verification and consent (required)
2. Sterile field preparation (required)
3. Surgical procedure performance (required)
4. Intraoperative complication monitoring (required)
5. Post-operative assessment (required)
6. Post-operative instructions (required)
7. Follow-up scheduling (required)

**New Roles Introduced**:
1. **Billing Officer**: Assigns RVS code, collects payment
2. **Nurse**: Provides post-operative instructions

**Optional vs Required Steps**:
- **Required**: Patient verification, consent, sterile field preparation, surgical procedure, intraoperative monitoring, post-operative assessment, post-operative instructions, follow-up scheduling, RVS code assignment, payment collection
- **Optional**: Time-out, EyeDraw documentation, specimen collection, post-operative medications, pathology follow-up

---

## 6. MAJOR SURGICAL PROCEDURE (OPERATING THEATRE)

### Original (NHS Context)
- Standardized pre-operative workup (labs, imaging, anesthesia clearance)
- Biometry reviewed; IOL power calculated
- Standardized equipment; trained OR staff
- Intraoperative imaging if needed
- Implant documentation detailed
- Post-operative imaging obtained

### Localized (Philippine Context)

**Pre-operative Workup Phase** (Ophthalmologist and Nurse)
- **Required**: Verify patient identity and procedure type
- **Required**: Verify informed consent (verbal acceptable; documented)
- **Optional**: Obtain pre-operative labs (only if available and indicated)
- **Optional**: Obtain anesthesia clearance (if anesthesiologist available)
- **Optional**: Obtain pre-operative imaging (if available and indicated)
- **Required**: Verify biometry (if cataract surgery)
- **Optional**: Calculate IOL power (if biometry available; manual calculation acceptable)
- **Required**: Verify implant availability and selection
- **Paper backup**: Manual pre-operative checklist if system unavailable

**Pre-operative Planning Phase** (Ophthalmologist)
- **Required**: Plan surgical technique
- **Required**: Verify implant selection and power (if applicable)
- **Required**: Identify potential complications and contingency plans
- **Optional**: Review prior imaging (if available)

**Operating Theatre Phase** (Ophthalmologist and OR Staff)
- **Required**: Perform surgical procedure per planned technique
- **Required**: Monitor for intraoperative complications
- **Optional**: Obtain intraoperative imaging (only if available and indicated)
- **Required**: Document implant details (type, power, position) if applicable
- **Required**: Document surgical technique and key steps
- **Paper backup**: Manual operative notes if system unavailable

**Post-operative Assessment Phase** (Ophthalmologist)
- **Required**: Evaluate immediate outcome
- **Required**: Check for immediate complications
- **Required**: Provide post-operative instructions

**Post-operative Care Phase** (Nurse)
- **Required**: Monitor vital signs and eye condition
- **Required**: Administer post-operative medications (if available)
- **Required**: Provide post-operative instructions
- **Optional**: Obtain post-operative imaging (only if indicated and patient can afford)
- **Required**: Schedule follow-up examination (1 week, 1 month, 3 months)

**Discharge Planning Phase** (Ophthalmologist and Nurse)
- **Required**: Verify readiness for discharge
- **Required**: Provide discharge medications (if available)
- **Required**: Provide discharge instructions
- **Required**: Schedule follow-up appointments

**Payment Phase** (Receptionist/Billing Officer)
- **Required**: Collect payment for procedure
- **Required**: Assign PhilHealth RVS procedure code (if eligible)
- **Required**: Document payment method

**Data Objects Created**:
- `Procedure` (surgical procedure with technique and implant details)
- `Observation` (outcome, complications)
- `CarePlan` (post-operative care instructions, discharge plan)
- `PhilHealthClaim` (if eligible for PhilHealth)

### Rationale

**What Changes**:
1. **Pre-operative workup abbreviated**: Labs/imaging only if available and indicated
2. **Anesthesia clearance optional**: Only if anesthesiologist available
3. **IOL calculation flexible**: Manual calculation acceptable if biometry available
4. **Intraoperative imaging optional**: Only if available and indicated
5. **Post-operative imaging optional**: Only if indicated and patient can afford
6. **RVS code assignment required**: For PhilHealth billing
7. **Verbal consent acceptable**: Documented in notes

**What Stays**:
1. Patient verification and consent (required)
2. Biometry verification (required if cataract surgery)
3. Implant verification and selection (required if applicable)
4. Surgical procedure performance (required)
5. Intraoperative complication monitoring (required)
6. Implant documentation (required if applicable)
7. Post-operative assessment (required)
8. Post-operative care (required)
9. Discharge planning (required)
10. Follow-up scheduling (required)

**New Roles Introduced**:
1. **Billing Officer**: Assigns RVS code, collects payment
2. **Anesthesiologist (if available)**: Provides anesthesia clearance and intraoperative anesthesia

**Optional vs Required Steps**:
- **Required**: Patient verification, consent, biometry verification, implant verification, surgical procedure, intraoperative monitoring, implant documentation, post-operative assessment, post-operative care, discharge planning, follow-up scheduling, RVS code assignment, payment collection
- **Optional**: Pre-operative labs, anesthesia clearance, pre-operative imaging, IOL calculation, intraoperative imaging, post-operative imaging, discharge medications

---

## 7. EMERGENCY EYE PRESENTATION

### Original (NHS Context)
- Nurse performs rapid triage
- Rapid ophthalmologic assessment
- Sight-threatening pathology identified
- Initial management performed
- Disposition determined (admission, OR, discharge)

### Localized (Philippine Context)

**Rapid Triage Phase** (Nurse or Receptionist)
- **Required**: Verify patient identity
- **Required**: Assess severity (pain, vision loss, trauma, chemical exposure)
- **Required**: Identify sight-threatening features (sudden vision loss, severe pain, chemical burn, globe rupture)
- **Required**: Notify ophthalmologist immediately if sight-threatening features present
- **Paper backup**: Manual triage form if system unavailable

**Emergency Examination Phase** (Ophthalmologist)
- **Required**: Perform rapid ophthalmic assessment
- **Required**: Identify sight-threatening pathology
- **Required**: Assess visual acuity (if possible)
- **Required**: Assess intraocular pressure (if possible)
- **Optional**: Obtain imaging (only if available and does not delay treatment)
- **Required**: Formulate working diagnosis

**Initial Management Phase** (Ophthalmologist and Nurse)
- **Required**: Stabilize eye condition (instill medications, apply dressing, etc.)
- **Required**: Prevent further deterioration
- **Required**: Manage pain (topical anesthesia, systemic analgesia if available)
- **Optional**: Obtain imaging for documentation (only if does not delay treatment)
- **Required**: Determine disposition

**Disposition Phase** (Ophthalmologist)
- **Required**: Determine appropriate care level:
  - Discharge with outpatient follow-up (for minor conditions)
  - Admission for observation (for moderate conditions)
  - Emergency OR (for sight-threatening conditions)
  - Referral to higher-level facility (if capability unavailable)
- **Required**: Communicate disposition to patient and family
- **Required**: Arrange transportation if referral needed

**Follow-up Phase** (Receptionist/Billing Officer)
- **Required**: Schedule urgent follow-up (24-48 hours for most emergencies)
- **Required**: Provide follow-up instructions
- **Required**: Collect payment (if patient able to pay; may defer if unable)
- **Paper backup**: Manual follow-up instructions if system unavailable

**Data Objects Created**:
- `Encounter` (emergency visit)
- `Observation` (visual acuity, IOP, findings)
- `Condition` (diagnosis)
- `CarePlan` (initial management, disposition, follow-up)
- `PhilHealthClaim` (if eligible for PhilHealth)

### Rationale

**What Changes**:
1. **Rapid triage by nurse/receptionist**: Formal triage protocol simplified
2. **Imaging optional**: Only if available and does not delay treatment
3. **Disposition flexible**: Based on facility capability and patient ability to pay
4. **Payment deferred if unable**: Ensures care not withheld due to inability to pay
5. **Referral pathway**: To higher-level facility if capability unavailable

**What Stays**:
1. Rapid triage and severity assessment (required)
2. Rapid ophthalmic assessment (required)
3. Sight-threatening pathology identification (required)
4. Initial management (required)
5. Disposition determination (required)
6. Follow-up scheduling (required)

**New Roles Introduced**:
1. **Receptionist**: May perform initial triage
2. **Billing Officer**: Arranges payment; may defer if unable to pay

**Optional vs Required Steps**:
- **Required**: Rapid triage, severity assessment, ophthalmic assessment, sight-threatening pathology identification, initial management, disposition determination, follow-up scheduling
- **Optional**: Imaging, formal triage protocol, payment collection (may defer if unable)

---

## 8. INPATIENT ADMISSION & MANAGEMENT

### Original (NHS Context)
- Baseline examination performed; baseline vision and IOP documented
- Consultant performs daily examination
- Medications administered on schedule
- Vital signs monitored
- Discharge planning performed
- Discharge summary with clear follow-up plan

### Localized (Philippine Context)

**Admission Phase** (Ophthalmologist and Nurse)
- **Required**: Verify patient identity and admission indication
- **Required**: Obtain informed consent for admission and treatment (verbal acceptable; documented)
- **Required**: Perform baseline examination (visual acuity, IOP, anterior/posterior segment)
- **Required**: Document baseline findings
- **Required**: Assess comorbidities and medication list
- **Optional**: Obtain baseline imaging (only if indicated and available)
- **Required**: Establish baseline pain level and symptoms
- **Paper backup**: Manual admission form if system unavailable

**Daily Management Phase** (Ophthalmologist or Resident)
- **Required**: Perform daily examination (may be abbreviated if stable)
- **Required**: Assess clinical progress
- **Required**: Monitor for complications
- **Required**: Adjust medications as needed
- **Optional**: Obtain repeat imaging (only if indicated and available)
- **Required**: Document daily findings
- **Paper backup**: Manual daily notes if system unavailable

**Nursing Care Phase** (Nurse)
- **Required**: Administer medications on schedule (if available)
- **Required**: Monitor vital signs (BP, pulse, temperature)
- **Required**: Provide eye care (instill medications, apply dressing, etc.)
- **Required**: Monitor for complications
- **Required**: Provide patient comfort and education
- **Optional**: Obtain repeat imaging (only if indicated and available)

**Discharge Planning Phase** (Ophthalmologist and Nurse)
- **Required**: Assess readiness for discharge
- **Required**: Provide discharge medications (if available)
- **Required**: Provide discharge instructions (activity restrictions, medication use, warning signs)
- **Required**: Schedule follow-up appointment (1-2 weeks)
- **Optional**: Provide written discharge summary (if time permits; verbal summary acceptable)
- **Paper backup**: Manual discharge instructions if system unavailable

**Payment Phase** (Receptionist/Billing Officer)
- **Required**: Collect payment for admission (daily rate or lump sum)
- **Required**: Collect payment for procedures/imaging
- **Required**: Assign PhilHealth RVS procedure codes (if eligible)
- **Required**: Prepare PhilHealth claim (if eligible)

**Data Objects Created**:
- `Encounter` (inpatient admission)
- `Observation` (baseline and daily findings)
- `CarePlan` (admission plan, daily management, discharge plan)
- `MedicationStatement` (medications administered)
- `PhilHealthClaim` (if eligible for PhilHealth)

### Rationale

**What Changes**:
1. **Daily examination flexible**: May be abbreviated if stable; resident-led acceptable
2. **Baseline imaging optional**: Only if indicated and available
3. **Repeat imaging optional**: Only if indicated and available
4. **Discharge summary optional**: Verbal summary acceptable; written preferred
5. **RVS code assignment required**: For PhilHealth billing
6. **Verbal consent acceptable**: Documented in notes

**What Stays**:
1. Baseline examination and documentation (required)
2. Daily examination and assessment (required)
3. Medication administration (required if prescribed)
4. Vital signs monitoring (required)
5. Complication monitoring (required)
6. Discharge planning (required)
7. Follow-up scheduling (required)

**New Roles Introduced**:
1. **Billing Officer**: Assigns RVS codes, prepares PhilHealth claim
2. **Resident**: May perform daily examination

**Optional vs Required Steps**:
- **Required**: Admission examination, baseline documentation, daily examination, medication administration, vital signs monitoring, complication monitoring, discharge planning, follow-up scheduling, RVS code assignment, payment collection
- **Optional**: Baseline imaging, repeat imaging, written discharge summary

---

## 9. PATIENT REGISTRATION & DEMOGRAPHICS

### Original (NHS Context)
- Check if patient is in system; retrieve existing record
- Patient demographics entered into system
- PhilHealth eligibility verified
- Patient ID card printed
- Registration form filed
- Appointment scheduled

### Localized (Philippine Context)

**Verification Phase** (Receptionist)
- **Required**: Ask if patient has been to facility before
- **Optional**: Check system for existing record (only if system available)
- **Required**: If not in system or system unavailable, proceed with new registration
- **Paper backup**: Manual patient list if system unavailable

**Data Entry Phase** (Receptionist)
- **Required**: Collect patient demographics (name, age, sex, address, contact)
- **Required**: Collect emergency contact information
- **Required**: Collect PhilHealth ID (if available)
- **Optional**: Verify PhilHealth eligibility (if system available; may defer to billing)
- **Optional**: Collect insurance information (if applicable)
- **Required**: Assign patient ID (system-generated or manual)
- **Paper backup**: Manual registration form if system unavailable

**Documentation Phase** (Receptionist)
- **Required**: Create patient record (digital or paper)
- **Optional**: Print patient ID card (if printer available)
- **Required**: File registration form (paper backup)
- **Optional**: Provide patient with copy of registration (if printer available)

**Appointment Scheduling Phase** (Receptionist)
- **Required**: Schedule appointment (or note walk-in status)
- **Optional**: Provide written appointment card (if printer available)
- **Required**: Provide verbal appointment confirmation
- **Paper backup**: Manual appointment record if system unavailable

**Data Objects Created**:
- `Patient` (patient demographics and contact information)
- `PatientID` (unique patient identifier)
- `Appointment` (scheduled appointment or walk-in status)

### Rationale

**What Changes**:
1. **System check optional**: Only if system available; manual verification acceptable
2. **PhilHealth verification deferred**: May be done at billing stage
3. **Patient ID card optional**: Only if printer available
4. **Written appointment card optional**: Verbal confirmation acceptable
5. **Paper backup required**: All information recorded on paper form

**What Stays**:
1. Patient demographics collection (required)
2. Patient ID assignment (required)
3. Patient record creation (required)
4. Appointment scheduling (required)

**New Roles Introduced**:
1. **Receptionist**: Performs registration, verification, appointment scheduling

**Optional vs Required Steps**:
- **Required**: Patient verification, demographics collection, patient ID assignment, patient record creation, appointment scheduling, verbal appointment confirmation
- **Optional**: System check, PhilHealth eligibility verification, patient ID card printing, written appointment card, insurance information collection

---

## 10. APPOINTMENT SCHEDULING

### Original (NHS Context)
- Clinical urgency determined
- Specialist assigned
- Appointment duration estimated
- Specialist availability checked
- Time slot offered
- Appointment confirmed
- Appointment reminder sent

### Localized (Philippine Context)

**Urgency Assessment Phase** (Receptionist or Nurse)
- **Required**: Assess clinical urgency (routine, urgent, stat)
- **Required**: Determine appropriate specialist (if multiple available)
- **Required**: Estimate appointment duration (based on procedure type)
- **Paper backup**: Manual urgency assessment form if system unavailable

**Scheduling Phase** (Receptionist)
- **Required**: Check specialist availability (if known; may be informal)
- **Required**: Offer available time slot
- **Optional**: Check system for available slots (only if system available)
- **Required**: Confirm appointment with patient (verbal)
- **Optional**: Provide written appointment card (if printer available)
- **Paper backup**: Manual appointment record if system unavailable

**Reminder Phase** (Receptionist)
- **Optional**: Send appointment reminder (SMS or phone call) - only if patient has contact information
- **Required**: Expect walk-in patients and accommodate if possible
- **Paper backup**: Manual reminder system if SMS unavailable

**Data Objects Created**:
- `Appointment` (scheduled appointment with urgency, specialist, time)
- `Reminder` (appointment reminder if sent)

### Rationale

**What Changes**:
1. **Specialist availability check informal**: May not be known in advance
2. **System check optional**: Only if system available; manual scheduling acceptable
3. **Appointment reminder optional**: Only if SMS/phone available
4. **Walk-in accommodation**: Expected and accommodated
5. **Written appointment card optional**: Verbal confirmation acceptable

**What Stays**:
1. Urgency assessment (required)
2. Specialist assignment (required)
3. Appointment scheduling (required)
4. Appointment confirmation (required)

**New Roles Introduced**:
1. **Receptionist**: Performs urgency assessment, scheduling, confirmation
2. **Nurse**: May assist with urgency assessment

**Optional vs Required Steps**:
- **Required**: Urgency assessment, specialist assignment, appointment scheduling, appointment confirmation, verbal confirmation
- **Optional**: System check, specialist availability verification, appointment reminder, written appointment card

---

## 11. REFERRAL MANAGEMENT

### Original (NHS Context)
- Referring clinician documents indication
- Attaches imaging/reports
- Specifies urgency
- Referral sent via secure channel
- Receiving facility receives and schedules
- Feedback communication sent

### Localized (Philippine Context)

**Referral Generation Phase** (Ophthalmologist)
- **Required**: Document referral indication
- **Optional**: Attach imaging/reports (only if available and patient willing to carry)
- **Required**: Specify urgency (routine, urgent, stat)
- **Required**: Specify receiving facility (satellite clinic, tertiary center, private specialist)
- **Paper backup**: Manual referral form if system unavailable

**Referral Documentation Phase** (Receptionist)
- **Required**: Complete referral form (paper or digital)
- **Required**: Include patient demographics and contact information
- **Required**: Include clinical indication and urgency
- **Optional**: Attach imaging (if available; patient may carry on CD/USB)
- **Required**: Provide copy to patient

**Referral Transmission Phase** (Receptionist or Patient)
- **Required**: Transmit referral to receiving facility:
  - Hand-carried by patient (most common)
  - Faxed (if fax available)
  - Emailed (if email available and secure)
  - Verbal communication followed by written referral
- **Required**: Document transmission method and date
- **Paper backup**: Manual referral tracking if system unavailable

**Referral Reception Phase** (Receiving Facility)
- **Required**: Receive referral and verify patient information
- **Required**: Schedule appointment (or note walk-in status)
- **Optional**: Communicate appointment to referring facility (only if system available)
- **Paper backup**: Manual referral receipt if system unavailable

**Feedback Phase** (Receiving Facility)
- **Optional**: Send feedback to referring facility (only if system available or willing to communicate)
- **Required**: Provide copy of report to patient (for carry-back to referring facility)

**Data Objects Created**:
- `ServiceRequest` (referral request)
- `Referral` (referral details with urgency and indication)
- `Appointment` (appointment at receiving facility)

### Rationale

**What Changes**:
1. **Imaging attachment optional**: Only if available; patient may carry on CD/USB
2. **Transmission method flexible**: Hand-carried most common; fax/email if available
3. **Feedback optional**: Only if system available or willing to communicate
4. **Patient carries referral**: Most common method in Philippine context
5. **Verbal communication acceptable**: Followed by written referral

**What Stays**:
1. Referral indication documentation (required)
2. Urgency specification (required)
3. Receiving facility specification (required)
4. Referral transmission (required)
5. Appointment scheduling (required)

**New Roles Introduced**:
1. **Receptionist**: Completes referral form, transmits referral, tracks referral
2. **Patient**: Carries referral to receiving facility

**Optional vs Required Steps**:
- **Required**: Referral indication documentation, urgency specification, receiving facility specification, referral transmission, appointment scheduling, copy to patient
- **Optional**: Imaging attachment, feedback communication, appointment confirmation to referring facility

---

## 12. PHILHEALTH CLAIM PREPARATION & SUBMISSION

### Original (NHS Context)
- Encounter data extracted from EMR
- Billable diagnosis/procedures identified
- ICD-10 diagnosis codes assigned
- RVS procedure codes assigned
- PhilHealth eClaims form populated
- Supporting documentation attached
- Claim submitted via eClaims system
- Claim status tracked

### Localized (Philippine Context)

**Data Extraction Phase** (Billing Officer or Ophthalmologist)
- **Required**: Extract encounter data from patient record (digital or paper)
- **Required**: Identify billable diagnosis (primary diagnosis required; secondary optional)
- **Required**: Identify billable procedures (if any)
- **Required**: Identify billable imaging/diagnostics (if any)
- **Paper backup**: Manual data extraction form if system unavailable

**Coding Phase** (Billing Officer)
- **Required**: Assign ICD-10 diagnosis code(s)
- **Required**: Assign RVS procedure code(s) (if procedures performed)
- **Required**: Verify coding accuracy (reference table or system)
- **Optional**: Obtain coding clarification from ophthalmologist (if uncertain)
- **Paper backup**: Manual coding reference table if system unavailable

**Claim Assembly Phase** (Billing Officer)
- **Required**: Populate PhilHealth eClaims form (or paper form if system unavailable)
- **Required**: Include patient demographics and PhilHealth ID
- **Required**: Include diagnosis code(s) and RVS code(s)
- **Required**: Include charges (consultation, procedures, imaging)
- **Optional**: Attach supporting documentation (imaging, operative notes) - only if required by PhilHealth
- **Required**: Verify completeness of form
- **Paper backup**: Manual form completion if system unavailable

**Submission Phase** (Billing Officer)
- **Required**: Submit claim via PhilHealth eClaims system (if available and internet available)
- **Optional**: Submit claim via paper form (if eClaims system unavailable)
- **Required**: Record submission date and claim ID
- **Required**: Keep copy of submitted claim
- **Paper backup**: Manual submission tracking if system unavailable

**Follow-up Phase** (Billing Officer)
- **Required**: Track claim status (approved, denied, pending)
- **Required**: Address denials (resubmit with corrected information)
- **Required**: Reconcile reimbursement (verify payment received)
- **Optional**: Provide patient with reimbursement information (if patient paid out-of-pocket)
- **Paper backup**: Manual claim tracking if system unavailable

**Data Objects Created**:
- `PhilHealthClaim` (claim with diagnosis/procedure codes)
- `ClaimSubmission` (submission details and status)
- `ClaimDenial` (if denied; reason for denial)

### Rationale

**What Changes**:
1. **Automated coding optional**: Manual coding acceptable; reference table provided
2. **eClaims submission optional**: Paper form acceptable if system unavailable
3. **Supporting documentation optional**: Only if required by PhilHealth
4. **Offline claim preparation**: Supported; submission when internet available
5. **Coding validation required**: To prevent rejections

**What Stays**:
1. Data extraction (required)
2. Diagnosis and procedure identification (required)
3. ICD-10 and RVS code assignment (required)
4. Claim form completion (required)
5. Claim submission (required)
6. Claim status tracking (required)
7. Denial management (required)

**New Roles Introduced**:
1. **Billing Officer**: Performs data extraction, coding, claim assembly, submission, follow-up
2. **Ophthalmologist**: May provide coding clarification

**Optional vs Required Steps**:
- **Required**: Data extraction, diagnosis/procedure identification, ICD-10/RVS code assignment, coding verification, claim form completion, claim submission, claim status tracking, denial management
- **Optional**: Automated coding, eClaims submission (paper acceptable), supporting documentation attachment, patient reimbursement information

---

## 13. PRESCRIPTION & MEDICATION MANAGEMENT

### Original (NHS Context)
- Medication selected from formulary
- Dosage/frequency specified
- Indication documented
- Pharmacist verifies prescription
- Medication prepared and labeled
- Patient education provided

### Localized (Philippine Context)

**Prescription Generation Phase** (Ophthalmologist)
- **Required**: Select medication (from available formulary or substitute if unavailable)
- **Required**: Specify dosage and frequency
- **Required**: Specify indication
- **Required**: Specify duration (if limited course)
- **Optional**: Specify quantity (if cost-sensitive patient)
- **Required**: Document allergy history
- **Paper backup**: Manual prescription form if system unavailable

**Prescription Review Phase** (Pharmacist or Nurse)
- **Optional**: Verify prescription (only if pharmacist available)
- **Optional**: Check for drug interactions (only if pharmacist available)
- **Optional**: Confirm dosage appropriateness (only if pharmacist available)
- **Required**: Verify patient allergy history

**Dispensing Phase** (Pharmacist or Nurse)
- **Required**: Prepare medication (or dispense from stock)
- **Required**: Label medication with patient name, drug name, dosage, frequency, indication
- **Required**: Provide medication to patient
- **Optional**: Provide written medication instructions (if available)

**Patient Education Phase** (Pharmacist or Nurse)
- **Required**: Explain medication purpose
- **Optional**: Demonstrate administration technique (if applicable)
- **Optional**: Discuss side effects (if time permits)
- **Required**: Provide verbal instructions
- **Paper backup**: Written instructions if available

**Medication Affordability Phase** (Billing Officer or Pharmacist)
- **Required**: Discuss medication cost with patient
- **Optional**: Suggest generic alternatives (if available and more affordable)
- **Optional**: Suggest PhilHealth-covered alternatives (if available)
- **Required**: Assess patient ability to afford medication
- **Required**: Document affordability issues (for follow-up assessment)

**Data Objects Created**:
- `Medication` (medication details)
- `MedicationRequest` (prescription)
- `MedicationDispense` (dispensed medication)
- `MedicationStatement` (patient medication history)

### Rationale

**What Changes**:
1. **Pharmacist verification optional**: Only if pharmacist available
2. **Drug interaction checking optional**: Only if pharmacist available
3. **Written instructions optional**: Verbal instructions acceptable
4. **Affordability assessment required**: To identify non-compliance due to cost
5. **Generic alternatives offered**: If more affordable
6. **PhilHealth-covered alternatives offered**: If available

**What Stays**:
1. Medication selection (required)
2. Dosage and frequency specification (required)
3. Indication documentation (required)
4. Medication dispensing (required)
5. Medication labeling (required)
6. Patient education (required)

**New Roles Introduced**:
1. **Pharmacist**: May verify prescription and provide patient education
2. **Billing Officer**: Assesses medication affordability

**Optional vs Required Steps**:
- **Required**: Medication selection, dosage/frequency specification, indication documentation, allergy history verification, medication dispensing, medication labeling, patient education, affordability assessment
- **Optional**: Pharmacist verification, drug interaction checking, written instructions, side effect discussion, generic alternative suggestion, PhilHealth alternative suggestion

---

## 14. CORRESPONDENCE & COMMUNICATION

### Original (NHS Context)
- Clinical summary dictated/typed
- Findings included
- Management plan specified
- Letter formatted per institutional standards
- Proofread
- Signed
- Sent to referring clinician

### Localized (Philippine Context)

**Letter Generation Phase** (Ophthalmologist or Resident)
- **Required**: Generate clinical summary (dictated, typed, or handwritten)
- **Required**: Include key findings
- **Required**: Include management plan
- **Optional**: Include detailed examination findings (if time permits)
- **Optional**: Include imaging descriptions (if images obtained)
- **Paper backup**: Handwritten letter acceptable

**Review & Formatting Phase** (Ophthalmologist or Secretary)
- **Optional**: Format letter per institutional standards (if secretary available)
- **Optional**: Proofread letter (if secretary available)
- **Required**: Review for accuracy
- **Paper backup**: Handwritten letter acceptable without formatting

**Signature & Dispatch Phase** (Ophthalmologist)
- **Required**: Sign letter
- **Required**: Dispatch letter to referring clinician:
  - Hand-carried by patient (most common)
  - Faxed (if fax available)
  - Mailed (if time permits)
  - Emailed (if email available and secure)
- **Required**: Provide copy to patient
- **Paper backup**: Handwritten letter acceptable

**Data Objects Created**:
- `Communication` (clinical summary/letter)
- `Referral` (if referral letter)

### Rationale

**What Changes**:
1. **Detailed formatting optional**: Handwritten letter acceptable
2. **Proofreading optional**: Only if secretary available
3. **Dispatch method flexible**: Hand-carried most common
4. **Dictation optional**: Typing or handwriting acceptable
5. **Detailed examination findings optional**: Key findings sufficient

**What Stays**:
1. Clinical summary generation (required)
2. Key findings inclusion (required)
3. Management plan inclusion (required)
4. Signature (required)
5. Dispatch to referring clinician (required)
6. Copy to patient (required)

**New Roles Introduced**:
1. **Secretary**: May format and proofread letter (if available)
2. **Patient**: Carries letter to referring clinician

**Optional vs Required Steps**:
- **Required**: Clinical summary generation, key findings inclusion, management plan inclusion, signature, dispatch, copy to patient
- **Optional**: Detailed formatting, proofreading, detailed examination findings, imaging descriptions, dictation

---

## SUMMARY TABLE: OPTIONAL VS REQUIRED STEPS BY WORKFLOW

| Workflow | Required Steps | Optional Steps | Key Adaptations |
|----------|---|---|---|
| **New Patient Consultation** | Vital signs, VA, IOP, slit lamp, posterior exam, diagnosis, ICD-10 code, management plan, patient communication, payment arrangement | Fundus photography, OCT, biometry, dilation, EyeDraw, written consent, patient education, written appointment card | Technician role optional; dilation optional; EyeDraw optional; verbal consent acceptable |
| **Follow-up Consultation** | Interval history, focused exam, clinical assessment, plan modification, patient communication, appointment scheduling | Repeat VA/IOP, repeat OCT, prior image comparison, written appointment card | Repeat measurements optional; prior image comparison optional |
| **Diagnostic Imaging** | Test requisition, patient preparation, image acquisition, clinical interpretation, report generation | Equipment calibration, quality control check, prior image comparison, written instructions | Quality control optional; prior comparison optional |
| **Laser Procedure** | Pre-laser assessment, patient preparation, consent, laser delivery, post-laser assessment, post-operative instructions, follow-up scheduling, RVS code, payment | Baseline imaging, parameter adjustment, post-operative medications, follow-up imaging, written consent | Baseline imaging optional; parameter adjustment optional; post-operative meds optional |
| **Minor Surgery** | Patient verification, consent, sterile field, surgical procedure, intraoperative monitoring, post-operative assessment, post-operative instructions, follow-up scheduling, RVS code, payment | Time-out, EyeDraw, specimen collection, post-operative medications, pathology follow-up | Time-out simplified; EyeDraw optional; specimen optional |
| **Major Surgery** | Patient verification, consent, biometry verification, implant verification, surgical procedure, intraoperative monitoring, implant documentation, post-operative assessment, post-operative care, discharge planning, follow-up scheduling, RVS code, payment | Pre-operative labs, anesthesia clearance, pre-operative imaging, IOL calculation, intraoperative imaging, post-operative imaging, discharge medications | Pre-operative workup abbreviated; anesthesia clearance optional; imaging optional |
| **Emergency Presentation** | Rapid triage, severity assessment, ophthalmic assessment, sight-threatening pathology identification, initial management, disposition, follow-up scheduling | Imaging, formal triage protocol, payment collection | Imaging optional; payment may be deferred |
| **Inpatient Admission** | Admission exam, baseline documentation, daily exam, medication administration, vital signs monitoring, complication monitoring, discharge planning, follow-up scheduling, RVS code, payment | Baseline imaging, repeat imaging, written discharge summary | Imaging optional; daily exam may be abbreviated; written summary optional |
| **Patient Registration** | Patient verification, demographics collection, patient ID assignment, patient record creation, appointment scheduling, verbal confirmation | System check, PhilHealth verification, patient ID card printing, written appointment card | System check optional; PhilHealth verification deferred; written card optional |
| **Appointment Scheduling** | Urgency assessment, specialist assignment, appointment scheduling, appointment confirmation, verbal confirmation | System check, specialist availability verification, appointment reminder, written appointment card | System check optional; reminder optional; written card optional |
| **Referral Management** | Referral indication documentation, urgency specification, receiving facility specification, referral transmission, appointment scheduling, copy to patient | Imaging attachment, feedback communication, appointment confirmation to referring facility | Imaging attachment optional; feedback optional; patient carries referral |
| **PhilHealth Claims** | Data extraction, diagnosis/procedure identification, ICD-10/RVS code assignment, coding verification, claim form completion, claim submission, claim status tracking, denial management | Automated coding, eClaims submission, supporting documentation, patient reimbursement info | Automated coding optional; paper form acceptable; offline preparation supported |
| **Prescription Management** | Medication selection, dosage/frequency specification, indication documentation, allergy verification, medication dispensing, medication labeling, patient education, affordability assessment | Pharmacist verification, drug interaction checking, written instructions, side effect discussion, generic alternatives, PhilHealth alternatives | Pharmacist verification optional; written instructions optional; affordability assessment required |
| **Correspondence** | Clinical summary generation, key findings inclusion, management plan inclusion, signature, dispatch, copy to patient | Detailed formatting, proofreading, detailed findings, imaging descriptions, dictation | Handwritten acceptable; formatting optional; proofreading optional |

---

## KEY DESIGN PRINCIPLES FOR PHILIPPINE CONTEXT

1. **Offline-first**: All workflows must function without internet connectivity
2. **Paper coexistence**: All digital steps have paper-based alternatives
3. **Physician-led**: Workflows accommodate physician-led processes; specialist roles flexible
4. **Cost-conscious**: Affordability assessment integrated; alternatives offered
5. **Flexible roles**: Staff roles substitutable based on availability
6. **Simplified processes**: Abbreviated workflows acceptable when resources limited
7. **PhilHealth integration**: ICD-10 and RVS coding required; eClaims support optional
8. **Resilience**: Workflows continue despite equipment failures, staff absence, power outages
9. **Local language**: Support for Filipino/Tagalog documentation and patient communication
10. **Modular design**: Workflows independent; optional steps can be skipped without breaking workflow

---

## IMPLEMENTATION PRIORITIES

### Phase 1 (Immediate)
- Patient registration and appointment scheduling (foundation)
- New patient consultation (core workflow)
- PhilHealth claim preparation (revenue critical)

### Phase 2 (Short-term)
- Follow-up consultation (continuity of care)
- Diagnostic imaging and testing (clinical support)
- Laser procedures (revenue-generating)

### Phase 3 (Medium-term)
- Minor and major surgical procedures (complex workflows)
- Inpatient admission and management (resource-intensive)
- Emergency presentations (safety-critical)

### Phase 4 (Long-term)
- Referral management (inter-facility coordination)
- Prescription management (medication tracking)
- Correspondence and communication (documentation)

