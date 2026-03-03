# Access Monitor Pro
### Advanced Security Analytics & Compliance Dashboard
**Developed by Impressico Business Solution**

---

## Overview

Access Monitor Pro is a comprehensive, AI-powered security monitoring and compliance dashboard built natively on Snowflake. It gives security teams, data engineers, and compliance officers complete visibility into their Snowflake environment — covering role management, user activity, login tracking, IP monitoring, privilege auditing, and dormant account detection — all in one place, with zero data leaving your account.

---


## Navigation & Filters

The sidebar provides the following controls:

**Date Range** — Filter all reports by Last 7 days, Last 30 days, Last 90 days, or Last 1 year.

**Include Deleted Objects** — Toggle to include deleted users and roles in reports. Useful for historical audits.

**Section Categories** — Choose from Role Management, User Management, Security Monitoring, or Analytics & Reports.

**Search** — Filter results within any section using a keyword search.

---

## 🎭 Role Management

### Role Privileges Audit
Complete audit of all privileges assigned to every role in your Snowflake account. Helps identify over-privileged roles and supports least-privilege enforcement.

### All Defined Roles
Full list of every role defined in your account including system roles and custom roles, with creation dates and ownership information.

### Role Hierarchy
Visualizes parent-child role relationships and inheritance chains. Understand how privileges flow across your role structure.

### Roles Without Privileges
Identifies roles that have no privileges assigned. These are candidates for cleanup to reduce role sprawl.

### Role Chart (AI-Powered)
The Role Chart uses AI to automatically analyze each role's privileges and classify it by category, purpose, and responsibilities. Outputs a visual pie chart showing role category distribution across your entire account. Categories include Admin, Read-Only, Data Engineering, Analytics, and more — generated automatically without any manual tagging.

### Orphaned Roles
Detects roles that are not assigned to any user or parent role. Orphaned roles represent security gaps and cleanup opportunities.

### Duplicate Roles Detection
Identifies roles with identical or heavily overlapping privilege sets. Duplicate roles create confusion and increase audit complexity.

---

## 👥 User Management

### User Overview
Complete list of all Snowflake users with account status, creation date, last login, MFA status, default role, and expiration details.

### Roles Assigned to Each User
Shows every role assigned to every user. Helps identify users with excessive role assignments.

### Privileges Directly Granted to Users
Audits privileges granted directly to users rather than through roles. Direct grants bypass role-based access control and are a compliance risk.

### Users With OWNERSHIP Privileges
Identifies users who hold OWNERSHIP privileges over database objects. Ownership grants full control and should be tightly managed.

### High-Privilege Role Assignments
Flags all users assigned to ACCOUNTADMIN, SECURITYADMIN, or SYSADMIN roles. These are the most powerful roles in Snowflake and should have minimal membership.

### Dormant Account Management
Read-only monitoring view that categorizes all user accounts by activity level and risk. Helps identify accounts that should be reviewed, disabled, or deleted.

**Dormancy Categories:**

**Delete Candidate** — User has been inactive for 120 or more days. Recommended action is to review and drop the account.

**Disable Candidate** — User has been inactive for 90 or more days. Recommended action is to review and disable the account.

**Monitor** — User has been inactive for 1 or more days. No immediate action required but should be watched.

**Active** — User is recently active. No action needed.

**Already Disabled** — Account has already been disabled.

**Risk Levels:**

**High Risk** — User holds ACCOUNTADMIN or SYSADMIN role.

**Medium Risk** — User holds SECURITYADMIN role or has 5 or more roles assigned.

**Low Risk** — User has at least one role assigned.

**No Risk** — User has no roles assigned.

For each dormant account the app surfaces a suggested SQL command that an ACCOUNTADMIN can copy and run outside of the app:

To disable a user:
```sql
ALTER USER "<username>" SET DISABLED = TRUE;
```

To drop a user:
```sql
DROP USER IF EXISTS "<username>";
```

Note: This app is a monitoring tool only. No user actions are performed by the app.

