# OpenEyes Role Responsibility Matrix
## Staff Roles, Responsibilities, and Permissions

---

## ROLE DEFINITIONS AND RESPONSIBILITIES

### 1. CONSULTANT OPHTHALMOLOGIST

**Role Summary**: Senior clinician responsible for all clinical decisions, diagnosis, treatment planning, and procedure approval.

**Primary Responsibilities**:

| Responsibility | Description | Frequency | Approval Required |
|---|---|---|---|
| **Patient Examination** | Perform comprehensive eye examination; document findings | Per patient | Self |
| **Diagnosis** | Formulate diagnosis and assign ICD-10 code | Per patient | Self |
| **Treatment Planning** | Develop treatment plan; discuss options with patient | Per patient | Self |
| **Procedure Approval** | Review and approve procedures planned by residents | Per procedure | Self |
| **Resident Supervision** | Review resident examinations and provide feedback | Daily | Self |
| **Imaging Review** | Review and interpret diagnostic imaging | Per imaging | Self |
| **Laser Procedures** | Perform laser procedures; document parameters | Per procedure | Self |
| **Surgical Procedures** | Perform surgical procedures; document findings | Per procedure | Self |
| **Emergency Cases** | Assess and manage emergency presentations | Per emergency | Self |
| **Insurance Coding Review** | Verify diagnosis and procedure codes | Weekly | Self |
| **Quality Assurance** | Monitor clinical quality and patient outcomes | Monthly | Self |

**System Permissions**:

| Function | Permission | Notes |
|---|---|---|
| View all patient records | Full access | All patients |
| Create patient records | Yes | New patients |
| Edit patient records | Yes | Own records; review others |
| View all encounters | Full access | All encounters |
| Create encounters | Yes | Own encounters |
| Edit encounters | Yes | Own encounters; review others |
| Document examination findings | Yes | Own examinations |
| Assign diagnosis codes | Yes | Own diagnoses |
| Assign RVS codes | Yes | Own procedures |
| Approve procedures | Yes | All procedures |
| Approve imaging | Yes | All imaging |
| View imaging | Yes | All imaging |
| View medications | Yes | All medications |
| Prescribe medications | Yes | Own prescriptions |
| View billing information | Read-only | For verification |
| View PhilHealth claims | Read-only | For verification |
| Approve claims | No | Billing officer approves |
| Access reports | Full access | All reports |
| Access audit logs | No | IT admin only |
| Manage users | No | IT admin only |
| Manage system configuration | No | IT admin only |

**Training Requirements**:
- Initial: 40 hours (comprehensive training)
- Ongoing: 4 hours annually (updates and new features)
- Competency verification: Quarterly

**Performance Metrics**:
- Average time per patient: 10-15 minutes
- Diagnosis accuracy: >95%
- Coding accuracy: >95%
- Patient satisfaction: >90%
- Procedure complication rate: <2%

---

### 2. RESIDENT OPHTHALMOLOGIST

**Role Summary**: Junior clinician performing examinations under consultant supervision; learning clinical skills and documentation.

**Primary Responsibilities**:

| Responsibility | Description | Frequency | Approval Required |
|---|---|---|---|
| **Patient Examination** | Perform eye examination; document findings | Per patient | Consultant review |
| **Preliminary Diagnosis** | Formulate preliminary diagnosis; suggest ICD-10 code | Per patient | Consultant approval |
| **Imaging Requests** | Order appropriate imaging; justify indication | Per patient | Consultant approval |
| **Procedure Requests** | Request procedures; document indication | Per patient | Consultant approval |
| **Documentation** | Document findings in structured format | Per patient | Consultant review |
| **Patient Communication** | Explain findings to patient (under consultant guidance) | Per patient | Consultant oversight |
| **Pre-operative Workup** | Perform pre-operative assessment for procedures | Per procedure | Consultant approval |
| **Procedure Assistance** | Assist consultant during procedures | Per procedure | Consultant supervision |
| **Follow-up Exams** | Perform follow-up examinations | Per patient | Consultant review |
| **Learning and Development** | Participate in training and case discussions | Weekly | Self |

**System Permissions**:

