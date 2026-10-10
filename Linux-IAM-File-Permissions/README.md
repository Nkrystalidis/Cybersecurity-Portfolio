# Linux System Administration: IAM & File Permissions

## Scenario
As a security analyst, I was responsible for auditing and managing file permissions for a research team's project directory (`/home/researcher2/projects`). The objective was to enforce the Principle of Least Privilege by ensuring that only authorized users and group members had appropriate read, write, and execute access to critical files and directories.

## Task
Utilize Linux command-line tools to inspect current file permissions (including hidden files), identify unauthorized access levels, and modify user, group, and other permissions to align with the organization's strict authorization policies.

## Action
- Executed `ls -la` to list all directory contents, successfully uncovering hidden files (e.g., `.project_x.txt`) that required permission auditing.
- Utilized the `chmod` command with symbolic representation to systematically revoke unauthorized access. Examples include:
  - Removing write permissions for "others" (`chmod o-w`).
  - Restricting read permissions for the "group" (`chmod g-r`).
  - Applying complex, multi-level permission changes in a single command (`chmod u-w,g+r,g-w`).
- Audited and secured the `drafts` directory by removing excessive permissions to prevent unauthorized horizontal access across the research team.

## Outcome
Successfully locked down the project directory and mitigated potential insider threats or unauthorized data modification. This project demonstrates practical proficiency in Linux Identity and Access Management (IAM), file system security, and command-line troubleshooting.
