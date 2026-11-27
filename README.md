# cloud-posture-dashboard-pm-assignment

**Submitted by:** Shivani Tiwari  
**Role:** Product Management Trainee: AccuKnox  
**Interactive Figma Prototype:** [Open Prototype](https://www.figma.com/proto/Q4NwbaiTyb4Cs1gmvir083/Untitled?node-id=6-1193&p=f&t=pqaxJ2pDia38hZwQ-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1)  
**PDF Submission:** [View Full Write-Up PDF](./CloudGuard_Assignment.pdf) 

---

## Problem Statement
When a team manages multiple cloud accounts like Production, Development, and Testing, it gets hard to keep track of misconfigurations. Standard cloud consoles throw hundreds of alerts at you at once using heavy technical terms. Because everything looks urgent, something serious like a public S3 bucket in Production can easily get buried under minor warnings from a Testing account. I designed CloudGuard to bring alerts from different accounts into one place and explain what needs attention first in plain English.

## Target User
This is built for a developer, DevOps engineer, or startup founder who manages AWS or other cloud accounts for a small team without a dedicated security person. They understand basic cloud setups, but do not want to spend hours decoding security terms or risk breaking a live app by changing permissions blindly. They just want to know which account has a problem, why it matters, and what safe steps to take to fix it.

## Proposed Features and Screen Notes
While the [Figma prototype](https://www.figma.com/proto/Q4NwbaiTyb4Cs1gmvir083/Untitled?node-id=6-1193&p=f&t=pqaxJ2pDia38hZwQ-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1) also covers onboarding, connected accounts, and scan progress, the main workflow focuses on screens:

1. **Overview Dashboard**  
   This screen shows the overall security score (72/100), account status, issue counts by severity, and a "Fix these issues first" list at the top. I put critical Production issues right at the top so a user does not have to dig through 24 alerts just to figure out where to start.
2. **Findings List**  
   This is a central table where you can search and filter alerts by cloud provider, account, severity, category, and status. I added these filters so an engineer can hide Testing or Development noise in one click and look only at Production risks.
3. **Finding Details and Verification**  
   When you open an issue, it explains what is happening and why it matters in simple terms, along with a warning before you make changes. It gives a 5-step checklist, a button to open the AWS console, a collapsed section for raw technical details, and a "Verify issue" button. I hid the raw technical details by default so the screen does not feel overwhelming, added the warning so users do not accidentally lock down permissions and break their app, and added the verify button so they can check right away if their fix worked.

## Prioritization
For version 1, I focused on the overview screen, multi-account filters, and step-by-step fix guides with verification. Together, these help users see their overall risk, hide non-production noise, and fix issues safely. Clear explanations matter much more early on than adding extra charts or complicated settings. Version 1 should also use read-only cloud access and guide users through fixes instead of making automatic changes to their cloud setup.

## Success Metrics
* How long it takes a user to find and fix a critical Production issue after opening the dashboard.
* How many new users connect an account with read-only access and finish their first scan.
* How many users who open a fix guide actually complete the steps and pass the verification check.

## Bonus: Development Discussion Points
* **Start with one cloud:** Launch with AWS and a small list of common checks (like public S3 buckets or open ports) before adding Azure and GCP.
* **Safe account connection:** Have a conversation with the dev team about the simplest read-only setup, like a basic read-only IAM role, so users feel safe connecting their accounts.
* **Common data format:** Store findings from different accounts and regions in one consistent format so search and filters stay fast as alerts grow.
* **Scoring and priority rules:** Set simple rules combining criticality and environment (Production vs. Testing) to rank the "Fix these issues first" list and calculate the score.
* **Single-resource check:** Check with developers if the "Verify issue" button can test just that one specific resource through the cloud API instead of running a full account scan.
