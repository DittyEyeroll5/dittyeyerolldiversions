# NHS-Specific Assumptions Embedded in OpenEyes Clinical Workflow Inventory
## Analysis for Philippine Tertiary Ophthalmology Adaptation

---

## COMPREHENSIVE ASSUMPTION ANALYSIS TABLE

| Workflow | Embedded NHS Assumption | Clinical/Operational Impact | Why It Matters | Risk in PH Context | Adaptation Required |
|----------|------------------------|---------------------------|-----------------|-------------------|-------------------|
| **NEW PATIENT OUTPATIENT CONSULTATION** | | | | | |
| Pre-exam | Trained ophthalmic technician available to perform VA, IOP, photography | Baseline measurements obtained before physician sees patient; standardized pre-exam protocol | Reduces physician time; ensures complete data capture; enables efficient triage | Technician may not be available; VA/IOP may be performed by nurse or physician; photography often skipped due to equipment unavailability | Workflow must accommodate physician-performed pre-exam; make technician involvement optional; support abbreviated pre-exam |
| Pre-exam | Diagnostic imaging (OCT, fundus photography) available and functional | Imaging integrated into initial visit; supports diagnosis | Improves diagnostic accuracy; documents baseline for follow-up | Equipment frequently broken or unavailable; imaging may be delayed days/weeks; patients may not return for imaging | Design offline imaging storage; allow workflow continuation without imaging; support asynchronous imaging |
| Examination | Consultant or senior resident performs initial examination | Specialist-level assessment from first contact | Ensures appropriate triage; prevents missed diagnoses | Consultant may not be present; resident may conduct initial exam without supervision; junior staff may lack experience | Support resident-led examination with consultant review; allow deferred specialist assessment |
| Examination | Dilated fundus examination performed routinely | Complete posterior segment assessment | Identifies posterior pathology; prevents missed diagnoses | Mydriasis contraindicated in narrow angles (not always screened first); patient may refuse dilation; time constraints limit dilation | Make dilation optional; support undilated examination documentation; flag high-risk cases for mandatory dilation |
| Examination | EyeDraw tool used for anatomical notation | Standardized, graphical documentation; supports clinical communication | Improves documentation quality; enables visual communication with other clinicians | Staff unfamiliar with EyeDraw; time constraints limit drawing; may be perceived as additional burden | Provide simplified drawing templates; make EyeDraw optional; support text-only documentation |
| Diagnosis | Single diagnosis assigned (primary condition) | Focused management plan | Simplifies decision-making; aligns with billing | Patients often have multiple conditions; comorbidities common (diabetes, hypertension); unclear which to prioritize | Support multiple diagnoses; require primary diagnosis for billing but allow secondary diagnoses |
| Management Plan | Standardized management pathways (medical, laser, surgical, referral) | Clear decision tree; reduces variation | Improves consistency; enables outcome tracking | Pathways may not align with local practice; patient preference/cost often drives decisions; limited surgical capacity | Provide flexible pathways; allow deviation documentation; support cost-based decision-making |
| Patient Communication | Informed consent obtained before any intervention | Legal protection; patient autonomy | Meets ethical standards; reduces liability | Consent often verbal/informal; limited patient health literacy; time constraints | Support simplified consent forms; allow verbal consent documentation; provide patient education materials in local language |
| Outputs | PhilHealth-compliant diagnosis code (ICD-10) assigned | Enables reimbursement | Mandatory for PhilHealth claims | ICD-10 coding knowledge limited; mapping from SNOMED not standardized; coding errors common | Provide ICD-10 coding reference; automate SNOMED-to-ICD-10 mapping; implement coding validation |
| **FOLLOW-UP/REVIEW CONSULTATION** | | | | | |
| Interval History | Structured medication adherence assessment | Identifies non-compliance; enables intervention | Improves treatment efficacy | Medication adherence often poor; patients may not afford medications; limited patient education | Support simplified adherence assessment; flag affordability issues; provide medication alternatives |
| Examination | Repeat key measurements (VA, IOP, OCT) for comparison | Objective assessment of disease progression | Enables quantitative monitoring; supports treatment decisions | OCT may not be available; IOP measurement may be skipped; VA may not be repeated | Make repeat measurements optional; support clinical assessment without measurements; allow qualitative comparison |
| Comparison Analysis | Prior imaging automatically retrieved and displayed | Side-by-side comparison; enables trend analysis | Improves diagnostic accuracy; supports treatment decisions | Prior imaging may not be digitized; paper records may be lost; different equipment used | Support manual comparison; allow narrative description of changes; provide comparison template |
| Plan Modification | Treatment escalation follows standardized protocols | Consistent, evidence-based management | Improves outcomes; reduces variation | Escalation may be limited by cost/availability; patient preference may override protocol | Support flexible escalation; document cost/availability constraints; allow protocol deviation with justification |
| **DIAGNOSTIC IMAGING & TESTING** | | | | | |
| Test Requisition | Clinician specifies test type and clinical indication | Ensures appropriate testing; prevents unnecessary tests | Reduces waste; improves efficiency | Clinician may not know which test to order; limited access to advanced imaging | Provide test selection guidance; support simplified ordering; allow technician recommendation |
| Patient Preparation | Technician explains procedure and positions patient | Improves image quality; reduces patient anxiety | Enables cooperation; improves compliance | Technician may not be available; explanation may be minimal; patient anxiety not addressed | Support self-service instructions; provide patient education materials; allow abbreviated preparation |
| Image Acquisition | Standardized protocol with quality control | Ensures reproducible, high-quality images | Enables comparison; improves diagnostic accuracy | Equipment may not support standardized protocols; technician may lack training; quality control absent | Support flexible protocols; allow manual quality assessment; document protocol deviations |
| Preliminary Review | Technician performs quality check; flags abnormalities | Prevents repeat imaging; enables urgent communication | Improves efficiency; ensures timely intervention | Technician may lack training; quality check may be skipped; abnormalities may be missed | Make quality check optional; support physician-only review; provide abnormality flagging guidance |
| Clinical Interpretation | Ophthalmologist interprets images; generates report | Expert assessment; clinical context provided | Ensures diagnostic accuracy; supports clinical decision-making | Interpretation may be delayed; report may be incomplete; clinician may lack expertise in modality | Support delayed interpretation; allow preliminary technician assessment; provide interpretation templates |
| Outputs | Quantitative measurements (OCT thickness, VF indices, biometry) | Objective data for monitoring | Enables trend analysis; supports treatment decisions | Measurements may not be available; equipment may not provide automated measurements; manual measurement may be inaccurate | Support manual measurements; allow qualitative assessment; provide measurement templates |
| **LASER PROCEDURE** | | | | | |
| Pre-laser Assessment | Consultant ophthalmologist confirms indication and plans procedure | Specialist-level decision-making | Ensures appropriate selection; prevents unnecessary procedures | Consultant may not be available; resident may make decision; procedure may be performed without specialist input | Support resident-led procedures with consultant review; allow deferred specialist assessment; document decision-maker |
| Patient Preparation | Informed consent obtained; topical anesthesia instilled; contact lens applied | Patient comfort; procedure safety | Enables cooperation; reduces pain; improves visualization | Consent may be verbal/informal; anesthesia may not be available; contact lens may not be available | Support simplified consent; allow procedure without anesthesia (if tolerated); provide alternative visualization methods |
| Laser Delivery | Standardized laser parameters (wavelength, power, duration, spot size) | Reproducible treatment; predictable outcomes | Enables protocol-based management; improves safety | Laser parameters may vary; operator may lack training; standardization absent | Support flexible parameters; allow operator-determined parameters; provide parameter guidance |
| Laser Delivery | Ophthalmologist monitors tissue response and adjusts parameters | Real-time optimization; complication prevention | Improves efficacy; reduces adverse effects | Monitoring may be minimal; adjustment may not occur; complications may not be recognized | Support simplified monitoring; allow fixed-parameter protocols; provide complication recognition guidance |
| Post-operative Care | Post-operative medications instilled; follow-up imaging scheduled | Ensures optimal healing; enables monitoring | Reduces complications; supports treatment efficacy | Post-operative medications may not be available; follow-up imaging may be delayed or unavailable | Support simplified post-operative care; allow home-based follow-up; provide medication alternatives |
| Outputs | PhilHealth RVS procedure code assigned | Enables reimbursement | Mandatory for PhilHealth claims | RVS code may not be known; mapping from procedure description not standardized; coding errors common | Provide RVS code reference; automate procedure-to-RVS mapping; implement coding validation |
| **MINOR SURGICAL PROCEDURE (IN-OFFICE)** | | | | | |
| Pre-operative Preparation | Time-out performed; sterile field prepared; consent verified | Safety checklist; infection prevention | Reduces wrong-site surgery; prevents infections | Time-out may be skipped; sterile technique may be limited; consent may be informal | Support simplified time-out; provide sterile technique guidance; document consent method |
| Surgical Procedure | Standardized surgical steps; EyeDraw used to diagram procedure site | Reproducible technique; documentation | Enables training; supports communication | Technique may vary; EyeDraw may not be used; documentation may be minimal | Support flexible technique; make EyeDraw optional; provide procedure template |
| Specimen Handling | Specimen collected, labeled, and sent for pathology | Diagnostic confirmation; enables treatment | Improves diagnostic accuracy; supports prognosis | Pathology services may not be available; specimen handling may be inadequate; results may be delayed | Support clinical diagnosis without pathology; provide specimen handling guidance; allow delayed pathology |
| Post-operative Assessment | Immediate outcome evaluated; complications assessed | Early complication detection | Enables prompt intervention; improves outcomes | Assessment may be minimal; complications may not be recognized; follow-up may be delayed | Support simplified assessment; provide complication recognition guidance; schedule early follow-up |
| Outputs | PhilHealth RVS procedure code assigned | Enables reimbursement | Mandatory for PhilHealth claims | RVS code may not be known; mapping not standardized; coding errors common | Provide RVS code reference; automate procedure-to-RVS mapping; implement coding validation |
| **MAJOR SURGICAL PROCEDURE (OPERATING THEATRE)** | | | | | |
| Pre-operative Workup | Standardized pre-operative assessment (labs, imaging, anesthesia clearance) | Safety verification; risk stratification | Prevents intraoperative complications; improves outcomes | Pre-operative workup may be abbreviated; labs may not be available; anesthesia clearance may be informal | Support abbreviated workup; allow clinical judgment for testing; provide risk assessment guidance |
| Pre-operative Planning | Biometry reviewed; IOL power calculated; implant selected | Optimized refractive outcome | Improves patient satisfaction; reduces need for glasses | Biometry may not be available; IOL selection may be limited; patient preference may override calculation | Support manual IOL selection; provide calculation alternatives; document patient preference |
| Operating Theatre | Standardized equipment; trained OR staff; anesthesia support | Safe surgical environment | Enables complex procedures; reduces complications | Equipment may be limited; OR staff may lack training; anesthesia support may be minimal | Support simplified procedures; provide staff training; allow local anesthesia alternatives |
| Surgical Technique | Standardized surgical steps; intraoperative imaging (if needed) | Reproducible technique; complication prevention | Improves outcomes; enables training | Technique may vary; intraoperative imaging may not be available; surgeon experience may vary | Support flexible technique; allow technique variation documentation; provide surgical guidance |
| Implant Documentation | Implant type, power, position documented in detail | Enables follow-up; supports refractive planning | Improves long-term outcomes; supports retreatment decisions | Implant documentation may be minimal; implant details may not be recorded; follow-up may be limited | Provide implant documentation template; require implant details for billing; support simplified documentation |
| Intraoperative Complications | Complications documented; management recorded | Enables outcome tracking; supports liability defense | Improves safety culture; enables quality improvement | Complications may not be documented; management may not be recorded; complications may be minimized | Provide complication documentation template; require documentation for all complications; support incident reporting |
| Post-operative Imaging | Post-operative imaging (OCT, photography) obtained | Documents surgical result; enables monitoring | Supports quality assessment; enables early complication detection | Post-operative imaging may be delayed or unavailable; imaging may not be performed | Support delayed imaging; allow clinical assessment without imaging; provide imaging templates |
| Outputs | Detailed operation notes with surgical technique | Enables training; supports communication | Improves documentation quality; enables peer review | Operation notes may be brief; technique may not be detailed; notes may be handwritten | Provide operation note template; support dictation; allow abbreviated notes with key details |
| Outputs | PhilHealth RVS procedure code assigned | Enables reimbursement | Mandatory for PhilHealth claims | RVS code may not be known; mapping not standardized; coding errors common | Provide RVS code reference; automate procedure-to-RVS mapping; implement coding validation |
| **EMERGENCY EYE PRESENTATION** | | | | | |
| Rapid Triage | Nurse performs rapid assessment; severity determined | Appropriate resource allocation | Prevents delays in urgent cases; improves outcomes | Triage may not be performed; severity assessment may be inaccurate; delays may occur | Support simplified triage; provide severity assessment guidance; allow physician-led triage |
| Emergency Examination | Rapid ophthalmologic assessment; sight-threatening pathology identified | Urgent intervention enabled | Prevents vision loss; improves outcomes | Examination may be delayed; pathology may be missed; specialist may not be available | Support non-specialist assessment; provide diagnostic guidance; allow telemedicine consultation |
| Initial Management | Stabilizing medications/procedures performed; disposition determined | Prevents further deterioration | Improves outcomes; enables appropriate care level | Management may be limited by availability; disposition may be unclear; follow-up may be uncertain | Support simplified management; provide disposition guidance; schedule urgent follow-up |
| Disposition | Admission, OR, or discharge determined based on severity | Appropriate care level | Improves outcomes; optimizes resource use | Admission may be limited by bed availability; OR may not be available; discharge may be premature | Support flexible disposition; allow observation in clinic; provide discharge criteria |
| Follow-up | Close follow-up scheduled; contact information provided | Ensures continuity of care | Improves outcomes; prevents complications | Follow-up may not be scheduled; patient may not return; contact information may be incomplete | Support patient reminder system; provide follow-up instructions; allow self-referral for urgent symptoms |
| **INPATIENT ADMISSION & MANAGEMENT** | | | | | |
| Admission | Baseline examination performed; baseline vision and IOP documented | Establishes starting point for monitoring | Enables outcome assessment; supports quality measurement | Baseline may not be documented; vision/IOP may not be measured; documentation may be incomplete | Provide admission assessment template; require baseline measurements; support simplified documentation |
| Daily Rounds | Consultant performs daily examination; clinical progress assessed | Specialist-level monitoring | Ensures appropriate management; enables early complication detection | Consultant may not be available daily; rounds may be performed by resident; frequency may vary | Support resident-led rounds with consultant review; allow less frequent rounds; document round frequency |
| Nursing Care | Medications administered on schedule; vital signs monitored; eye care maintained | Ensures optimal healing; prevents complications | Improves outcomes; reduces infections | Medication administration may be irregular; vital signs may not be monitored; eye care may be minimal | Support simplified medication schedule; provide vital sign monitoring guidance; provide eye care instructions |
| Discharge Planning | Readiness for discharge assessed; discharge medications provided; follow-up arranged | Ensures safe transition to outpatient care | Improves outcomes; prevents readmission | Discharge planning may be minimal; medications may not be provided; follow-up may not be arranged | Provide discharge planning template; support medication provision; schedule follow-up appointment |
| Outputs | Discharge summary with clear follow-up plan | Enables continuity of care | Improves outcomes; supports referral communication | Discharge summary may be brief; follow-up plan may be unclear; communication may not occur | Provide discharge summary template; require clear follow-up plan; support referral communication |
| **PATIENT REGISTRATION & DEMOGRAPHICS** | | | | | |
| Verification | Check if patient is in system; retrieve existing record if present | Prevents duplicate records; enables continuity of care | Improves data quality; reduces errors | System may not be available; patient may not be in system; duplicate records may exist | Support offline registration; allow duplicate record merging; provide manual verification |
| Data Entry | Patient demographics entered into system; PhilHealth eligibility verified | Enables billing and follow-up | Ensures accurate patient identification; enables reimbursement | Data entry may be manual; PhilHealth verification may be delayed; eligibility may be uncertain | Support manual data entry; allow offline PhilHealth verification; provide eligibility status options |
| Documentation | Patient ID card printed; registration form filed; appointment scheduled | Patient identified; record created; appointment confirmed | Enables future visits; ensures continuity of care | Patient ID may not be printed; registration form may not be filed; appointment may not be scheduled | Support digital patient ID; allow paper registration; provide appointment confirmation method |
| **APPOINTMENT SCHEDULING** | | | | | |
| Triage | Clinical urgency determined; specialist assigned; appointment duration estimated | Appropriate scheduling; specialist matching | Improves efficiency; ensures appropriate care | Urgency determination may be informal; specialist assignment may be unclear; duration may vary | Support simplified urgency assessment; allow flexible specialist assignment; provide duration guidance |
| Scheduling | Specialist availability checked; time slot offered; appointment confirmed | Efficient use of specialist time | Reduces wait times; improves patient satisfaction | Availability may not be known; limited slots may be available; confirmation may be informal | Support flexible scheduling; allow walk-in patients; provide appointment confirmation method |
| Reminder | Appointment reminder sent to patient (SMS, phone) | Reduces no-show rate | Improves efficiency; improves patient satisfaction | Reminders may not be sent; patient may not receive reminder; no-show rate may be high | Support optional reminders; allow phone/SMS reminders; provide alternative confirmation methods |
| **REFERRAL MANAGEMENT** | | | | | |
| Referral Generation | Referring clinician documents indication; attaches imaging/reports; specifies urgency | Enables appropriate routing; provides clinical context | Improves efficiency; ensures appropriate care | Referral may be verbal; documentation may be minimal; imaging may not be attached | Support verbal referral documentation; allow simplified referral form; provide imaging attachment method |
| Referral Transmission | Referral sent to receiving facility via secure channel (fax, email, portal) | Ensures timely receipt; maintains confidentiality | Improves efficiency; ensures continuity of care | Referral may be hand-carried; transmission may be delayed; confidentiality may not be ensured | Support hand-carried referral; allow delayed transmission; provide referral tracking |
| Referral Reception | Receiving facility receives referral; verifies patient information; schedules appointment | Ensures appropriate care; enables continuity | Improves efficiency; ensures patient engagement | Reception may be delayed; patient information may not be verified; appointment may not be scheduled | Support manual reception; allow patient self-scheduling; provide appointment confirmation |
| Feedback | Feedback communication sent to referring clinician | Enables continuity of care; supports quality improvement | Improves outcomes; enables learning | Feedback may not be sent; communication may be delayed; feedback may be minimal | Support optional feedback; allow delayed communication; provide feedback template |
| **PHILHEALTH CLAIM PREPARATION & SUBMISSION** | | | | | |
| Data Extraction | Encounter data extracted from EMR; billable diagnosis/procedures identified | Enables accurate billing | Ensures appropriate reimbursement; improves revenue | EMR may not have encounter data; billable items may not be identified; extraction may be manual | Support manual data extraction; provide billable item checklist; allow simplified extraction |
| Coding | ICD-10 diagnosis codes assigned; RVS procedure codes assigned; accuracy verified | Enables reimbursement; ensures compliance | Mandatory for PhilHealth claims; improves revenue | Coding may be inaccurate; codes may not be known; verification may not occur | Provide coding reference; automate SNOMED-to-ICD-10 mapping; implement coding validation |
| Claim Assembly | PhilHealth eClaims form populated; supporting documentation attached; completeness verified | Enables submission; ensures compliance | Mandatory for PhilHealth reimbursement | Form may not be completed; documentation may be missing; verification may not occur | Provide eClaims template; require supporting documentation; implement completeness check |
| Submission | Claim submitted via PhilHealth eClaims system; submission date recorded; claim ID obtained | Initiates reimbursement process | Mandatory for PhilHealth reimbursement; enables tracking | Submission may be delayed; claim ID may not be recorded; submission may fail | Support offline claim preparation; allow batch submission; provide submission tracking |
| Follow-up | Claim status tracked; denials addressed; reimbursement reconciled | Ensures payment receipt; enables dispute resolution | Improves cash flow; enables quality improvement | Tracking may not occur; denials may not be addressed; reconciliation may be incomplete | Provide claim tracking template; support denial management; provide reconciliation guidance |
| **PRESCRIPTION & MEDICATION MANAGEMENT** | | | | | |
| Prescription Generation | Medication selected from formulary; dosage/frequency specified; indication documented | Enables safe dispensing; ensures appropriate use | Improves patient safety; enables monitoring | Formulary may not be available; dosage may not be specified; indication may not be documented | Support manual medication entry; allow simplified dosage specification; provide indication guidance |
| Prescription Review | Pharmacist verifies prescription; checks for interactions/allergies; confirms dosage | Ensures patient safety; prevents adverse events | Improves patient safety; reduces errors | Review may not occur; interactions may not be checked; dosage may not be confirmed | Support simplified review; provide interaction checking; allow abbreviated review |
| Dispensing | Medication prepared; label applied; patient education provided | Ensures correct medication; enables safe use | Improves patient safety; improves adherence | Medication may not be prepared correctly; label may be incomplete; education may not be provided | Support manual dispensing; provide labeling template; provide patient education materials |
| Patient Education | Medication purpose explained; administration technique demonstrated; side effects discussed | Improves adherence; enables early complication detection | Improves patient safety; improves outcomes | Education may not occur; demonstration may not occur; side effects may not be discussed | Support written education materials; provide administration guidance; provide side effect information |
| **CORRESPONDENCE & COMMUNICATION** | | | | | |
| Letter Generation | Clinical summary dictated/typed; findings included; management plan specified | Enables communication; documents decision-making | Improves continuity of care; supports referral | Letter may not be generated; summary may be incomplete; plan may not be specified | Support simplified letter template; allow abbreviated summary; provide plan guidance |
| Review & Formatting | Letter formatted per institutional standards; proofread; prepared for signature | Ensures professional appearance; prevents errors | Improves communication quality; reduces errors | Formatting may not occur; proofreading may not occur; signature may be delayed | Support simplified formatting; allow abbreviated proofreading; provide signature process |
| Signature & Dispatch | Letter signed; sent to referring clinician (fax, email, post); copy provided to patient | Ensures timely communication; maintains continuity | Improves outcomes; supports referral | Signature may be delayed; dispatch may not occur; copy may not be provided | Support electronic signature; allow delayed dispatch; provide patient copy option |

