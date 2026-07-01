\# Incident Report



\## Incident Details



\- Incident ID: INC-0001

\- Incident Name: Windows Privilege Escalation Investigation

\- Severity: High

\- Status: Closed (Lab Simulation)

\- Analyst: Likith Sunny



\---



\## Incident Summary



Multiple failed login attempts were detected on a Windows system. After a successful login, a new local user account named `backup\_admin` was created. The account was then added to the local Administrators group. This sequence of events indicates a potential privilege escalation scenario.



\---



\## Timeline



| Time | Event ID | Description |

|------|----------|-------------|

|10:36|4625|Multiple Failed Login Attempts|

|10:38|4624|Successful Login|

|10:52|4720|New User Created|

|11:00|4732|User Added to Administrators|



\---



\## Evidence



\- Event ID 4625 – Failed Login

\- Event ID 4624 – Successful Login

\- Event ID 4720 – New Local User Created

\- Event ID 4732 – User Added to Local Administrators Group



\---



\## Root Cause



A privileged account manually created a new local user (`backup\_admin`) and added it to the Administrators group as part of this lab simulation.



\---



\## Recommendations



\- Enable account lockout policies.

\- Monitor new user account creation.

\- Monitor administrator group membership changes.

\- Review privileged account activity regularly.

\- Enable email alerts for privilege escalation events.



\---



\## Conclusion



The investigation identified a sequence of events consistent with a privilege escalation scenario. Although this was intentionally performed in a lab environment, similar activity in a production environment should be investigated immediately.

