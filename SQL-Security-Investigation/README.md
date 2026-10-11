# SQL Security Investigation: Analyzing Login Attempts

## Scenario
As a security analyst, I was tasked with investigating potential security incidents within the organization's network. The objective was to query the organization's database to identify unusual login activity, potential unauthorized access attempts, and systems requiring immediate security patching.

## Task
Utilize SQL queries within a MariaDB shell to extract, filter, and analyze security logs from the `log_in_attempts` and `machines` tables.

## Action
- Queried the `machines` table to retrieve hardware and operating system data (`device_id`, `operating_system`, `OS_patch_date`) to identify vulnerabilities and unpatched devices.
- Investigated the `log_in_attempts` table by selecting critical security fields (`username`, `login_date`, `login_time`, `country`, `ip_address`, `success`).
- Utilized the `ORDER BY` clause to sort login attempts chronologically by date and time, effectively creating a timeline of events.
- Identified anomalous behavioral patterns, specifically multiple consecutive failed login attempts (`success = 0`) occurring during after-hours, indicating a potential brute-force attack or unauthorized access attempt.

## Outcome
Successfully extracted actionable security intelligence from raw database tables. This project demonstrates practical proficiency in using SQL for incident response, log analysis, and threat hunting.
