Lab: Security Baseline Gap Analysis (Microsoft Security Compliance Toolkit)

Domain: Security Compliance / Windows Server Hardening Date completed: August 2026 Tools used: Microsoft Security Compliance Toolkit (Policy Analyzer, LGPO)

Objective

Perform a gap analysis on a Windows Server to compare its current local security configuration against a Microsoft-recommended security baseline, in order to identify deviations before they become compliance or security risks.

Gap analysis is the process of comparing a system's current configuration against a template, baseline, security framework, or documented standard — to surface differences between the intended and actual configuration.

Steps Taken
Confirmed the server's Windows version - verified I was working on Windows Server 2019 (Version 1809, OS Build 17763.4377) before selecting a matching baseline.
Downloaded and installed the Microsoft Security Compliance Toolkit, which includes Policy Analyzer and LGPO for comparing local policy against Microsoft's published baselines.
Ran Policy Analyzer against the local Group Policy settings, loading the relevant Microsoft security baseline for comparison (371 policy items).
Ran "Compare to Effective State", which performs the actual gap analysis between the baseline security template and the current in-use values on the local operating system (393 items, with mismatches highlighted).
Screenshots
Step 1: Confirming the Windows Server version
<img width="906" height="526" alt="Screenshot 2026-08-07 214952" src="https://github.com/user-attachments/assets/9cba97d2-bb99-42d8-9854-cf0a7e63c78f" />
Step 2: Policy Analyzer — baseline 
<img width="1082" height="887" alt="Screenshot 2026-08-07 221711" src="https://github.com/user-attachments/assets/19f2d44e-1342-4b1b-88cb-a04bb6581c2b" />
Step 3: Compare to Effective State
<img width="1092" height="882" alt="Screenshot 2026-08-07 222339" src="https://github.com/user-attachments/assets/0ce2b78b-606e-4be6-b8d1-3e3a89772e72" />

Gap analysis doesn't force a system into compliance - it identifies where the current configuration deviates from a recommended framework, so those gaps can be reviewed and addressed deliberately. This kind of analysis is typically run when first adopting a security framework, after a significant amount of time has passed since the last review, or when meeting a new industry or legal compliance requirement.
Reference
Microsoft Security Compliance Toolkit
Related exam domains: CompTIA Security+ (baseline/hardening concepts)