| Function | Permission | Notes |
|---|---|---|
| View own patient records | Yes | Assigned patients |
| View other residents' records | Yes | For learning |
| View consultant's records | Yes | For learning |
| Create patient records | No | Receptionist creates |
| Edit patient records | Limited | Own records only |
| View own encounters | Yes | Own encounters |
| Create encounters | Yes | Own examinations |
| Edit encounters | Yes | Own encounters only |
| Document examination findings | Yes | Own examinations |
| Assign diagnosis codes | Yes | Preliminary; consultant verifies |
| Assign RVS codes | Yes | Request only; consultant assigns |
| Approve procedures | No | Consultant approves |
| Approve imaging | No | Consultant approves |
| View imaging | Yes | All imaging |
| View medications | Yes | All medications |
| Prescribe medications | Limited | Under consultant guidance |
| View billing information | Read-only | For learning |
| View PhilHealth claims | Read-only | For learning |
| Approve claims | No | Billing officer approves |
| Access reports | Yes | Own reports |
| Access audit logs | No | IT admin only |
| Manage users | No | IT admin only |
| Manage system configuration | No | IT admin only |

**Training Requirements**:
- Initial: 40 hours (comprehensive training)
- Ongoing: 4 hours annually (updates)
- Competency verification: Monthly (by consultant)

**Performance Metrics**:
- Average time per patient: 15-20 minutes
- Examination completeness: >90%
- Documentation completeness: >95%
- Consultant feedback: Positive trend
- Learning progression: Documented

---

### 3. OPHTHALMIC NURSE

**Role Summary**: Clinical support staff responsible for patient preparation, pre-examination measurements, procedure assistance, and patient education.

**Primary Responsibilities**:

| Responsibility | Description | Frequency | Approval Required |
|---|---|---|---|
| **Patient Registration Verification** | Verify patient information at check-in | Per patient | Self |
| **Pre-exam Measurements** | Measure visual acuity, eye pressure, vital signs | Per patient | Self |
| **Patient Preparation** | Prepare patient for examination or procedure | Per patient | Self |
| **Procedure Assistance** | Assist during procedures; monitor patient | Per procedure | Consultant supervision |
| **Post-operative Care** | Provide post-operative instructions and care | Per procedure | Self |
| **Patient Education** | Provide pre- and post-operative education | Per patient | Self |
| **Appointment Scheduling** | Schedule follow-up appointments | Per patient | Self |
| **Medication Administration** | Instill eye drops and medications | Per patient | Consultant order |
| **Equipment Maintenance** | Maintain clinical equipment; report problems | Daily | Self |
| **Documentation** | Record measurements and observations | Per patient | Self |
| **Patient Safety** | Monitor patient safety during procedures | Per procedure | Self |

**System Permissions**:

| Function | Permission | Notes |
|---|---|---|
| View patient records | Yes | Current patients |
| Create patient records | No | Receptionist creates |
| Edit patient records | No | Receptionist edits |
| View encounters | Yes | Current patients |
| Create encounters | No | Doctor creates |
| Edit encounters | No | Doctor edits |
| Document pre-exam | Yes | Own pre-exams |
| Document vital signs | Yes | Own measurements |
| Document procedure assistance | Yes | Own assistance |
| Assign diagnosis codes | No | Doctor assigns |
| Assign RVS codes | No | Doctor assigns |
| Approve procedures | No | Doctor approves |
| Approve imaging | No | Doctor approves |
| View imaging | Yes | Current patients |
| View medications | Yes | Current patients |
| Prescribe medications | No | Doctor prescribes |
| View billing information | No | Not needed |
| View PhilHealth claims | No | Not needed |
| Approve claims | No | Billing officer approves |
| Access reports | No | Not needed |
| Access audit logs | No | IT admin only |
| Manage users | No | IT admin only |
| Manage system configuration | No | IT admin only |

**Training Requirements**:
- Initial: 20 hours (role-specific training)
- Ongoing: 2 hours annually (updates)
- Competency verification: Semi-annually

**Performance Metrics**:
- Pre-exam accuracy: >95%
- Patient satisfaction: >90%
- Procedure complication rate: <1%
- Documentation completeness: >95%
- Appointment scheduling accuracy: >98%

---

### 4. OPHTHALMIC TECHNICIAN

**Role Summary**: Diagnostic equipment specialist responsible for imaging acquisition, quality control, and equipment maintenance.

**Primary Responsibilities**:

