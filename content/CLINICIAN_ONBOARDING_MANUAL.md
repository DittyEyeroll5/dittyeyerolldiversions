# OpenEyes Clinician Onboarding Manual
## A Practical Guide for Philippine Ophthalmology Staff

**Version**: 1.0  
**Audience**: Ophthalmologists, residents, nurses, technicians, administrative staff  
**Tone**: Practical, reassuring, low jargon  
**Context**: Department-owned server, mesh VPN, intermittent internet

---

## INTRODUCTION: WHAT YOU NEED TO KNOW

Welcome to OpenEyes—a system designed to help you care for patients while managing paperwork efficiently. This manual explains how the system works in real-world terms, not technical jargon.

### The Big Picture

OpenEyes is a **patient record system** that:
- Stores patient information in one place (no more lost files)
- Helps you document what you find during examinations
- Tracks patient progress over time
- Prepares insurance claims automatically
- Works even when the internet is down

### Key Principle: Paper and Digital Work Together

You can use OpenEyes on a computer, but if the system is down or internet is unavailable, you can still:
- Write notes on paper
- Record measurements manually
- See patients normally
- Enter everything into the system later when it's back online

**Nothing stops you from caring for patients.**

### What This Manual Covers

- How the system works (conceptual overview)
- A typical day using the system (day-in-the-life examples)
- Your specific role and what you do (role-based quick starts)
- Common situations and how to handle them (scenarios)
- What to do when something goes wrong (troubleshooting)

---

## PART 1: CONCEPTUAL OVERVIEW

### How OpenEyes Works

Think of OpenEyes as a **digital filing system** that follows your patient through their visit:

```
Patient Arrives
    ↓
Registration (Name, contact, insurance)
    ↓
Pre-exam (Nurse takes measurements: vision, eye pressure)
    ↓
Examination (Doctor examines patient)
    ↓
Diagnosis (Doctor decides what's wrong)
    ↓
Treatment Plan (Doctor explains what to do next)
    ↓
Billing (Staff prepares insurance paperwork)
    ↓
Follow-up (Patient scheduled for next visit)
```

At each step, information is recorded in the system. The system helps ensure nothing is missed.

### The System's Three Main Jobs

**1. Patient Care**
- Keeps all patient information in one place
- Shows you what happened at previous visits
- Helps you make better decisions about treatment

**2. Documentation**
- Records what you found during examination
- Creates a legal record of care
- Supports quality improvement

**3. Insurance**
- Prepares PhilHealth claims automatically
- Reduces paperwork and errors
- Helps the department get paid

### Offline-First: The System Works Without Internet

The system is designed for **intermittent internet**. Here's how:

**When Online**:
- System syncs data with the server
- PhilHealth claims are submitted
- Software updates are downloaded

**When Offline**:
- You can still see patients
- You can still enter information
- Everything is saved locally
- When internet returns, data syncs automatically

**You never have to stop seeing patients because the internet is down.**

### The Server: Where Your Data Lives

Your department owns a server (a computer that stores all patient data). Think of it as a **secure filing cabinet** that:
- Stores all patient records
- Backs up data daily
- Is accessible only to authorized staff
- Is protected by encryption

You access this server through a **secure tunnel** (mesh VPN) on your personal computer.

### Data Security: Your Patient Information is Protected

Patient information is protected by:
- **Encryption**: Data is scrambled so only authorized people can read it
- **Access control**: Only staff with permission can see patient records
- **Audit trail**: The system tracks who accessed what information and when
- **Backups**: Data is backed up daily in case of emergency

---

## PART 2: DAY-IN-THE-LIFE EXAMPLES

### Example 1: Dr. Maria's Day (Consultant Ophthalmologist)

**8:00 AM - Arrive at Clinic**

Maria opens her laptop and connects to the clinic's secure network (mesh VPN). She opens OpenEyes and sees her schedule for the day: 12 new patients and 8 follow-ups.

**8:15 AM - First Patient (New)**