---

## 🔒 Security Monitoring

### Login History
Full audit trail of all login activity across your Snowflake account. Filter by date range to investigate specific time windows.

### Recent Failed Login Attempts
Real-time tracking of failed authentication attempts. High volumes of failures may indicate brute force attacks or misconfigured integrations.

### Users Without MFA Enabled
Identifies all user accounts that do not have multi-factor authentication enabled. These accounts are at higher risk of unauthorized access.

### Password Policy Compliance
Reviews user accounts against your password policy settings. Flags accounts with weak or non-compliant password configurations.

### Session Duration Analysis
Analyzes the length of user sessions. Unusually long or short sessions can indicate automation, shared credentials, or suspicious behavior.

### IP Address Analysis (AI-Powered)
Tracks every IP address that has accessed your Snowflake account. Helps identify:
- Unusual or unexpected login locations
- Unauthorized access attempts from unknown IPs
- Geographic access patterns and anomalies
- Suspicious IPs that may warrant investigation or blocking

---

## 📊 Analytics & Reports

### Privilege Usage Analytics
Analyzes how privileges across your account are actually being used versus what has been granted. Identifies unused privileges that can be revoked.

### Role Effectiveness Report
Measures how effectively each role is being utilized. Roles with low utilization may be candidates for consolidation or removal.

### Access Pattern Analysis
Identifies trends and anomalies in how users are accessing your Snowflake environment. Useful for detecting unusual behavior.

### Compliance Summary
Generates a high-level compliance report covering MFA adoption, privilege distribution, dormant accounts, and policy adherence. Ready for export and use in audits.

### Role Modification History
Full audit trail of all changes made to roles over time — including grants, revocations, and ownership transfers.

### Who Granted Which Role
Shows exactly who granted each role assignment and when. Essential for access governance and audit investigations.

### Object Privileges by Role
Detailed breakdown of all object-level privileges held by each role. Supports data access reviews and least-privilege audits.

### All Role Grants
Complete view of every role grant in the account, including grant timestamps and granting users.

---

## AI-Powered Features

### Role Chart
Automatically analyzes and categorizes every role in your Snowflake account using AI. Outputs structured data including category, purpose, and a list of responsibilities for each role. Accompanied by a visual pie chart showing the distribution of role categories across your account.

### IP Address Analysis
Automatically surfaces access patterns from login history and flags IP addresses that may be unusual or unauthorized. Helps security teams quickly identify which locations are accessing their Snowflake environment.

---

## Excel Export

Every section in the app includes a Download as Excel button. Reports are exported with all visible columns and can be used for offline analysis, governance reviews, or sharing with stakeholders.

---

## Troubleshooting

**No data returned?**
- Verify that IMPORTED PRIVILEGES ON SNOWFLAKE DB has been approved in the Permissions tab
- Try adjusting the Date Range filter to a wider range such as Last 90 days or Last 1 year
- Enable the Include Deleted Objects toggle to include historical records
- Ensure the role running the app has access to SNOWFLAKE.ACCOUNT_USAGE views

**Error executing query?**
- Check the Permissions tab to confirm all required privileges are granted
- Some views in SNOWFLAKE.ACCOUNT_USAGE may have a data latency of up to 2 hours
- Verify your Snowflake account has the ACCOUNT_USAGE share enabled

---

## Data Privacy & Security

Access Monitor Pro runs entirely within your Snowflake account. Your data never leaves your environment. There are no external API calls, no third-party data sharing, and no telemetry. All queries are executed against your own SNOWFLAKE.ACCOUNT_USAGE views.

---

## Support

Support Link: https://www.impressico.com/contact-us/
Email: info@impressico.com
Website: www.impressico.com

---

## About Impressico Business Solution

Impressico Business Solution is a technology company specializing in data analytics, cloud solutions, and enterprise application development. We build intelligent tools that help organizations gain deeper insights from their data while maintaining the highest standards of security and compliance.
# Access-Monitor-Pro
