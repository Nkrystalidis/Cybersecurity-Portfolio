# Linux Command Line: Security Log Analysis & IAM Auditing

## Scenario
As a security analyst, I was tasked with investigating server logs for potential security breaches and auditing Identity and Access Management (IAM) reports. The objective was to identify unauthorized access attempts and verify user account additions and deletions across different quarters.

## Task
Utilize the Linux command-line interface (Bash) to navigate the file system, filter directory contents, and extract specific security events from raw text files and server logs.

## Action
- Navigated the Linux file system using `cd` and `ls` to locate targeted security logs and quarterly user reports.
- Executed the `grep` command to parse `server_logs.txt`, successfully extracting critical security events such as multiple "incorrect password" and "unauthorized access" attempts.
- Utilized piping (`ls | grep`) to efficiently filter directory contents and isolate specific quarterly reports (e.g., Q1 and Q4 access files).
- Conducted an IAM audit by using `grep` to search inside text files, verifying the deletion of a specific user account (`jhill`) and identifying all new hires added to the "Human Resources" department.

## Outcome
Successfully extracted actionable intelligence from raw log files using core Linux commands. This exercise demonstrated proficiency in using the CLI for rapid security incident investigation, log parsing, and user access auditing without relying on Graphical User Interfaces (GUIs).