| Responsibility | Description | Frequency | Per imaging |
|---|---|---|---|
| **Imaging Acquisition** | Operate diagnostic equipment; acquire images | Per imaging | Self |
| **Image Quality Control** | Assess image quality; flag poor-quality images | Per imaging | Self |
| **Equipment Operation** | Operate OCT, visual fields, biometry, photography | Per imaging | Self |
| **Patient Preparation** | Prepare patient for imaging; explain procedure | Per imaging | Self |
| **Image Upload** | Upload images to system; verify upload | Per imaging | Self |
| **Equipment Maintenance** | Maintain equipment; perform basic troubleshooting | Daily | Self |
| **Equipment Calibration** | Calibrate equipment per manufacturer guidelines | Per schedule | Self |
| **Laser Assistance** | Assist during laser procedures | Per procedure | Consultant supervision |
| **Documentation** | Record test parameters and image quality | Per imaging | Self |
| **Equipment Reporting** | Report equipment problems to IT admin | Per problem | Self |

**System Permissions**:

| Function | Permission | Notes |
|---|---|---|
| View patient records | Limited | Imaging patients only |
| Create patient records | No | Receptionist creates |
| Edit patient records | No | Receptionist edits |
| View encounters | Limited | Imaging encounters only |
| Create encounters | No | Doctor creates |
| Edit encounters | No | Doctor edits |
| Document imaging | Yes | Own imaging only |
| Upload imaging | Yes | Own imaging only |
| Record test parameters | Yes | Own imaging only |
| Assign diagnosis codes | No | Doctor assigns |
| Assign RVS codes | No | Doctor assigns |
| Approve procedures | No | Doctor approves |
| Approve imaging | No | Doctor approves |
| View imaging | Yes | Own imaging |
| View medications | No | Not needed |
| Prescribe medications | No | Not needed |
| View billing information | No | Not needed |
| View PhilHealth claims | No | Not needed |
| Approve claims | No | Billing officer approves |
| Access reports | No | Not needed |
| Access audit logs | No | IT admin only |
| Manage users | No | IT admin only |
| Manage system configuration | No | IT admin only |

**Training Requirements**:
- Initial: 30 hours (equipment-specific training)
- Ongoing: 4 hours annually (updates and new equipment)
- Competency verification: Semi-annually

**Performance Metrics**:
- Image quality: >95% acceptable
- Equipment uptime: >98%
- Imaging turnaround time: <2 hours
- Documentation completeness: >95%
- Equipment maintenance compliance: 100%

---

### 5. RECEPTIONIST / ADMINISTRATIVE STAFF

**Role Summary**: Administrative support staff responsible for patient registration, appointment scheduling, and front-desk operations.

**Primary Responsibilities**:

| Responsibility | Description | Frequency | Approval Required |
|---|---|---|---|
| **Patient Registration** | Register new patients; enter demographics | Per new patient | Self |
| **Insurance Verification** | Verify patient insurance information | Per patient | Self |
| **Appointment Scheduling** | Schedule appointments; manage calendar | Per appointment | Self |
| **Appointment Confirmation** | Confirm appointments; remind patients | Daily | Self |
| **Appointment Cancellation** | Cancel appointments; update calendar | Per cancellation | Self |
| **Walk-in Management** | Register walk-in patients; add to queue | Per walk-in | Self |
| **Referral Forms** | Generate and print referral forms | Per referral | Self |
| **Appointment Cards** | Print appointment cards; provide to patients | Per appointment | Self |
| **Patient Communication** | Answer patient questions; provide information | Per inquiry | Self |
| **Schedule Management** | Manage clinic schedule; optimize appointments | Daily | Self |
| **Documentation** | Record patient interactions and notes | Per interaction | Self |

**System Permissions**:

| Function | Permission | Notes |
|---|---|---|
| View patient records | Limited | Demographics only |
| Create patient records | Yes | New patients |
| Edit patient records | Limited | Demographics only |
| View encounters | No | Not needed |
| Create encounters | No | Doctor creates |
| Edit encounters | No | Doctor edits |
| Document pre-exam | No | Nurse documents |
| Schedule appointments | Yes | Own scheduling |
| Cancel appointments | Yes | Own cancellations |
| View appointments | Yes | All appointments |
| Assign diagnosis codes | No | Doctor assigns |
| Assign RVS codes | No | Doctor assigns |
| Approve procedures | No | Doctor approves |
| Approve imaging | No | Doctor approves |
| View imaging | No | Not needed |
| View medications | No | Not needed |
| Prescribe medications | No | Not needed |
| View billing information | Limited | Patient charges only |
| View PhilHealth claims | No | Not needed |
| Approve claims | No | Billing officer approves |
| Access reports | No | Not needed |
| Access audit logs | No | IT admin only |
| Manage users | No | IT admin only |
| Manage system configuration | No | IT admin only |

**Training Requirements**:
- Initial: 15 hours (role-specific training)
- Ongoing: 1 hour annually (updates)
- Competency verification: Quarterly