---

## SUMMARY OF KEY EMBEDDED ASSUMPTIONS

### Infrastructure Assumptions (Most Critical)
1. **Reliable electricity and continuous internet connectivity** - Assumed throughout workflows; critical for eClaims submission, imaging storage, data backup
2. **Dedicated IT support and centralized server management** - Assumed for EMR functionality, data security, system maintenance
3. **Standardized diagnostic equipment** - Assumed for OCT, visual fields, biometry; enables protocol-based workflows
4. **Centralized data management system** - Assumed for patient records, imaging storage, appointment scheduling
5. **Electronic referral system** - Assumed for inter-facility communication; enables structured referral pathways

### Staffing Assumptions (Critical)
1. **Specialist availability during clinic hours** - Assumed for all clinical workflows; enables specialist-led assessment
2. **Trained ophthalmic technicians** - Assumed for diagnostic testing, imaging, pre-exam procedures
3. **Specialized ophthalmic nurses** - Assumed for patient preparation, procedure assistance, patient education
4. **Dedicated administrative staff** - Assumed for scheduling, billing, correspondence
5. **Structured training pathways** - Assumed for residents; enables supervised procedures

### Operational Assumptions (Critical)
1. **Scheduled appointments with predictable patient flow** - Assumed for clinic planning; enables specialist scheduling
2. **Parallel diagnostic processing in single visit** - Assumed for efficiency; requires multiple staff and equipment
3. **Structured referral pathways with gatekeeping** - Assumed for appropriate resource allocation
4. **Automated billing and coding** - Assumed for PhilHealth claims; requires standardized coding
5. **Reliable follow-up with high compliance** - Assumed for chronic disease management; enables monitoring

