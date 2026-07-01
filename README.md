\# 🛡️ Windows Privilege Escalation Investigation using Splunk



\## 📌 Overview



This project demonstrates how to detect and investigate a Windows privilege escalation scenario using Splunk Enterprise. Windows Security Event Logs were collected, analyzed, and correlated to identify suspicious activities such as failed logins, successful logins, user account creation, and administrator privilege assignment.



\---



\## 🎯 Objective



Detect and investigate a potential privilege escalation attack by analyzing Windows Security Event Logs in Splunk.



\---



\## 🏗️ Lab Environment



\- Windows 11 Home

\- Splunk Enterprise

\- Splunk Universal Forwarder

\- Windows Security Event Logs



\---



\## 📋 Attack Scenario



The following sequence of events was simulated:



1\. Multiple failed login attempts (Event ID 4625)

2\. Successful login (Event ID 4624)

3\. New local user account created (Event ID 4720)

4\. User added to the Administrators group (Event ID 4732)



\---



\## 🔍 Event IDs Used



| Event ID | Description |

|----------|-------------|

|4625|Failed Login|

|4624|Successful Login|

|4720|User Account Created|

|4732|User Added to Administrators Group|



\---



\## 🔎 Detection Query



```spl

index=\* (EventCode=4625 OR EventCode=4624 OR EventCode=4720 OR EventCode=4732)

| eval Activity=case(

EventCode=4625,"Failed Login",

EventCode=4624,"Successful Login",

EventCode=4720,"New User Created",

EventCode=4732,"Added to Administrators"

)

| table \_time EventCode Activity host

| sort \_time

```



\---



\## 🚨 Investigation Summary



The investigation identified multiple failed login attempts followed by a successful login. A new local user account (`backup\_admin`) was created and later added to the local Administrators group. This behavior represents a potential privilege escalation scenario and should be investigated immediately in a production environment.



\---



\## 🛠️ Skills Demonstrated



\- Splunk Search Processing Language (SPL)

\- Windows Security Event Analysis

\- Security Monitoring

\- Incident Investigation

\- Privilege Escalation Detection

\- Alert Creation

\- Root Cause Analysis

\- Incident Reporting



\---



\## 📚 MITRE ATT\&CK



\- Valid Accounts

\- Create Account

\- Account Manipulation



\---



\## 📷 Screenshots



Add screenshots of:



\- Windows Event Viewer

\- Splunk Search Results

\- Detection Query

\- Alert Configuration

\- Investigation Timeline



\---



\## 👨‍💻 Author



Likith Sunny



Final Year B.Tech (CSE - AI \& Data Science)



Aspiring SOC Analyst