**Performance Metrics**:
- Registration accuracy: >98%
- Appointment scheduling accuracy: >98%
- Patient satisfaction: >90%
- No-show rate: <15%
- Documentation completeness: >95%

---

### 6. BILLING OFFICER

**Role Summary**: Administrative staff responsible for insurance claims, billing, and PhilHealth compliance.

**Primary Responsibilities**:

| Responsibility | Description | Frequency | Approval Required |
|---|---|---|---|
| **Encounter Review** | Review completed encounters for billing | Daily | Self |
| **Code Verification** | Verify diagnosis and procedure codes | Per encounter | Self |
| **Code Correction** | Correct incorrect codes; consult doctor if needed | Per error | Doctor approval |
| **Claim Preparation** | Prepare PhilHealth claims | Per encounter | Self |
| **Claim Submission** | Submit claims to PhilHealth (when online) | Daily | Self |
| **Claim Tracking** | Track claim status; monitor approvals | Daily | Self |
| **Denial Management** | Review denied claims; prepare resubmission | Per denial | Doctor approval |
| **Patient Billing** | Calculate patient charges; collect payment | Per patient | Self |
| **Insurance Verification** | Verify patient insurance coverage | Per patient | Self |
| **Payment Recording** | Record payments; maintain payment records | Per payment | Self |
| **Financial Reporting** | Generate billing reports; track revenue | Monthly | Self |
| **PhilHealth Compliance** | Ensure compliance with PhilHealth requirements | Ongoing | Self |

**System Permissions**:

| Function | Permission | Notes |
|---|---|---|
| View patient records | Limited | Demographics and insurance |
| Create patient records | No | Receptionist creates |
| Edit patient records | Limited | Insurance information only |
| View encounters | Yes | All encounters |
| Create encounters | No | Doctor creates |
| Edit encounters | Limited | Coding only |
| Document pre-exam | No | Nurse documents |
| Assign diagnosis codes | Yes | Verification and correction |
| Assign RVS codes | Yes | Verification and correction |
| Approve procedures | No | Doctor approves |
| Approve imaging | No | Doctor approves |
| View imaging | No | Not needed |
| View medications | No | Not needed |
| Prescribe medications | No | Not needed |
| View billing information | Full access | All billing data |
| View PhilHealth claims | Full access | All claims |
| Approve claims | Yes | Own claims |
| Submit claims | Yes | Own submissions |
| Access reports | Yes | Billing reports |
| Access audit logs | No | IT admin only |
| Manage users | No | IT admin only |
| Manage system configuration | No | IT admin only |

**Training Requirements**:
- Initial: 25 hours (billing and coding training)
- Ongoing: 4 hours annually (PhilHealth updates)
- Competency verification: Quarterly

**Performance Metrics**:
- Coding accuracy: >98%
- Claim submission accuracy: >98%
- Claim approval rate: >90%
- Billing accuracy: >99%
- Payment collection rate: >85%

---

### 7. IT ADMINISTRATOR

**Role Summary**: Technical staff responsible for system maintenance, user management, security, and troubleshooting.

**Primary Responsibilities**:

| Responsibility | Description | Frequency | Approval Required |
|---|---|---|---|
| **User Account Management** | Create, update, delete user accounts | Per request | Department head approval |
| **User Authentication** | Manage passwords; reset credentials | Per request | Self |
| **Access Control** | Assign roles and permissions | Per request | Department head approval |
| **System Monitoring** | Monitor system health; check logs | Daily | Self |
| **Database Maintenance** | Maintain database; optimize performance | Weekly | Self |
| **Backup Management** | Perform backups; verify integrity | Daily | Self |
| **VPN Management** | Manage mesh VPN; configure access | Per request | Self |
| **Network Maintenance** | Maintain network connectivity; troubleshoot | Per issue | Self |
| **System Troubleshooting** | Diagnose and resolve system issues | Per issue | Self |
| **Software Updates** | Install updates; manage versions | Per schedule | Department head approval |
| **Security Management** | Implement security measures; manage encryption | Ongoing | Self |
| **Audit Logging** | Maintain audit logs; review for security | Weekly | Self |
| **Disaster Recovery** | Plan and test disaster recovery | Quarterly | Department head approval |
| **Documentation** | Document system configuration; maintain runbooks | Ongoing | Self |
| **Training** | Train staff on system use; provide support | Per request | Self |

**System Permissions**:

