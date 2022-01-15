# Project-2
RED TEAM VS BLUE TEAM
### Project-2: Red vs Blue


In our second project I worked in a Red Team vs Blue Team scenario, where I played the role of both pentester and SOC analyst.

As the red team I attacked a vulnerable VM within our environment, ultimately gaining root access to the machine. As the Blue Team, I used Kibana to review logs taken during the attack, using those logs to extract hard data and visulizations for our report.

Then I interpreted the log data to suggest mitigation strategies for each exploit that I successfully performed.


### Project Objectives

This project will apply the knowledge and use of the following skills and tools:

- Penetration testing with kali Linux.
- Log and incident analysis with Kibana.
- System hardening and configuration.
- Reporting, documentation, and communication.


**The technical skills of this project were performed in a lab environment located in Windows Azure Lab Services.**


## Red Team

Before performing the attack it was essential to setup the backend logs to capture the attack data.

<details>
    <summary>Click hear to see beats and commands used to set up Kibana.</summary>
  <br>

**Filebeat**
- `filebeat modules enable apache`
- `filebeat setup`
  
**Metricbeat**
- `metricbeat modules enable apache`
- `metricbeat setup`
  
**Packetbeat**
- `packetbeat setup`
  
**Restarting to ensure they working and operational**
- `systemctl restart filebeat`
- `systemctl restart metricbeat`
- `systemctl restart packetbeat`
  
</details>

<br>

**Red Team Instructions**

1. Discover the IP address of the Linux web server.
2. Locate the hidden directory on the web server.
3. Brute force the password for the hidden directory using Hydra.
4. Break the hashed password with the Crack Station website or John the Ripper.
5. Connect to the server via WebDAV.
6. Upload a PHP reverse shell payload.
7. Execute payload to open up a meterpreter session.
8. Find and capture the flag.


## Blue Team

**Blue Team Instructions**

Using Kibana to analyse logs taken during the Red Team attack. The data will be used to develop ideas for new alerts that can improve monitoring.

Even though I already know what I did to exploit the target, analysing logs is still valuable. It teaches:
- What your attack looks like from a defender's perspective.
- How stealthy or detectable your tactics are.
- Which kinds of alarms and alerts SOC and Incident Response professionals can use to spot these types of attacks while they occur, rather than after.

**Creating Dashboards**

Using the Dashboards I added the following reports:
- `HTTP status codes for the top queries [Packetbeat] ECS`
- `Top 10 HTTP requests [Packetbeat] ECS`
- `Network Traffic Between Hosts [Packetbeat Flows] ECS`
- `Top Hosts Creating Traffic [Packetbeat Flows] ECS`
- `Connections over time [Packetbeat Flows] ECS`
- `HTTP error codes [Packetbeat] ECS`
- `Errors vs successful transactions [Packetbeat] ECS`
- `HTTP Transactions [Packetbeat] ECS`

Using the search queries in the Discover screen with packetbeat I was tasked with the following:
1. Identify the offensive traffic.
2. Find the request for the hidden directory.
3. Identify the brute force attack.
4. Find the WebDAV connection.
5. Identify the reverse shell and meterpreter traffic.


### Please view the Presentation to view the culmination of my results.
