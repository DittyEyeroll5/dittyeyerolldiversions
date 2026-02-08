# OpenEyes Clinic Setup Worksheet
## Configuration and Readiness Planning

**Facility Name**: ________________________  
**Facility Address**: ________________________  
**Department**: Ophthalmology  
**Setup Date**: ________________________  
**Responsible Person**: ________________________  
**Contact**: ________________________

---

## SECTION 1: FACILITY INFORMATION

### Basic Information

| Item | Value | Status |
|------|-------|--------|
| Facility Name | | ☐ Complete |
| Facility Address | | ☐ Complete |
| City/Province | | ☐ Complete |
| Contact Phone | | ☐ Complete |
| Contact Email | | ☐ Complete |
| Department Head Name | | ☐ Complete |
| Department Head Phone | | ☐ Complete |

### PhilHealth Information

| Item | Value | Status |
|------|-------|--------|
| PhilHealth Facility ID | | ☐ Complete |
| Facility Accreditation Status | | ☐ Complete |
| Accreditation Expiry Date | | ☐ Complete |
| Contact Person at PhilHealth | | ☐ Complete |
| PhilHealth Contact Phone | | ☐ Complete |

---

## SECTION 2: INFRASTRUCTURE SETUP

### Server Setup

| Item | Specification | Status |
|------|---------------|--------|
| Server Hardware | Processor: __________ RAM: __________ Storage: __________ | ☐ Complete |
| Operating System | ☐ Linux ☐ Windows ☐ macOS | ☐ Complete |
| Database | ☐ PostgreSQL ☐ MySQL ☐ Other: __________ | ☐ Complete |
| Database Size | __________ GB | ☐ Complete |
| Server Location | __________ | ☐ Complete |
| Server Security | ☐ Locked cabinet ☐ Restricted access | ☐ Complete |
| Backup Drive | __________ GB ☐ Encrypted | ☐ Complete |
| Backup Location | __________ | ☐ Complete |

### Network Setup

| Item | Specification | Status |
|------|---------------|--------|
| Internet Provider | __________ | ☐ Complete |
| Internet Speed | __________ Mbps | ☐ Complete |
| Internet Reliability | ☐ Reliable ☐ Intermittent ☐ Unreliable | ☐ Complete |
| Mesh VPN Software | ☐ Tailscale ☐ Wireguard ☐ Other: __________ | ☐ Complete |
| VPN Server Setup | ☐ Configured ☐ Tested | ☐ Complete |
| VPN Backup Method | ☐ Direct IP access ☐ Other: __________ | ☐ Complete |
| Firewall Configuration | ☐ Configured | ☐ Complete |

### Workstation Setup

| Item | Specification | Status |
|------|---------------|--------|
| Number of Workstations | __________ | ☐ Complete |
| Workstation 1 | Owner: __________ OS: __________ | ☐ Complete |
| Workstation 2 | Owner: __________ OS: __________ | ☐ Complete |
| Workstation 3 | Owner: __________ OS: __________ | ☐ Complete |
| Workstation 4 | Owner: __________ OS: __________ | ☐ Complete |
| VPN Client Installed | ☐ All workstations | ☐ Complete |
| VPN Connection Tested | ☐ All workstations | ☐ Complete |

---

## SECTION 3: STAFF AND ROLES

### Staff Roster

| Name | Role | Email | Phone | Status |
|------|------|-------|-------|--------|
| | Consultant | | | ☐ Account created |
| | Resident | | | ☐ Account created |
| | Nurse | | | ☐ Account created |
| | Technician | | | ☐ Account created |
| | Receptionist | | | ☐ Account created |
| | Billing Officer | | | ☐ Account created |
| | IT Administrator | | | ☐ Account created |

### Role Assignments

| Role | Assigned To | Permissions | Status |
|------|------------|-------------|--------|
| Consultant | __________ | All clinical + approval | ☐ Configured |
| Resident | __________ | Clinical (supervised) | ☐ Configured |
| Nurse | __________ | Pre-exam + procedures | ☐ Configured |
| Technician | __________ | Imaging only | ☐ Configured |
| Receptionist | __________ | Registration + scheduling | ☐ Configured |
| Billing Officer | __________ | Billing + claims | ☐ Configured |
| IT Administrator | __________ | System + all data | ☐ Configured |

---

## SECTION 4: CLINICAL CONFIGURATION

### Clinic Schedule