| Function | Permission | Notes |
|---|---|---|
| View patient records | Full access | Audit only |
| Create patient records | No | Receptionist creates |
| Edit patient records | No | Authorized staff edit |
| View encounters | Full access | Audit only |
| Create encounters | No | Doctor creates |
| Edit encounters | No | Authorized staff edit |
| Document pre-exam | No | Nurse documents |
| Assign diagnosis codes | No | Doctor assigns |
| Assign RVS codes | No | Doctor assigns |
| Approve procedures | No | Doctor approves |
| Approve imaging | No | Doctor approves |
| View imaging | Full access | Audit only |
| View medications | Full access | Audit only |
| Prescribe medications | No | Doctor prescribes |
| View billing information | Full access | Audit only |
| View PhilHealth claims | Full access | Audit only |
| Approve claims | No | Billing officer approves |
| Access reports | Full access | All reports |
| Access audit logs | Full access | All logs |
| Manage users | Yes | Full control |
| Manage system configuration | Yes | Full control |
| Manage backups | Yes | Full control |
| Manage security | Yes | Full control |
| Manage database | Yes | Full control |

**Training Requirements**:
- Initial: 60 hours (comprehensive system training)
- Ongoing: 8 hours annually (updates and new features)
- Competency verification: Annually

**Performance Metrics**:
- System uptime: >99%
- Average issue resolution time: <2 hours
- Backup success rate: 100%
- Security incident response time: <1 hour
- User satisfaction: >85%

---

### 8. DEPARTMENT HEAD

**Role Summary**: Administrative leader responsible for overall department operations, policy, and strategic decisions.

**Primary Responsibilities**:

| Responsibility | Description | Frequency | Approval Required |
|---|---|---|---|
| **Operational Oversight** | Oversee daily operations; monitor performance | Daily | Self |
| **Staff Management** | Manage staff; approve hiring/termination | Per request | Self |
| **Policy Development** | Develop department policies and procedures | As needed | Self |
| **Quality Assurance** | Monitor clinical quality; review outcomes | Monthly | Self |
| **Financial Oversight** | Monitor budget; approve expenditures | Monthly | Self |
| **PhilHealth Compliance** | Ensure PhilHealth compliance; maintain accreditation | Ongoing | Self |
| **System Governance** | Approve system changes; manage configuration | Per request | Self |
| **Incident Response** | Respond to critical incidents; approve resolution | Per incident | Self |
| **Strategic Planning** | Plan department growth; set objectives | Quarterly | Self |
| **Staff Development** | Support staff training and development | Ongoing | Self |
| **Patient Safety** | Ensure patient safety; investigate incidents | Per incident | Self |
| **Audit Review** | Review audit logs for compliance | Monthly | Self |

**System Permissions**:

| Function | Permission | Notes |
|---|---|---|
| View patient records | Read-only | Reports only |
| Create patient records | No | Receptionist creates |
| Edit patient records | No | Authorized staff edit |
| View encounters | Read-only | Reports only |
| Create encounters | No | Doctor creates |
| Edit encounters | No | Authorized staff edit |
| Document pre-exam | No | Nurse documents |
| Assign diagnosis codes | No | Doctor assigns |
| Assign RVS codes | No | Doctor assigns |
| Approve procedures | No | Doctor approves |
| Approve imaging | No | Doctor approves |
| View imaging | Read-only | Reports only |
| View medications | Read-only | Reports only |
| Prescribe medications | No | Doctor prescribes |
| View billing information | Read-only | Reports only |
| View PhilHealth claims | Read-only | Reports only |
| Approve claims | No | Billing officer approves |
| Access reports | Full access | All reports |
| Access audit logs | Read-only | Review only |
| Manage users | Limited | Approve requests |
| Manage system configuration | Limited | Approve changes |
| Manage backups | No | IT admin manages |
| Manage security | Limited | Approve policies |
| Manage database | No | IT admin manages |

**Training Requirements**:
- Initial: 20 hours (system overview and governance)
- Ongoing: 2 hours annually (updates)
- Competency verification: Annually

**Performance Metrics**:
- Department performance: Meets targets
- Staff satisfaction: >80%
- PhilHealth compliance: 100%
- Patient satisfaction: >90%
- Financial performance: Meets budget

---

## CROSS-FUNCTIONAL RESPONSIBILITIES

### Data Quality

| Role | Responsibility |
|---|---|
| **Doctor** | Ensure accurate diagnosis and coding |
| **Nurse** | Ensure accurate measurements and documentation |
| **Technician** | Ensure high-quality imaging |
| **Billing Officer** | Verify accuracy of codes and claims |
| **IT Administrator** | Ensure data integrity and backups |

