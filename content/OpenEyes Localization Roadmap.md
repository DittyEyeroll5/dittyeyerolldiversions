## Phase 0. Scope Definition:

^f95ce5

1. Subspecialty Coverage
	1. General Ophthalmology
    2. Retina and Vitreous
    3. Glaucoma
    4. External Disease and Cornea
    5. Pediatric Ophthalmology and Strabismus
    6. Orbit and Oculoplasty
    7. Neuro-Ophthalmology
    8. Uveitis
    9. Low Vision
    10. Refractive Surgery
    11. Ocular Genetics
    12. Ocular Pathology
    13. Ocular Oncology
2. Surgical Case Coverage
	1. Cataract surgeries
	    1. Adult Cataract
        2. Complex cataract surgeries
        3. Pediatric Cataract
	2. Retina Surgeries
    3. Glaucoma Surgeries
    4. Cornea Surgeries
    5. Strabismus Surgeries
    6. Orbit Surgeries
3. Health Insurance Coverage
	1. Philhealth - PRIORITY
    2. Co-pay options for out-of-pocket settlement (For later development for future implementations with free-standing ambulatory surgery clinics)
    3. HMO settlement (For later development for future implementations with free-standing ambulatory surgery clinics)

  

## Phase 1. System Evaluation

### A. Module Mapping

For mapping of

- Admin Modules
- Clinical modules
- Event Types
- Pathways
- Firm (Team) structures
- User Roles

### B. NHS Dependency Mapping

For mapping of NHS-specific terms used as dependencies in Modules

- NHS Number requirements
- SNOMED enforcement
- UK Referral Types
- Tariff Billing
- GP Integration
- National Audit Reporting

### C. Workflow Mapping

For mapping of:

- Clinical Outpatient Workflows
- - Outpatient Booking
    - Worklist Generation
    - Conflict Resolution - Outpatient Rescheduling
- Clinical Inpatient Workflows
- Surgical Booking
- - Conflict Resolution - Overbooking
    - Conflict Resolution - Time Extentsions
- Referral Documentation
- - Inter-departmental referral
    - Inter-hospital department referral
    - External referral

### D. Configuration Strategy

For configuration of mapped modules

- [ ] Firms
- [ ]  Sites (Clinics)
- [ ]  Subspecialties
- [ ] Event Templates
- [ ] Clinical Elements
- [ ] Roles & Permissions
- [ ] Pathways
- [ ] Worklists
- [ ] Operation Sequences
- [ ] Operation Sessions