| Day | Hours | Status |
|-----|-------|--------|
| Monday | From: __________ To: __________ | ☐ Configured |
| Tuesday | From: __________ To: __________ | ☐ Configured |
| Wednesday | From: __________ To: __________ | ☐ Configured |
| Thursday | From: __________ To: __________ | ☐ Configured |
| Friday | From: __________ To: __________ | ☐ Configured |
| Saturday | From: __________ To: __________ | ☐ Configured |
| Sunday | From: __________ To: __________ | ☐ Configured |

### Appointment Configuration

| Item | Value | Status |
|------|-------|--------|
| Appointment Slot Duration | __________ minutes | ☐ Configured |
| New Patient Appointment Duration | __________ minutes | ☐ Configured |
| Follow-up Appointment Duration | __________ minutes | ☐ Configured |
| Procedure Appointment Duration | __________ minutes | ☐ Configured |
| Maximum Appointments per Day | __________ | ☐ Configured |

### Diagnosis Codes (ICD-10)

| Diagnosis | ICD-10 Code | Status |
|-----------|------------|--------|
| Cataract | H25.9 | ☐ Loaded |
| Glaucoma | H40.9 | ☐ Loaded |
| Diabetic Retinopathy | H35.3 | ☐ Loaded |
| Age-related Macular Degeneration | H35.3 | ☐ Loaded |
| Refractive Error | H52.9 | ☐ Loaded |
| Dry Eye | H04.1 | ☐ Loaded |
| Presbyopia | H52.4 | ☐ Loaded |
| Other: __________ | __________ | ☐ Loaded |

### Procedure Codes (RVS)

| Procedure | RVS Code | Typical Fee | Status |
|-----------|----------|------------|--------|
| Office Visit (New) | 99213 | __________ PHP | ☐ Loaded |
| Office Visit (Follow-up) | 99213 | __________ PHP | ☐ Loaded |
| Comprehensive Exam | 92004 | __________ PHP | ☐ Loaded |
| Dilated Exam | 92012 | __________ PHP | ☐ Loaded |
| Cataract Surgery | 66840 | __________ PHP | ☐ Loaded |
| Laser Photocoagulation | 67040 | __________ PHP | ☐ Loaded |
| Laser Iridotomy | 66761 | __________ PHP | ☐ Loaded |
| OCT Imaging | 92134 | __________ PHP | ☐ Loaded |
| Visual Field Testing | 92081 | __________ PHP | ☐ Loaded |
| Biometry | 76512 | __________ PHP | ☐ Loaded |
| Other: __________ | __________ | __________ PHP | ☐ Loaded |

### Drug Formulary

| Medication | Indication | Dose | Status |
|-----------|-----------|------|--------|
| Tropicamide 1% | Dilation | 1 drop | ☐ Loaded |
| Phenylephrine 2.5% | Dilation | 1 drop | ☐ Loaded |
| Timolol 0.5% | Glaucoma | 1 drop BID | ☐ Loaded |
| Latanoprost 0.005% | Glaucoma | 1 drop QHS | ☐ Loaded |
| Dorzolamide 2% | Glaucoma | 1 drop TID | ☐ Loaded |
| Moxifloxacin 0.5% | Infection | 1 drop QID | ☐ Loaded |
| Artificial Tears | Dry Eye | 1 drop QID | ☐ Loaded |
| Dexamethasone 0.1% | Inflammation | 1 drop QID | ☐ Loaded |
| Other: __________ | __________ | __________ | ☐ Loaded |

---

## SECTION 5: BILLING CONFIGURATION

### Consultation Fees

| Service | Fee (PHP) | PhilHealth Covered | Status |
|---------|-----------|-------------------|--------|
| New Patient Consultation | __________ | ☐ Yes ☐ No | ☐ Configured |
| Follow-up Consultation | __________ | ☐ Yes ☐ No | ☐ Configured |
| Comprehensive Eye Exam | __________ | ☐ Yes ☐ No | ☐ Configured |
| Dilated Eye Exam | __________ | ☐ Yes ☐ No | ☐ Configured |

### Procedure Fees

| Procedure | Fee (PHP) | PhilHealth Covered | Status |
|-----------|-----------|-------------------|--------|
| Cataract Surgery | __________ | ☐ Yes ☐ No | ☐ Configured |
| Laser Photocoagulation | __________ | ☐ Yes ☐ No | ☐ Configured |
| Laser Iridotomy | __________ | ☐ Yes ☐ No | ☐ Configured |
| Other: __________ | __________ | ☐ Yes ☐ No | ☐ Configured |

### Imaging Fees

| Imaging Type | Fee (PHP) | PhilHealth Covered | Status |
|--------------|-----------|-------------------|--------|
| OCT | __________ | ☐ Yes ☐ No | ☐ Configured |
| Visual Field | __________ | ☐ Yes ☐ No | ☐ Configured |
| Biometry | __________ | ☐ Yes ☐ No | ☐ Configured |
| Photography | __________ | ☐ Yes ☐ No | ☐ Configured |

