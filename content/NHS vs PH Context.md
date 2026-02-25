# NHS vs Philippine Healthcare Context: Key Differences

## NHS Ophthalmology Service Model (UK Context)

### Staffing Structure
- **Consultant ophthalmologists**: Lead clinicians, on-call rotas (1:5 to 1:10), specialized subspecialties
- **Specialty doctors**: Senior non-consultant doctors, support consultants
- **Residents/Trainees**: Structured training pathway, supervised procedures
- **Ophthalmic nurses**: Registered nurses with specialized training, expanded clinical roles
- **Ophthalmic technicians**: Trained technicians performing diagnostics (OCT, VF, biometry)
- **Orthoptists**: Vision specialists, visual field testing, orthoptic evaluation
- **Administrative staff**: Dedicated clerical, scheduling, billing support

### Infrastructure Assumptions
- **Reliable electricity and internet**: Continuous power supply, broadband connectivity
- **Dedicated IT support**: Hospital-provided IT infrastructure, servers, network management
- **Standardized equipment**: Consistent diagnostic equipment (OCT, visual field analyzers, biometry)
- **Electronic referral systems**: Integrated with GP practices and other hospitals (EeRS, SPARC)
- **Centralized data management**: Hospital-wide EMR systems (e.g., Cerner, Epic)
- **Regulated supply chains**: Reliable access to medications, implants, equipment

### Regulatory & Operational Context
- **National guidelines**: NICE guidelines, Royal College standards
- **Standardized pathways**: Evidence-based care pathways, clinical protocols
- **Performance metrics**: Waiting times, quality indicators, patient satisfaction
- **Accreditation**: CQC (Care Quality Commission) inspections
- **Funding model**: Fixed NHS budget allocation, activity-based commissioning
- **Medico-legal environment**: Strict liability, robust malpractice insurance
- **Referral system**: GP gatekeeping, structured referral pathways, triage systems
- **Patient expectations**: Informed consent, patient choice, transparency

### Workflow Assumptions
- **Appointment system**: Centralized scheduling, standardized wait times
- **Diagnostic workflow**: Parallel processing (VA, IOP, imaging in single visit)
- **Specialist availability**: Dedicated clinic days, predictable schedules
- **Surgical planning**: Standardized pre-operative workup, anesthesia clearance
- **Follow-up protocols**: Structured follow-up intervals, automated reminders
- **Billing**: Centralized, activity-based, automated coding
- **Communication**: Electronic correspondence, integrated messaging systems

---

## Philippine Healthcare Context (Tertiary Ophthalmology)

### Staffing Structure
- **Consultant ophthalmologists**: Limited number, often solo practitioners or small groups
- **Residents**: Variable training standards, may be self-funded or department-supported
- **Nurses**: May lack specialized ophthalmic training; multi-tasking across departments
- **Technicians**: Limited availability; often multi-skilled (not ophthalmology-specific)
- **Orthoptists**: Rare; functions often performed by nurses or technicians
- **Administrative staff**: Limited; often shared across departments
- **Barangay health workers**: Community-level health workers in satellite clinics

### Infrastructure Constraints
- **Intermittent electricity**: Power outages common; backup generators unreliable
- **Limited internet**: Intermittent connectivity; low bandwidth; high latency
- **Department-owned server**: No hospital IT support; minimal technical oversight
- **Mesh VPN access**: Personal workstations via mesh network; security concerns
- **Limited equipment**: Shared diagnostic equipment; older models; maintenance issues
- **No centralized EMR**: Paper-based or fragmented systems; limited interoperability
- **Unreliable supply chains**: Medication/implant shortages; delayed deliveries

### Regulatory & Operational Context
- **PhilHealth requirements**: Specific coding (ICD-10 + RVS), documentation standards for reimbursement
- **Variable standards**: Guidelines exist but implementation inconsistent across facilities
- **Limited oversight**: Minimal regulatory inspection; accreditation requirements less stringent
- **Funding model**: PhilHealth case rates + out-of-pocket payments; revenue uncertainty
- **Medico-legal environment**: Emerging liability concerns; limited malpractice insurance
- **Referral system**: Informal referral pathways; variable documentation
- **Patient expectations**: Cost-conscious; limited health literacy; variable informed consent

### Workflow Constraints
- **Scheduling challenges**: Limited clinic slots; high no-show rates; walk-in patients
- **Sequential diagnostics**: Limited parallel processing; patients may not complete workup in one visit
- **Specialist availability**: Consultant may not be present daily; residents conduct initial exams
- **Surgical planning**: Abbreviated pre-operative workup; cost constraints limit testing
- **Follow-up compliance**: Poor follow-up rates; patients lost to follow-up
- **Billing challenges**: Manual claim preparation; frequent PhilHealth rejections; delayed reimbursement
- **Communication**: Limited electronic communication; paper-based correspondence

---

## Key Differences Summary

| Aspect | NHS (UK) | Philippine Tertiary |
|--------|----------|-------------------|
| **Staffing** | Multidisciplinary, specialized | Limited, multi-tasking |
| **IT Infrastructure** | Centralized, reliable | Department-owned, unreliable |
| **Internet** | Continuous, high-speed | Intermittent, low-bandwidth |
| **Diagnostic Equipment** | Standardized, modern | Shared, older models |
| **Referral System** | Electronic, integrated | Paper-based, informal |
| **Billing** | Automated, activity-based | Manual, case-rate based |
| **Regulatory** | Strict, standardized | Variable, emerging |
| **Patient Flow** | Scheduled, predictable | Walk-in, unpredictable |
| **Follow-up** | Structured, high compliance | Informal, low compliance |
| **Funding** | Fixed budget | Fee-for-service + PhilHealth |

---

## Implications for OpenEyes Adaptation

### Critical Gaps to Address
1. **Offline-first architecture**: Must function without internet
2. **Lightweight infrastructure**: No hospital IT support; minimal server resources
3. **Simplified workflows**: Accommodate limited staffing and resources
4. **PhilHealth integration**: Mandatory for reimbursement
5. **Manual processes**: Support paper-based backup workflows
6. **Low-bandwidth design**: Minimize data transmission
7. **Resilience**: Handle equipment failures, power outages, staff absence

### Assumptions to Challenge
- Specialist availability (may not be present daily)
- Parallel diagnostic processing (may be sequential)
- Structured referral system (may be informal)
- Reliable follow-up (may be low compliance)
- Automated billing (must support manual processes)
- Electronic communication (must support paper backup)
- Standardized equipment (must be flexible)
- Continuous internet (must be offline-capable)
