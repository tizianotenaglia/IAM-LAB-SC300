# Module 1.1 – Domain population via Bulk create

## What I did

Populated the GrapeTech tenant with 15 internal member users via the Bulk create feature in 
Microsoft Entra ID, using a CSV file structured across multiple departments (HR, Operations, IT, 
Finance, Sales, and generic staff) to simulate a realistic small organization for testing 
Conditional Access, PIM, and Access Review scenarios later in the project.

## Steps

1. In Entra admin center → Users → All users, opened **Bulk operations** → **Bulk create (Preview)**.
2. Downloaded the official CSV template directly from the portal to ensure the correct column 
   headers and format.
3. Filled in the template with 15 users, each assigned a display name, UPN on the custom domain 
   (@grapetech.online), an initial password, account enabled status, job title, department, and 
   usage location (AU, consistent across all users since it only affects license eligibility, not 
   Conditional Access location logic).
4. Uploaded the completed CSV file and submitted the bulk create job.
5. Verified the result in **All users**: 16 users now listed (15 newly created + my own admin account).

## Screenshots

![Bulk create panel in Entra](imgs/bulk-invite.png)
*Bulk create users panel in Entra admin center, showing the 3-step process: download template, edit CSV, upload file.*

![Completed CSV file (passwords redacted)](imgs/aaa.png)
*Final CSV file with 15 users across HR, Operations, IT, Finance, Sales and generic Employee roles. 
Passwords shown as REDACTED here for security — the real file used a shared initial password that 
each user is required to change on first sign-in.*

![Populated tenant - All users list](imgs/populated.png)
*All users view in Entra confirming successful creation: 16 users found, matching the 15 new accounts plus the original admin account.*

## Why include a disabled account

One of the 15 users, Brenda Merenda, was deliberately created with **Account enabled = false** 
(Account status: Disabled), instead of matching the rest of the batch.

Including at least one disabled account in the population is useful for a realistic lab environment 
for a few reasons:

- It simulates a common real-world scenario: an offboarded or on-leave employee, whose account is 
  disabled rather than deleted, preserving audit history, group memberships, and licensing 
  assignments for compliance purposes.
- It allows testing that Conditional Access and sign-in flows correctly block authentication for 
  disabled accounts, even if the account otherwise has valid credentials.
- It provides a concrete example for Access Reviews and stale-account governance scenarios later in 
  the project, where reviewers need to identify and act on accounts that should no longer have 
  active access.
- It confirms that a disabled account still shows up in reporting (Users list, Sign-in logs, Bulk 
  operation results) but cannot authenticate — an important distinction from account deletion.

![Disabled account status](imgs/disabled.png)
*Brenda Merenda's user profile in Entra, showing Account status: Disabled under "My Feed", confirming the account was created disabled as intended.*