### Regulatory Assumptions (Moderate)
1. **Standardized clinical guidelines and protocols** - Assumed for evidence-based practice
2. **Strict informed consent requirements** - Assumed for legal protection; requires detailed documentation
3. **Comprehensive documentation standards** - Assumed for medico-legal protection
4. **Accreditation and inspection requirements** - Assumed for quality assurance
5. **Liability insurance and malpractice protection** - Assumed for risk management

---

## RISKS IN PHILIPPINE CONTEXT

### High-Risk Assumptions (Likely to Fail)
- **Reliable internet connectivity**: Intermittent connectivity will disrupt eClaims submission, imaging storage, data sync
- **Specialist availability**: Consultant may not be present daily; residents may conduct initial exams without supervision
- **Parallel diagnostic processing**: Sequential processing more realistic; patients may not complete workup in single visit
- **Automated billing**: Manual claim preparation more realistic; PhilHealth rejections common
- **Reliable follow-up**: Poor follow-up rates; patients lost to follow-up common

### Medium-Risk Assumptions (May Fail in Some Contexts)
- **Trained technicians**: Limited availability; multi-tasking across departments; may lack specialized training
- **Standardized equipment**: Equipment may be older, broken, or unavailable; different models in use
- **Structured referral pathways**: Informal referral pathways more common; documentation variable
- **Scheduled appointments**: Walk-in patients common; high no-show rates; unpredictable patient flow
- **Comprehensive documentation**: Documentation often minimal; time constraints limit detail

