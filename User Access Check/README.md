# AWS – Terminated User Access Verification (AWS Identity Store)
## Summary

Access reviews for terminated users are a high-risk, high-effort control in most organizations.
They are often manual, fragmented across systems, and performed reactively during audits.

This solution provides a single, repeatable check to verify whether terminated users still exist in AWS Identity Store, enabling faster access reviews, reduced audit effort, and improved assurance.

The tool is designed for security, GRC, IAM, and audit teams who need clear, defensible evidence without relying on screenshots, spreadsheets, or manual AWS console checks.

### The Problem This Solves
Common challenges in access reviews

- Termination lists come from HR, but verification across AWS is manual
- Reviewers must log into AWS, search users one by one, and document results
- Screenshots are inconsistent and not reproducible
- SSO sessions expire, causing unreliable automation
- Audit evidence is scattered, subjective, and time-consuming to re-create

### Risk impact

- Delayed or incomplete removal of access
- Weak evidence during ISO 27001 / SOC 2 / internal audits
- High operational overhead every quarter


### The Approach

This solution creates a single source of truth for terminated user verification:

- Input: a simple list of terminated user emails
- Output: a clear, human-readable access status from AWS Identity Store
- Execution: one-click, repeatable, and auditable

No AWS console navigation.
No spreadsheets.
No guesswork.

### How It Works (High Level)

** Termination input

- Terminated users are listed in emails.txt (one email per line)
- No script changes are required between runs

** Authenticated execution

- Uses AWS SSO with a pinned profile
- Automatically fails fast if authentication is invalid
- Ensures results are always generated using an authenticated identity

** Identity Store verification

- Retrieves users from AWS Identity Store
- Matches terminated emails against existing identities

** Output

- Displays results directly in the console:

  Total terminated users provided
  Users still present in AWS Identity Store
  Users not found (expected state)
  Includes date and time of execution
  Clear separation of FOUND vs NOT FOUND


EXAMPLE OUTPUT
========================================
AWS Access Check - Terminated Users
========================================

Run at: 2026-01-22 15:04:12

=== CHECK RESULT ===
Terminated provided: 11
Terminated found in Identity Store: 1
Terminated not found in Identity Store: 10

== FOUND ==
user1@company.com -> jdoe(uid=abcd1234)

== NOT FOUND ==
user2@company.com
user3@company.com
...

========================================
Check completed.
========================================


| Framework      | Control Objective                        |
| -------------- | ---------------------------------------- |
| ISO 27001      | A.5.18 – Access rights removal           |
| SOC 2          | CC6.2 – Timely removal of logical access |
| NIST CSF       | PR.AC-4 – Access permissions managed     |
| Internal Audit | User de-provisioning verification        |


### Who This Is For

- GRC professionals conducting access reviews
- IAM teams validating de-provisioning
- Internal and external auditors
- Security teams reducing manual access verification effort