A 65-year-old man presents with blurred vision. Maria:
1. Pulls up his registration (already done by receptionist)
2. Reviews his chief complaint: "Difficulty seeing far away"
3. Checks pre-exam measurements from the nurse: VA 6/18, IOP 16 mmHg
4. Performs her examination (slit lamp, dilated exam)
5. Documents her findings in the system (anterior segment clear, posterior segment shows early cataract)
6. Enters diagnosis: "Age-related cataract"
7. The system automatically suggests the correct insurance code
8. Explains options to patient: glasses, surgery, or watchful waiting
9. Patient chooses surgery; Maria schedules for next week

**Time in system**: 5 minutes (mostly just clicking and typing what she already knows)

**9:00 AM - Second Patient (Follow-up)**

A 52-year-old woman returns for glaucoma follow-up. Maria:
1. Pulls up her previous visit (3 months ago)
2. Compares today's eye pressure (14 mmHg) to last visit (16 mmHg)
3. Reviews her medication compliance (patient says she's taking drops daily)
4. Examines patient; finds stable appearance
5. Decides to continue current treatment
6. Schedules next visit in 3 months

**Time in system**: 3 minutes (mostly just reviewing and confirming)

**10:00 AM - Internet Goes Down**

The internet connection fails. Maria continues seeing patients normally. She:
1. Still sees patients using the system (all data is stored locally)
2. Still enters examination findings
3. Still prescribes medications
4. Still schedules follow-ups

Nothing changes in her workflow. The system continues to work.

**1:00 PM - Internet Comes Back**

When internet returns, the system automatically syncs all the morning's data to the server. Maria doesn't have to do anything—it happens in the background.

**2:00 PM - Laser Procedure**

A patient with diabetic retinopathy needs laser treatment. Maria:
1. Reviews the patient's imaging (OCT shows macular edema)
2. Confirms the indication and plans laser parameters
3. Nurse prepares patient (anesthesia, positioning)
4. Maria performs laser treatment
5. Documents the procedure (number of burns, location, patient response)
6. Schedules follow-up imaging in 1 week

**Time in system**: 10 minutes (mostly documentation after procedure)

**4:00 PM - Billing Review**

The billing officer shows Maria a claim that was denied. The insurance code was incorrect. Maria:
1. Reviews the patient's record
2. Confirms the correct diagnosis
3. Billing officer corrects the code
4. Claim is resubmitted

**Time in system**: 2 minutes (just confirming information)

**5:00 PM - End of Day**

Maria reviews her schedule for tomorrow and notes any special cases. She closes her laptop. All her day's work is saved and synced.

### Example 2: Nurse Rosa's Day

**8:00 AM - Arrive at Clinic**

Rosa logs into the system and checks the patient schedule. She sees 20 patients today.

**8:15 AM - First Patient Pre-exam**

A new patient arrives. Rosa:
1. Verifies patient information (name, date of birth, insurance)
2. Takes vital signs (blood pressure, pulse, temperature)
3. Measures visual acuity (both eyes, with and without glasses)
4. Measures eye pressure
5. Takes a photo of the front of the eye (if camera available)
6. Enters all measurements into the system

**Time**: 10 minutes

**8:30 AM - Patient Ready for Doctor**

Rosa alerts the doctor that the patient is ready. The doctor can see all the pre-exam information on the screen.

**9:00 AM - Laser Procedure Preparation**

Rosa prepares a patient for laser treatment:
1. Verifies patient identity and procedure type
2. Explains the procedure in simple terms
3. Obtains verbal consent (documented in system)
4. Instills anesthetic drops
5. Positions patient at laser equipment

**Time**: 5 minutes

**9:15 AM - Procedure Support**

Rosa assists the doctor during the procedure:
1. Monitors patient comfort
2. Alerts doctor to any patient movement
3. Provides additional drops as needed

**Time**: 20 minutes

**9:40 AM - Post-operative Care**

Rosa provides post-operative instructions:
1. Explains what to expect (mild discomfort, redness)
2. Provides written instructions (if available)
3. Schedules follow-up appointment
4. Documents in system

**Time**: 5 minutes

**Throughout the Day**

Rosa continues pre-exams, procedure support, and patient education. She also:
- Answers patient questions
- Helps patients with paperwork
- Assists with any urgent issues

**Key Point**: Rosa's work in the system is straightforward—mostly entering measurements and scheduling. The doctor reviews and interprets.

### Example 3: Billing Officer Juan's Day

**8:00 AM - Arrive at Clinic**

Juan logs into the system and checks for completed encounters from yesterday that need billing.

**8:15 AM - Review Yesterday's Encounters**

Juan reviews 15 encounters from yesterday:
1. For each patient, he checks:
   - Was the diagnosis coded? (Is there an ICD-10 code?)
   - Was the procedure coded? (Is there an RVS code if a procedure was done?)
   - Are the codes correct?
2. For any missing codes, he contacts the doctor to clarify
3. For any incorrect codes, he corrects them using the lookup table

**Time**: 30 minutes

**9:00 AM - Prepare PhilHealth Claims**

For patients with PhilHealth insurance, Juan:
1. Extracts the patient information (name, ID, insurance number)
2. Extracts the diagnosis code and procedure codes
3. Extracts the charges
4. Populates the PhilHealth claim form
5. Verifies everything is correct
6. Submits the claim (if internet is available)

**Time**: 1 minute per claim (mostly automatic)

**10:00 AM - Track Claim Status**

Juan checks the status of claims submitted last week:
1. Logs into PhilHealth portal
2. Reviews claim statuses (approved, denied, pending)
3. For any denied claims, reviews the reason
4. Prepares corrected claim for resubmission

**Time**: 30 minutes

**11:00 AM - Patient Billing**

A patient asks about their bill. Juan:
1. Pulls up the patient's encounter
2. Shows the charges (consultation, procedures, imaging)
3. Shows what insurance covered
4. Shows what patient owes
5. Collects payment (cash, or schedules payment plan)

**Time**: 5 minutes

**Throughout the Day**

Juan continues reviewing encounters, preparing claims, tracking status, and handling patient billing questions.

**Key Point**: Most of Juan's work is straightforward—reviewing information and submitting forms. The system helps by suggesting correct codes and organizing information.

---

## PART 3: ROLE-BASED QUICK STARTS

### Consultant Ophthalmologist

**Your Main Tasks in the System**:
1. Review patient information
2. Document examination findings
3. Enter diagnosis and treatment plan
4. Assign insurance codes (system suggests them)
5. Approve procedures and treatment plans
6. Review resident examinations

**Quick Start**:

```
1. Open OpenEyes
2. Click "My Schedule" to see today's patients
3. Click on a patient to open their record
4. Review pre-exam information (from nurse)
5. Perform examination
6. Click "Document Findings" and enter what you found
7. Click "Enter Diagnosis" and select from list
8. System suggests insurance code—confirm or change
9. Click "Treatment Plan" and document next steps
10. Click "Save and Close"
```

**Time per patient**: 5-10 minutes (mostly just clicking and typing what you already know)

**Common Tasks**:
- Review resident examinations: Click "Pending Reviews" to see exams waiting for your approval
- Approve procedures: Click "Pending Procedures" to review and approve planned procedures
- Check imaging: Click "Imaging" to review OCT, visual fields, photography

**If System is Down**:
- Write notes on paper
- Document findings in paper form
- Enter into system when it's back online
- Patients are still seen normally

### Resident Ophthalmologist

**Your Main Tasks in the System**:
1. Perform initial examination
2. Document findings
3. Enter preliminary diagnosis
4. Request imaging or procedures
5. Receive feedback from consultant

**Quick Start**:

```
1. Open OpenEyes
2. Click "My Patients" to see patients assigned to you
3. Click on a patient to open their record
4. Review pre-exam information
5. Perform examination
6. Click "Document Findings" and enter what you found
7. Click "Preliminary Diagnosis" and select from list
8. Click "Request Review" to notify consultant
9. Consultant reviews and provides feedback
10. Click "Save and Close"
```

**Time per patient**: 10-15 minutes

**Important**: Your examinations are reviewed by the consultant. This is normal and helps you learn.

**Common Tasks**:
- Request imaging: Click "Order Imaging" to request OCT, visual fields, etc.
- Request procedures: Click "Schedule Procedure" to request laser or surgery
- Receive feedback: Check "My Feedback" to see consultant comments

**If System is Down**:
- Write notes on paper
- Document findings in paper form
- Enter into system when it's back online

### Ophthalmic Nurse

**Your Main Tasks in the System**:
1. Take pre-exam measurements (vision, eye pressure)
2. Prepare patients for procedures
3. Assist during procedures
4. Provide post-operative instructions
5. Schedule follow-up appointments

**Quick Start**:

```
1. Open OpenEyes
2. Click "Today's Schedule" to see all patients
3. Click on a patient to open their record
4. Click "Pre-exam" to start measurements
5. Enter visual acuity (both eyes)
6. Enter eye pressure (both eyes)
7. Enter vital signs (blood pressure, pulse, temperature)
8. Click "Complete Pre-exam"
9. Alert doctor that patient is ready
```

**Time per patient**: 10 minutes

**Common Tasks**:
- Schedule follow-up: Click "Schedule Appointment" to book next visit
- Provide instructions: Click "Patient Education" to print or display instructions
- Record procedure assistance: Click "Procedure Log" to document your role

**If System is Down**:
- Record measurements on paper
- Enter into system when it's back online

### Ophthalmic Technician

**Your Main Tasks in the System**:
1. Operate diagnostic equipment (OCT, visual fields, biometry)
2. Acquire and store images
3. Record test parameters
4. Assist with laser procedures

**Quick Start**:

```
1. Open OpenEyes
2. Click "Imaging Queue" to see ordered tests
3. Click on a test to open the order
4. Review clinical indication
5. Prepare patient and equipment
6. Acquire images/measurements
7. Click "Upload Images" to save to system
8. Click "Complete Test"
```

**Time per test**: 15-30 minutes (depending on test type)

**Common Tasks**:
- Laser assistance: Click "Laser Queue" to see scheduled procedures
- Equipment maintenance: Log equipment status and maintenance
- Quality check: Review image quality and flag poor-quality images

**If System is Down**:
- Acquire images and save to external drive
- Upload to system when it's back online

### Receptionist/Administrative Staff

**Your Main Tasks in the System**:
1. Register new patients
2. Schedule appointments
3. Verify insurance information
4. Manage appointment calendar
5. Print appointment cards and referral forms

**Quick Start**:

```
1. Open OpenEyes
2. Click "New Patient" to register
3. Enter patient information (name, DOB, address, contact, insurance)
4. Click "Save Patient"
5. Click "Schedule Appointment" to book visit
6. Select date and time
7. Click "Confirm Appointment"
8. Click "Print Appointment Card"
```

**Time per patient**: 5 minutes

**Common Tasks**:
- Check appointment status: Click "Today's Schedule" to see who's arriving
- Verify insurance: Click "Insurance Verification" to confirm coverage
- Handle cancellations: Click "Cancel Appointment" to free up slot
- Print referral: Click "Print Referral" to generate referral form

**If System is Down**:
- Register patients on paper
- Write appointments in paper calendar
- Enter into system when it's back online

### Billing Officer

**Your Main Tasks in the System**:
1. Review completed encounters
2. Verify diagnosis and procedure codes
3. Prepare PhilHealth claims
4. Track claim status
5. Handle patient billing

**Quick Start**:

```
1. Open OpenEyes
2. Click "Pending Billing" to see encounters needing codes
3. For each encounter:
   - Review diagnosis
   - Confirm ICD-10 code (system suggests)
   - Confirm RVS code if procedure was done
   - Click "Verify Codes"
4. Click "Prepare Claim" to create PhilHealth claim
5. Click "Submit Claim" (if internet available)
6. Click "Track Status" to monitor claim
```

**Time per claim**: 1-2 minutes (mostly automatic)

**Common Tasks**:
- Handle denied claims: Click "Denied Claims" to review reasons and resubmit
- Patient billing: Click "Patient Charges" to show patient what they owe
- Insurance verification: Click "Verify Coverage" to confirm patient eligibility

**If System is Down**:
- Record billing information on paper
- Enter into system when it's back online

---

## PART 4: COMMON SCENARIOS AND HOW TO HANDLE THEM

### Scenario 1: Patient Arrives Without Appointment (Walk-in)

**What to do**:

1. **Receptionist**: Register patient normally (same as scheduled patient)
2. **Receptionist**: Click "Walk-in" instead of scheduled appointment
3. **Receptionist**: Add to end of queue
4. **Nurse**: Perform pre-exam when patient is ready
5. **Doctor**: See patient when available
6. **Continue normally**: Document, diagnose, plan, bill

**Key Point**: Walk-in patients are handled the same way as scheduled patients. The system just notes they walked in.

### Scenario 2: Patient Doesn't Know Their Insurance Information

**What to do**:

1. **Receptionist**: Register patient with available information (name, DOB, address, contact)
2. **Receptionist**: Leave insurance field blank
3. **Receptionist**: Click "Verify Later"
4. **Later**: Billing officer can verify insurance when patient provides information
5. **Update**: Billing officer updates patient record with insurance information

**Key Point**: Don't delay seeing the patient. Insurance can be verified later.

### Scenario 3: Doctor Wants to Change Diagnosis After Seeing Patient

**What to do**:

1. **Doctor**: Click "Edit Diagnosis"
2. **Doctor**: Select new diagnosis from list
3. **System**: Suggests new insurance code
4. **Doctor**: Confirm or change code
5. **Click "Save"**

**Key Point**: Diagnoses can be changed anytime. The system updates the insurance code automatically.

### Scenario 4: Patient Needs Imaging (OCT, Visual Fields, etc.)

**What to do**:

1. **Doctor**: Click "Order Imaging"
2. **Doctor**: Select test type (OCT, visual fields, biometry, photography)
3. **Doctor**: Enter clinical indication
4. **Click "Submit Order"**
5. **Technician**: Receives order and performs test
6. **Technician**: Uploads images to system
7. **Doctor**: Reviews images and enters findings

**Key Point**: Imaging is ordered by the doctor and performed by the technician. Results are reviewed by the doctor.

### Scenario 5: Patient Needs Procedure (Laser, Surgery)

**What to do**:

1. **Doctor**: Click "Schedule Procedure"
2. **Doctor**: Select procedure type (laser, minor surgery, major surgery)
3. **Doctor**: Enter indication and planned approach
4. **Doctor**: Assign RVS code (system suggests)
5. **Click "Schedule"**
6. **Receptionist**: Schedules procedure date/time
7. **Nurse**: Prepares patient on procedure day
8. **Doctor**: Performs procedure
9. **Doctor**: Documents procedure details
10. **Billing**: Prepares claim with RVS code

**Key Point**: Procedures are planned in advance. The system helps organize everything.

### Scenario 6: Patient Can't Afford Treatment

**What to do**:

1. **Doctor**: Discusses cost with patient
2. **Doctor**: Explores alternatives (generic medications, less expensive procedures, watchful waiting)
3. **Billing Officer**: Explains PhilHealth coverage and out-of-pocket costs
4. **Billing Officer**: Offers payment plan if needed
5. **Document**: Note patient's financial constraints in record

**Key Point**: The system helps track affordability issues. This is important for follow-up and understanding why patients don't comply with treatment.

### Scenario 7: PhilHealth Claim is Denied

**What to do**:

1. **Billing Officer**: Receives denial notification
2. **Billing Officer**: Reviews denial reason (common reasons: invalid code, patient not eligible, duplicate claim)
3. **Billing Officer**: Corrects the issue (wrong code, verify eligibility, check for duplicate)
4. **Billing Officer**: Resubmits claim
5. **Track**: Monitor status of resubmitted claim

**Key Point**: Denials are common and usually fixable. The system tracks the reason so you know what to correct.

### Scenario 8: Internet is Down

**What to do**:

1. **Continue seeing patients normally** (system works offline)
2. **Continue entering information** (data is saved locally)
3. **Continue scheduling** (appointments are recorded locally)
4. **When internet returns**: System automatically syncs all data
5. **You don't have to do anything** (sync happens in background)

**Key Point**: Internet outages don't stop patient care. Everything syncs automatically when internet returns.

### Scenario 9: System is Completely Down (Server Problem)

**What to do**:

1. **Use paper forms** (pre-printed forms available at front desk)
2. **Continue seeing patients** (write notes on paper)
3. **Document everything** (patient info, measurements, findings, diagnosis, plan)
4. **When system is back**: Enter all paper records into system
5. **Alert IT administrator** (they will fix the problem)

**Key Point**: You always have a paper backup. Patient care never stops.

### Scenario 10: Patient Doesn't Show Up for Follow-up

**What to do**:

1. **Receptionist**: Notes patient as "no-show" in system
2. **Receptionist**: Marks appointment as cancelled
3. **Doctor**: Reviews no-show rate (helps identify compliance issues)
4. **Billing Officer**: May adjust claim if procedure wasn't done

**Key Point**: The system tracks no-shows. This helps identify patients who need extra support or reminders.

---

## PART 5: TROUBLESHOOTING

### Problem: I Can't Log In

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| Wrong password | Check caps lock; reset password with IT admin |
| Account not created | Contact IT admin to create account |
| VPN not connected | Check mesh VPN connection; restart if needed |
| System is down | Wait 15 minutes; try again; contact IT admin if still down |

**What to do**: Contact the IT administrator. They can reset your password or create your account.

### Problem: System is Very Slow

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| Internet is slow | Wait a few minutes; try again |
| Many users online | Try again during off-peak hours |
| Large file uploading | Close other programs; try again |
| Server is overloaded | Contact IT admin; may need to restart server |

**What to do**: Close unnecessary programs and try again. If still slow, contact IT admin.

### Problem: I Can't Find a Patient Record

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| Patient not registered | Register patient first (receptionist) |
| Misspelled name | Search by date of birth or phone number |
| Patient is in satellite clinic system | Contact satellite clinic; request data sync |
| System is down | Wait for system to come back online |

**What to do**: Try searching by different information (DOB, phone number). If still can't find, ask receptionist to register patient.

### Problem: Insurance Code is Wrong

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| System suggested wrong code | Billing officer can select correct code manually |
| Diagnosis wasn't entered correctly | Doctor reviews and corrects diagnosis |
| Code doesn't exist in lookup table | Billing officer can add new code (with IT admin) |

**What to do**: Billing officer reviews and corrects the code. Contact billing officer if unsure.

### Problem: Imaging Won't Upload

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| File is too large | Compress image; try again |
| Internet is down | Wait for internet; try again |
| Imaging equipment not connected | Check equipment connection; try again |
| Storage is full | Contact IT admin; delete old files |

**What to do**: Try uploading again. If still doesn't work, contact IT admin.

### Problem: PhilHealth Claim Was Rejected

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| Invalid diagnosis code | Billing officer checks and corrects code |
| Invalid procedure code | Billing officer checks and corrects code |
| Patient not eligible | Verify patient PhilHealth coverage |
| Duplicate claim | Check if claim was already submitted |
| Missing information | Billing officer adds missing information |

**What to do**: Billing officer reviews rejection reason and corrects the issue. Claim is resubmitted.

### Problem: Appointment Won't Schedule

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| Time slot is full | Choose different time |
| Doctor is not available | Choose different date |
| Patient already has appointment | Cancel old appointment first |
| System is down | Wait for system; try again |

**What to do**: Try different date/time. If still doesn't work, contact receptionist.

### Problem: I Accidentally Deleted Something

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| Deleted patient record | Contact IT admin; may be able to restore |
| Deleted appointment | Reschedule appointment |
| Deleted diagnosis | Re-enter diagnosis |
| Deleted imaging | Re-upload imaging |

**What to do**: Contact IT admin immediately. They may be able to restore deleted information.

### Problem: I Can't See Another Staff Member's Patient

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| You don't have permission | This is normal; only authorized staff can see patient |
| Patient record is locked | Contact IT admin to unlock |
| System is down | Wait for system; try again |

**What to do**: This is usually correct (privacy protection). If you need access, ask your supervisor or IT admin.

### Problem: System Says I Don't Have Permission to Do Something

**Possible Causes and Solutions**:

| Problem | Solution |
|---------|----------|
| Your role doesn't allow this action | Ask your supervisor or IT admin |
| You need to be trained on this task | Ask for training |
| Your account needs to be updated | Contact IT admin |

**What to do**: Ask your supervisor or IT admin. They can update your permissions or provide training.

---

## PART 6: QUICK REFERENCE GUIDES

### Pre-Exam Measurements Quick Reference

**Visual Acuity (VA)**:
- Measure both eyes separately
- With and without glasses (if patient wears them)
- Record as: 6/6, 6/9, 6/12, 6/18, 6/24, 6/60, CF (count fingers), HM (hand movements), LP (light perception), NLP (no light perception)
- If patient can't read chart: use counting fingers or hand movements

**Intraocular Pressure (IOP)**:
- Measure both eyes
- Use tonometer (applanation or rebound)
- Record in mmHg
- Normal range: 10-21 mmHg
- Alert doctor if >25 mmHg

**Vital Signs**:
- Blood pressure (systolic/diastolic)
- Pulse (beats per minute)
- Temperature (Celsius)
- Respiratory rate (breaths per minute)

### Common Diagnoses and Insurance Codes

| Diagnosis | ICD-10 Code | Common RVS Code |
|-----------|------------|-----------------|
| Cataract | H25.9 | 66840 |
| Glaucoma | H40.9 | 92004 |
| Diabetic retinopathy | H35.3 | 67040 |
| Age-related macular degeneration | H35.3 | 92004 |
| Refractive error | H52.9 | 92004 |
| Dry eye | H04.1 | 92004 |
| Presbyopia | H52.4 | 92004 |
| Floaters | H43.3 | 92004 |

**Note**: System suggests codes automatically. Use this table for reference only.

### Common Procedures and RVS Codes

| Procedure | RVS Code | Typical Fee |
|-----------|----------|------------|
| Office visit (new patient) | 99213 | 800 PHP |
| Office visit (follow-up) | 99213 | 500 PHP |
| Comprehensive eye exam | 92004 | 800 PHP |
| Dilated eye exam | 92012 | 600 PHP |
| Cataract surgery | 66840 | 15,000 PHP |
| Laser photocoagulation | 67040 | 5,000 PHP |
| Laser iridotomy | 66761 | 3,000 PHP |
| OCT imaging | 92134 | 1,200 PHP |
| Visual field testing | 92081 | 1,500 PHP |
| Biometry | 76512 | 800 PHP |

**Note**: Fees vary by facility and insurance. This is for reference only.

### Common Medications Quick Reference

| Medication | Use | Dose | Notes |
|-----------|-----|------|-------|
| Tropicamide 1% | Dilation | 1 drop | Onset 20-30 min; wear sunglasses |
| Phenylephrine 2.5% | Dilation | 1 drop | Use with tropicamide |
| Timolol 0.5% | Glaucoma | 1 drop BID | Check pulse before dispensing |
| Latanoprost 0.005% | Glaucoma | 1 drop QHS | May darken iris; causes lash growth |
| Dorzolamide 2% | Glaucoma | 1 drop TID | Sulfonamide; check allergy |
| Moxifloxacin 0.5% | Infection | 1 drop QID | Fluoroquinolone antibiotic |
| Artificial tears | Dry eye | 1 drop QID | Preservative-free preferred |
| Dexamethasone 0.1% | Inflammation | 1 drop QID | Taper; monitor IOP |

**Note**: Always check patient allergies. Confirm dosing with doctor.

---

## PART 7: KEY TIPS FOR SUCCESS

### Tip 1: Understand Your Role

Each staff member has a specific role:
- **Receptionist**: Registration and scheduling
- **Nurse**: Pre-exam and patient preparation
- **Technician**: Imaging and equipment
- **Doctor**: Examination and diagnosis
- **Billing Officer**: Insurance and payment

**Success**: Know your role and do it well. Don't try to do someone else's job.

### Tip 2: Enter Information Completely

Incomplete information causes problems later:
- Missing diagnosis code → claim denied
- Missing procedure code → billing error
- Missing patient contact → can't reach for follow-up

**Success**: Take time to enter complete information. It saves time later.

### Tip 3: Use the Lookup Tables

The system has built-in lookup tables for:
- Diagnosis codes (ICD-10)
- Procedure codes (RVS)
- Medications
- Follow-up intervals

**Success**: Use these tables instead of typing. It prevents errors.

### Tip 4: Ask for Help

If you're unsure about something:
- Ask your supervisor
- Ask a colleague
- Contact IT admin
- Read this manual

**Success**: It's better to ask than to make a mistake.

### Tip 5: Document Everything

If something unusual happens:
- Patient can't afford treatment → document in notes
- Patient has allergy → document in allergy field
- Patient didn't show up → mark as no-show
- System problem → tell IT admin

**Success**: Good documentation helps everyone understand what happened.

### Tip 6: Don't Panic When Internet is Down

The system works offline. You can:
- See patients normally
- Enter information on paper
- Continue working
- Sync when internet returns

**Success**: Internet outages are normal. Patient care continues.

### Tip 7: Protect Patient Privacy

Patient information is confidential:
- Don't share passwords
- Don't leave computer unattended
- Don't discuss patient information in public
- Log out when you're done

**Success**: Protecting privacy protects patients and the department.

### Tip 8: Give Feedback

If something doesn't work well:
- Tell your supervisor
- Tell IT admin
- Suggest improvements
- Help make the system better

**Success**: Your feedback helps improve the system for everyone.

---

## PART 8: GETTING HELP

### Who to Contact for Different Problems

| Problem | Contact | How |
|---------|---------|-----|
| Can't log in | IT Administrator | In person or phone |
| System is slow | IT Administrator | In person or phone |
| System is down | IT Administrator | In person or phone |
| Lost patient record | IT Administrator | In person or phone |
| Unsure about diagnosis code | Billing Officer or Doctor | In person |
| Unsure about procedure code | Billing Officer or Doctor | In person |
| Unsure about medication | Doctor or Pharmacist | In person |
| Unsure about patient care | Doctor or Supervisor | In person |
| Unsure about scheduling | Receptionist | In person |
| Unsure about anything else | Your Supervisor | In person |

### IT Administrator Contact Information

**Name**: [To be filled in]  
**Phone**: [To be filled in]  
**Email**: [To be filled in]  
**Office**: [To be filled in]  
**Hours**: [To be filled in]  
**Emergency**: [To be filled in]

### Training and Support

- **Initial training**: [Date and time to be scheduled]
- **Refresher training**: [Quarterly, dates to be scheduled]
- **One-on-one support**: Available from IT admin
- **This manual**: Always available for reference

---

## CONCLUSION: YOU'VE GOT THIS

OpenEyes is designed to make your job easier, not harder. Remember:

- **The system helps you care for patients better**
- **Paper is always a backup if something goes wrong**
- **Your job is to care for patients; the system helps with paperwork**
- **Ask for help if you need it**
- **You're not alone—everyone is learning together**

Welcome to the team. We're glad you're here.

---

**Questions?** Ask your supervisor or contact the IT administrator.

**Need this manual in another language?** Ask your supervisor.

**Want to suggest improvements?** Tell your supervisor or IT admin.

---

**Document Version**: 1.0  
**Last Updated**: February 2026  
**Next Review**: August 2026