### Lower-Risk Assumptions (Likely to Work with Adaptation)
- **Informed consent**: Simplified consent forms can work; verbal consent acceptable in some contexts
- **Clinical guidelines**: Guidelines exist but implementation variable; flexibility needed
- **Patient education**: Simplified materials in local language can be effective
- **Medication management**: Simplified medication protocols can work; alternatives needed for unavailable drugs
- **Correspondence**: Paper-based correspondence can supplement electronic communication

---

## ADAPTATION PRIORITIES

### Priority 1: Infrastructure & Connectivity
- **Offline-first architecture**: All workflows must function without internet
- **Data synchronization**: Support asynchronous sync when connectivity available
- **Lightweight design**: Minimize bandwidth requirements; support low-speed connections
- **Local storage**: Support imaging and data storage on department server

### Priority 2: Staffing & Workflow Flexibility
- **Flexible role assignment**: Support workflows with limited staff; allow role substitution
- **Resident-led workflows**: Support resident-led examination with consultant review
- **Sequential processing**: Allow diagnostic testing across multiple visits
- **Simplified procedures**: Support abbreviated workflows for resource-constrained settings

### Priority 3: PhilHealth Integration
- **Automated coding**: Automate SNOMED-to-ICD-10 and procedure-to-RVS mapping
- **Offline claim preparation**: Support claim assembly without internet
- **Batch submission**: Allow batch eClaims submission when connectivity available
- **Coding validation**: Implement validation to catch coding errors before submission