### Payment Methods

| Payment Method | Accepted | Notes | Status |
|---|---|---|---|
| Cash | ☐ Yes ☐ No | | ☐ Configured |
| PhilHealth | ☐ Yes ☐ No | | ☐ Configured |
| Private Insurance | ☐ Yes ☐ No | Which: __________ | ☐ Configured |
| Payment Plan | ☐ Yes ☐ No | Terms: __________ | ☐ Configured |

---

## SECTION 6: PHILHEALTH INTEGRATION

### PhilHealth Credentials

| Item | Value | Status |
|------|-------|--------|
| Facility ID | __________ | ☐ Verified |
| Username | __________ | ☐ Verified |
| Password | __________ | ☐ Verified |
| API Endpoint | __________ | ☐ Verified |
| Test Connection | ☐ Success ☐ Failed | ☐ Tested |

### PhilHealth Submission Schedule

| Item | Value | Status |
|------|-------|--------|
| Submission Frequency | ☐ Daily ☐ Weekly ☐ Monthly | ☐ Configured |
| Submission Time | __________ | ☐ Configured |
| Submission Day (if weekly) | __________ | ☐ Configured |
| Contact Person | __________ | ☐ Assigned |
| Contact Phone | __________ | ☐ Recorded |

### PhilHealth Claim Tracking

| Item | Value | Status |
|------|-------|--------|
| Tracking Method | ☐ Automated ☐ Manual | ☐ Configured |
| Tracking Frequency | ☐ Daily ☐ Weekly ☐ Monthly | ☐ Configured |
| Denial Review Process | ☐ Documented | ☐ Documented |
| Resubmission Process | ☐ Documented | ☐ Documented |

---

## SECTION 7: DATA BACKUP AND SECURITY

### Backup Configuration

| Item | Specification | Status |
|------|---------------|--------|
| Backup Frequency | ☐ Daily ☐ Weekly ☐ Monthly | ☐ Configured |
| Backup Time | __________ | ☐ Configured |
| Backup Location | __________ | ☐ Configured |
| Backup Encryption | ☐ Yes ☐ No | ☐ Configured |
| Backup Verification | ☐ Tested | ☐ Tested |
| Backup Retention | __________ days/weeks/months | ☐ Configured |

### Security Configuration

| Item | Specification | Status |
|------|---------------|--------|
| Database Encryption | ☐ Yes ☐ No | ☐ Configured |
| Password Policy | Min length: __________ | ☐ Configured |
| Session Timeout | __________ minutes | ☐ Configured |
| Audit Logging | ☐ Enabled | ☐ Configured |
| Audit Log Retention | __________ years | ☐ Configured |
| Access Control | ☐ Role-based | ☐ Configured |

---

## SECTION 8: SATELLITE CLINIC SETUP (If Applicable)

### Satellite Clinic Information

| Item | Value | Status |
|------|-------|--------|
| Clinic Name | __________ | ☐ Complete |
| Clinic Address | __________ | ☐ Complete |
| Clinic Contact | __________ | ☐ Complete |
| Clinic Manager | __________ | ☐ Complete |
| Distance from Main Clinic | __________ km | ☐ Complete |

### Satellite Clinic Access

| Item | Specification | Status |
|------|---------------|--------|
| VPN Access | ☐ Yes ☐ No | ☐ Configured |
| Workstations | __________ | ☐ Configured |
| Internet Connectivity | ☐ Reliable ☐ Intermittent | ☐ Assessed |
| Backup Internet | ☐ Mobile hotspot ☐ Other: __________ | ☐ Configured |

### Satellite Clinic Data Sync

| Item | Specification | Status |
|------|---------------|--------|
| Sync Method | ☐ Automated ☐ Manual | ☐ Configured |
| Sync Frequency | ☐ Daily ☐ Weekly ☐ On-demand | ☐ Configured |
| Sync Time | __________ | ☐ Configured |
| Sync Encryption | ☐ Yes ☐ No | ☐ Configured |
| Sync Verification | ☐ Tested | ☐ Tested |

---

## SECTION 9: TRAINING SCHEDULE

### Training Plan

| Phase | Dates | Trainer | Status |
|-------|-------|---------|--------|
| Phase 1: Pre-training | From: __________ To: __________ | __________ | ☐ Scheduled |
| Phase 2: Initial training | From: __________ To: __________ | __________ | ☐ Scheduled |
| Phase 3: Role-specific | From: __________ To: __________ | __________ | ☐ Scheduled |
| Phase 4: Hands-on practice | From: __________ To: __________ | __________ | ☐ Scheduled |
| Phase 5: Independent practice | From: __________ To: __________ | __________ | ☐ Scheduled |

