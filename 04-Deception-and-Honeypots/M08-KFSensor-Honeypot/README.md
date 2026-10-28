<div align="center">

<img src="./images/cover.png" alt="KFSensor Honeypot" width="100%" />

<br><br>

<h1>KFSensor Honeypot</h1>
<h3>Cyber Counterintelligence Data Collection with a Windows Honeypot</h3>

<br>

<img src="https://img.shields.io/badge/MODULE-M08-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/DOMAIN-Honeypot-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/STATUS-COMPLETED-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/ENVIRONMENT-ISOLATED%20LAB-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />

<br><br>

<a href="#overview"><b>Overview</b></a> &nbsp;·&nbsp;
<a href="#key-findings"><b>Findings</b></a> &nbsp;·&nbsp;
<a href="#evidence"><b>Evidence</b></a> &nbsp;·&nbsp;
<a href="#tools"><b>Tools</b></a> &nbsp;·&nbsp;
<a href="Lab-Report.pdf"><b>Full Report</b></a> &nbsp;·&nbsp;
<a href="../README.md"><b>Back</b></a>

</div>

<br>

---

## Overview

<table>
<tr><td>Objective</td><td>Deploy a honeypot and capture reconnaissance activity as threat-intelligence data</td></tr>
<tr><td>Topology</td><td>Windows 10 VM (KFSensor) + Kali Linux VM (Zenmap) on an isolated lab network</td></tr>
<tr><td>Module</td><td>CTIA Module 04 — Data Collection and Processing</td></tr>
<tr><td>Technique</td><td>Decoy services, port-scan detection, attacker-source identification</td></tr>
</table>

<br>

## Key Findings

<table>
<tr><th>Area</th><th>Result</th></tr>
<tr><td>Deployment</td><td>KFSensor installed with WinPcap; native-service ports released so the sensor could monitor them directly</td></tr>
<tr><td>Baseline</td><td><code>netstat -an</code> confirmed the honeypot's listening ports</td></tr>
<tr><td>Attack simulation</td><td>Zenmap Intense Scan launched from Kali against the honeypot</td></tr>
<tr><td>Detection</td><td>Recent-activity flags raised on FTP, SSH, Telnet, SMTP, DNS, HTTP/HTTPS, MySQL, VNC and others, with the scanner identified as visitor</td></tr>
<tr><td>Hardening takeaways</td><td>Close unused ports, retire plaintext services (FTP/Telnet/VNC), feed honeypot logs to a SIEM and update firewall rules</td></tr>
</table>

<br>

## Evidence

<!-- Source: Task 2 (PDF pg. 6) -->
<p align="center"><img src="./images/kfsensor-setup-wizard-native-services.png" alt="Setup wizard native-services step." width="85%" /></p>
<p align="center"><sub>Setup wizard native-services step.</sub></p>

<!-- Source: Task 3 (PDF pg. 8) -->
<p align="center"><img src="./images/kfsensor-main-window-sensor-ports.png" alt="Main window listing sensor ports before the scan." width="85%" /></p>
<p align="center"><sub>Main window listing sensor ports before the scan.</sub></p>

<!-- Source: Task 4 (PDF pg. 9) -->
<p align="center"><img src="./images/netstat-listening-ports.png" alt="Command-line view of active listening ports." width="85%" /></p>
<p align="center"><sub>Command-line view of active listening ports.</sub></p>

<!-- Source: Task 5 (PDF pg. 11) -->
<p align="center"><img src="./images/zenmap-intense-scan-open-ports.png" alt="Zenmap results showing open ports on the honeypot." width="85%" /></p>
<p align="center"><sub>Zenmap results showing open ports on the honeypot.</sub></p>

<!-- Source: Task 6 (PDF pg. 12) -->
<p align="center"><img src="./images/kfsensor-recent-activity-detections.png" alt="KFSensor flagging recent activity across scanned services." width="85%" /></p>
<p align="center"><sub>KFSensor flagging recent activity across scanned services.</sub></p>

<br>

## Tools

<table>
<tr><th>Tool</th><th>Purpose</th></tr>
<tr><td><code>KFSensor Professional (trial)</code></td><td>Windows honeypot</td></tr>
<tr><td><code>WinPcap</code></td><td>Packet capture dependency</td></tr>
<tr><td><code>Zenmap / Nmap</code></td><td>Scan simulation</td></tr>
<tr><td><code>Command Prompt</code></td><td>netstat verification</td></tr>
</table>

<br>

## Full Report

<a href="Lab-Report.pdf"><img src="https://img.shields.io/badge/FULL%20REPORT-PDF-0d1117?style=for-the-badge&logo=adobeacrobatreader&logoColor=white&color=00b4d8" /></a>

<br>

---

<div align="center">

<a href="../README.md"><b>← Back to Deception &amp; Honeypots</b></a> &nbsp;·&nbsp;
<a href="../../README.md"><b>← Back to Main Repository</b></a>

</div>