### Patient Safety

| Role | Responsibility |
|---|---|
| **Doctor** | Clinical decision-making; procedure safety |
| **Nurse** | Patient monitoring; complication detection |
| **Technician** | Equipment safety; patient positioning |
| **Receptionist** | Patient verification; appointment accuracy |
| **IT Administrator** | System reliability; data security |

### Security and Privacy

| Role | Responsibility |
|---|---|
| **All Staff** | Protect patient privacy; follow security policies |
| **Doctor** | Appropriate access to patient data |
| **Nurse** | Confidentiality during patient care |
| **Technician** | Secure handling of imaging data |
| **Billing Officer** | Confidential handling of financial data |
| **IT Administrator** | System security; access control; encryption |

### Training and Development

| Role | Responsibility |
|---|---|
| **Department Head** | Support training and development |
| **Doctor** | Supervise and mentor residents |
| **IT Administrator** | Provide system training and support |
| **Trainer** | Conduct onboarding and ongoing training |
| **All Staff** | Participate in training and development |

---

## DECISION AUTHORITY MATRIX

### Clinical Decisions

| Decision | Authority | Consultation |
|---|---|---|
| Diagnosis | Consultant | Resident input |
| Treatment Plan | Consultant | Resident input |
| Procedure | Consultant | Resident input |
| Medication | Consultant | Pharmacist (if available) |
| Imaging | Consultant | Resident input |
| Emergency Management | Consultant | Nurse support |

### Administrative Decisions

| Decision | Authority | Consultation |
|---|---|---|
| Appointment Scheduling | Receptionist | Consultant availability |
| Patient Registration | Receptionist | Billing officer (insurance) |
| Insurance Verification | Billing Officer | Receptionist (patient info) |
| Claim Submission | Billing Officer | Doctor (coding verification) |
| Staff Hiring | Department Head | Consultant (clinical roles) |
| System Configuration | IT Administrator | Department Head (approval) |
| Policy Changes | Department Head | All staff (input) |
| Budget Approval | Department Head | Finance (if applicable) |

---

## RESPONSIBILITY SUMMARY TABLE

| Task | Consultant | Resident | Nurse | Technician | Receptionist | Billing | IT Admin | Dept Head |
|---|---|---|---|---|---|---|---|---|
| Patient examination | ✓ | ✓ | | | | | | |
| Diagnosis | ✓ | ✓* | | | | | | |
| Treatment planning | ✓ | ✓* | | | | | | |
| Procedure approval | ✓ | | | | | | | |
| Imaging review | ✓ | ✓* | | | | | | |
| Pre-exam measurements | | | ✓ | | | | | |
| Imaging acquisition | | | | ✓ | | | | |
| Patient registration | | | | | ✓ | | | |
| Appointment scheduling | | | | | ✓ | | | |
| Insurance verification | | | | | ✓ | ✓ | | |
| Billing | | | | | | ✓ | | |
| Claim submission | | | | | | ✓ | | |
| System maintenance | | | | | | | ✓ | |
| User management | | | | | | | ✓ | |
| Policy approval | | | | | | | | ✓ |
| Staff management | | | | | | | | ✓ |

**Legend**: ✓ = Primary responsibility; ✓* = Secondary (requires approval)

---

## ESCALATION PATHS

### Clinical Issues

```
Resident/Nurse Issue
    ↓
Consultant Review
    ↓
Department Head (if unresolved)
    ↓
Hospital Administration (if critical)
```

### Administrative Issues

```
Staff Member Issue
    ↓
Immediate Supervisor
    ↓
Department Head
    ↓
Hospital Administration (if unresolved)
```

### System Issues

```
User Issue
    ↓
IT Administrator
    ↓
Backup IT Support (if unavailable)
    ↓
External Vendor (if critical)
```

### Patient Safety Issues

```
Staff Member Identifies Issue
    ↓
Immediate Supervisor
    ↓
Department Head
    ↓
Hospital Administration
    ↓
Regulatory Body (if required)
```

---

## SIGN-OFF

This Role Responsibility Matrix is approved and effective as of the date below.

**Department Head**: ________________________  
**Signature**: ________________________  
**Date**: ________________________

**IT Administrator**: ________________________  
**Signature**: ________________________  
**Date**: ________________________

---

**Document Version**: 1.0  
**Last Updated**: February 2026  
**Next Review**: August 2026