### Training Materials

| Material | Available | Status |
|----------|-----------|--------|
| Clinician Onboarding Manual | ☐ Printed ☐ Digital | ☐ Distributed |
| Quick Reference Guides | ☐ Printed ☐ Digital | ☐ Distributed |
| Role-specific Guides | ☐ Printed ☐ Digital | ☐ Distributed |
| Troubleshooting Guide | ☐ Printed ☐ Digital | ☐ Distributed |
| Contact Information Sheet | ☐ Printed ☐ Digital | ☐ Distributed |

---

## SECTION 10: GO-LIVE PREPARATION

### System Readiness

| Item | Status |
|------|--------|
| Server configured and tested | ☐ Complete |
| Database initialized | ☐ Complete |
| Backup system tested | ☐ Complete |
| VPN configured and tested | ☐ Complete |
| User accounts created | ☐ Complete |
| Roles and permissions configured | ☐ Complete |
| Clinical codes loaded (ICD-10, RVS) | ☐ Complete |
| Drug formulary loaded | ☐ Complete |
| PhilHealth credentials verified | ☐ Complete |
| Imaging equipment connected | ☐ Complete |

### Staff Readiness

| Item | Status |
|------|--------|
| All staff trained | ☐ Complete |
| All staff competency verified | ☐ Complete |
| IT administrator trained | ☐ Complete |
| Backup IT support identified | ☐ Complete |
| Support contact information distributed | ☐ Complete |
| Troubleshooting guide reviewed | ☐ Complete |

### Operational Readiness

| Item | Status |
|------|--------|
| Clinic schedule configured | ☐ Complete |
| Appointment slots available | ☐ Complete |
| Paper backup forms available | ☐ Complete |
| Patient education materials available | ☐ Complete |
| Referral forms available | ☐ Complete |
| Appointment cards available | ☐ Complete |

### Go-Live Approval

| Item | Approved By | Date | Status |
|------|------------|------|--------|
| System Readiness | IT Administrator | __________ | ☐ Approved |
| Staff Readiness | Department Head | __________ | ☐ Approved |
| Operational Readiness | Department Head | __________ | ☐ Approved |
| Go-Live Authorization | Department Head | __________ | ☐ Approved |

---

## SECTION 11: POST-LAUNCH SUPPORT

### Support Team

| Role | Name | Phone | Email | Hours |
|------|------|-------|-------|-------|
| IT Administrator | __________ | __________ | __________ | __________ |
| Backup IT Support | __________ | __________ | __________ | __________ |
| Department Head | __________ | __________ | __________ | __________ |
| Trainer | __________ | __________ | __________ | __________ |

### Support Schedule

| Day | Hours | On-Call | Status |
|-----|-------|---------|--------|
| Monday | __________ | __________ | ☐ Scheduled |
| Tuesday | __________ | __________ | ☐ Scheduled |
| Wednesday | __________ | __________ | ☐ Scheduled |
| Thursday | __________ | __________ | ☐ Scheduled |
| Friday | __________ | __________ | ☐ Scheduled |
| Saturday | __________ | __________ | ☐ Scheduled |
| Sunday | __________ | __________ | ☐ Scheduled |

### Feedback and Improvement

| Item | Frequency | Owner | Status |
|------|-----------|-------|--------|
| Staff feedback collection | ☐ Weekly ☐ Monthly | __________ | ☐ Scheduled |
| System performance review | ☐ Weekly ☐ Monthly | __________ | ☐ Scheduled |
| Incident review | ☐ Weekly ☐ Monthly | __________ | ☐ Scheduled |
| Process improvement meeting | ☐ Weekly ☐ Monthly | __________ | ☐ Scheduled |

---

## SIGN-OFF

### IT Administrator Sign-Off

I confirm that the system is properly configured and ready for clinical use.

**Name**: ________________________  
**Signature**: ________________________  
**Date**: ________________________

### Department Head Sign-Off

I confirm that the staff is trained and the clinic is ready for go-live.

**Name**: ________________________  
**Signature**: ________________________  
**Date**: ________________________

### Project Manager Sign-Off

I confirm that all setup tasks are complete and the project is ready for launch.

**Name**: ________________________  
**Signature**: ________________________  
**Date**: ________________________

---

## NOTES

**Setup Notes**:

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Issues and Resolutions**:

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

**Lessons Learned**:

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

---

**Document Version**: 1.0  
**Last Updated**: February 2026