### Priority 4: Operational Resilience
- **Manual backup processes**: Support paper-based backup for critical workflows
- **Equipment flexibility**: Allow workflow continuation with limited/unavailable equipment
- **Staff absence handling**: Support workflows with reduced staffing
- **Power outage resilience**: Support operation during power outages (with backup power)

### Priority 5: User Experience
- **Simplified interfaces**: Design for users with limited IT literacy
- **Offline documentation**: Support offline note-taking and documentation
- **Mobile access**: Support access via personal devices (residents, consultants)
- **Local language support**: Provide Filipino/Tagalog interface and documentation

---

## CONCLUSION

The Clinical Workflow Inventory contains numerous NHS-specific assumptions embedded in its design. The most critical assumptions relate to **infrastructure reliability** (internet, electricity, server), **staffing availability** (specialists, technicians, nurses), and **operational predictability** (scheduled appointments, parallel processing, reliable follow-up).

These assumptions are **high-risk in the Philippine context** and require significant adaptation. The adaptation strategy should prioritize **offline-first architecture**, **staffing flexibility**, **PhilHealth integration**, **operational resilience**, and **simplified user experience** to ensure the system functions effectively in resource-constrained settings with intermittent connectivity.

The next iteration should explicitly challenge each assumption and design workflows that function effectively even when these assumptions fail.
