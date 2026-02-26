---
title: OpenEyes PH
draft: false
tags: 
- openeyes
--- 

I've always wanted to use an Electronic Medical Record (EMR) made just for Ophthalmologists. Ophthalmologists have been used since training to draw or use pictures to document the findings as the adage is ever so true in Ophthalmology that *"a picture is worth a thousand words"*

# OpenEyes
![OpenEyes Logo|200](https://raw.githubusercontent.com/openeyes/openeyes.github.io/master/img/logo.png)
[OpenEyes](https://github.com/appertafoundation/openeyes) is an open-source EMR created with the ophthalmologist in mind, allowing for rapid entry of data, while providing interactive illustrations which are adapted to the way eye doctors document their findings.
It is [[OpenEyes Features|highly configurable]] and has been actively utilized in the UK for more than a decade. It is consistently been updated by it's maintainer, Apperta Foundation. 

One challenge though is that OpenEyes is configured for the UK NHS and needs some code changes to reflect the differences and how we operate here in the Philippines. I'm listing down though the [[OpenEyes NHS Concepts|various concepts]] that are in OpenEyes that are unique to the NHS and needs further explanation to identify the Philippine equivalent.


> [!tldr] Target Goal
> Adaptation of OpenEyes to the Philippine healthcare system, which means registering OpenEyesPH as a registered EMR with PhilHealth for reimbursements.

## Open Invitation
I am no software developer. While I have aspired to be one, I have neither the energy or time to reverse engineer the source code on my own. I am posting my learning journey online in the hopes of getting more eyes on this project and helping it reach fruition.

### Current Challenges

| Challenge                                                                                                         | Context                                                                          |
| ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| OpenEyes was developed for the NHS                                                                                | The NHS system is vastly different from the current Philippine Healthcare System |
| OpenEyes, while open source, relies on Accredited Partners for implementation, support, and further customization | There are limited onboarding videos on the internet on using the system..        |

## Generative AI Assisted Outputs
Given the large scope of OpenEyes as a mature Ophthalmology-based EMR, I cannot manage everything alone. I'm asking assistance from AI LLMs.

> [!WARNING] DISCLAIMER
> These are Generative AI outputs created by [Manus](https://www.manus.im/app) 
> The contents of these outputs may be inaccurate. Viewers are strongly advised to personally verify.
#### Conceptual Differences
I've asked AI to identify the different organizational realities between the UK and Philippine healthcare systems:
- [[NHS Assumption Analysis]]
- [[NHS vs PH Context]]
#### Systems Evaluation
I have limited exposure to OpenEyes apart from this testbed so I'm delegating some evaluation to AI.
- [[Clinical Workflow Inventory]]
- [[CLINICIAN_ONBOARDING_MANUAL]]
- [[OpenEyes Clinic Setup Worksheet]]
- [[OpenEyes Onboarding Checklist]]
- [[Role Responsibility Matrix]]
- [[Technical Workflow Design]]
- [[Workflows Adapted to Philippine Setting]]