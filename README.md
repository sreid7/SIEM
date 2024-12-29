# SIEM

**Elastic Stack**

Elastic Stack Literature https://www.elastic.co/guide/en/ecs/current/ecs-reference.html

Windows Port Error Codes for Elastic Search https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=4625

**WINDOWS RESEARCH WITHIN THE ELASTIC SIEM**

1. event.code:4625 
-This Windows event code is associated with failed login attempts in a Windows operating system.

2. event.code:4625 AND user.name: admin*
-The query identifies the number of failed login attempts (Event ID 4625) for accounts that start with "admin."

3. event.code:4625 AND winlog.event_data.SubStatus:0xC0000072 
-A SubStatus value of 0xC0000072 inside a 4625 Windows event log indicates that the account is currently disabled.

4. event.code:4625 AND winlog.event_data.SubStatus:0xC0000072 AND @timestamp >= "2023-03-03T00:00:00.000Z" AND @timestamp <= "2023-03-06T23:59:59.999Z"
-By using this query, SOC analysts can identify failed login attempts against disabled accounts that took place between March 3rd 2023 and March 6th 2023.
------------------------------------

When creating an SOP and documenting alert handling, consider the following:

-process.name
-process.parent.name
-event.action
-machine where the alert was detected
-user associated with the machine
-user activity within +/- 2 days of the alert's generation

After gathering this information, defenders should engage with the user and examine the user's machine to analyze system logs, antivirus logs, and proxy logs from the SIEM for full visibility.
The SOC team should document all the above points, along with the Incident Response Plan, so that Incident Handlers can reference them during analysis.
