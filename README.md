# cloud-posture-dashboard-pm-assignment

**Submitted by:** Shivani Tiwari  
**Role:** Product Management Trainee: AccuKnox  
**Interactive Figma Prototype:** [Open Prototype](https://www.figma.com/proto/Q4NwbaiTyb4Cs1gmvir083/Untitled?node-id=6-1193&p=f&t=pqaxJ2pDia38hZwQ-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1)  
**PDF Write-Up:** [View Full Submission PDF](./AccuKnox%20Product%20Management%20Trainee%20Assignment_%20Shivani%20Tiwari.pdf)

---

## Problem Statement
When a team manages multiple cloud accounts like Production, Development, and Testing, it gets hard to keep track of misconfigurations. Standard cloud consoles throw hundreds of alerts at you at once using heavy technical terms. Because everything looks urgent, something serious like a public S3 bucket in Production can easily get buried under minor warnings from a Testing account. I designed CloudGuard to bring alerts from different accounts into one place and explain what needs attention first in plain English.

## Target User
This is built for a developer, DevOps engineer, or startup founder who manages AWS or other cloud accounts for a small team without a dedicated security person. They understand basic cloud setups, but do not want to spend hours decoding security terms or risk breaking a live app by changing permissions blindly. They just want to know which account has a problem, why it matters, and what safe steps to take to fix it.

## Proposed Features and Screen Notes
My [Figma prototype](https://figma.com) walks through the complete 7-screen workflow from connecting an account to verifying a fix:

1. **Connect Cloud Account (Onboarding):** Lets users pick AWS, Azure, or GCP using safe read-only access without asking for passwords or secret keys so they trust the setup.
2. **Overview Dashboard:** Shows the overall security score (72/100), connected accounts, severity counts, and a "Fix these issues first" list at the top so users immediately see critical Production risks instead of digging through 24 alerts.
3. **Findings List:** A central table with search and filters (provider, account, severity, category, status) so engineers can hide Testing noise in one click and focus only on Production risks.
4. **Finding Details and Verification:** Explains what is happening and why it matters in plain English, adds a safety warning before making changes, provides a 5-step checklist with an Open AWS Console button, hides raw specs under a collapsed "Technical details" toggle, and ends with a "Verify issue" button.
5. **Cloud Accounts Management:** Displays all connected accounts, their last scan time, and simple options to reconnect, disconnect, or add another account.
6. **Live Scan Progress:** Shows real-time check progress (like "Checking 42 of 62") when a scan runs so users know the system is working.
7. **Workspace Settings:** Keeps basic scan preferences and team access controls simple and easy to manage.

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
