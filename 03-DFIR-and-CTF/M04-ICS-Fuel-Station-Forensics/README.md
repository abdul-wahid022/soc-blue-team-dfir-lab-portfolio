<div align="center">

<img src="./images/cover.png" alt="ICS Fuel Station Forensics" width="100%" />

<br><br>

<h1>ICS Fuel Station Forensics</h1>
<h3>PCAP Analysis of an Automatic Tank Gauge (ATG) Compromise</h3>

<br>

<img src="https://img.shields.io/badge/MODULE-M04-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/DOMAIN-ICS%20%C2%B7%20PCAP-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
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
<tr><td>Objective</td><td>Analyse captured traffic from a compromised fuel-site ATG to reconstruct attacker activity and extract indicators</td></tr>
<tr><td>Evidence</td><td>Single PCAP analysed in Wireshark</td></tr>
<tr><td>Protocol focus</td><td>Veeder-Root style ATG communications on a non-standard TCP port</td></tr>
<tr><td>Disclosure</td><td>Challenge-specific answers are intentionally omitted — methodology only</td></tr>
</table>

<br>

## Key Findings

<table>
<tr><th>Area</th><th>Result</th></tr>
<tr><td>Connection analysis</td><td>Used SYN / SYN-ACK display filters to find first contact, the initiating host and responding services</td></tr>
<tr><td>Service discovery</td><td>Identified a standard service port plus a non-standard ICS port carrying the ATG protocol</td></tr>
<tr><td>Protocol identification</td><td>Confirmed the ICS protocol via dissector output and payload inspection</td></tr>
<tr><td>Stream analysis</td><td><code>Follow TCP Stream</code> with payload-length filters to isolate data-rich ATG reports and readable operator/status fields</td></tr>
<tr><td>Host identification</td><td>DHCP Option 12 used to tie traffic to an asset hostname</td></tr>
<tr><td>Threat context</td><td>Extortion-style content embedded in the ICS channel; contact indicators extracted for TI (not published here)</td></tr>
</table>

<br>

## Evidence

<!-- Source: Q1 · Initial SYN filter (PDF pg. 5) -->
<p align="center"><img src="./images/wireshark-syn-only-filter-first-contact.png" alt="Display filter isolating connection-initiation packets." width="85%" /></p>
<p align="center"><sub>Display filter isolating connection-initiation packets.</sub></p>

<!-- Source: Q6 · ICS protocol filter (PDF pg. 11) -->
<p align="center"><img src="./images/wireshark-port-10001-ics-traffic.png" alt="Traffic on the identified ICS port in the packet list." width="85%" /></p>
<p align="center"><sub>Traffic on the identified ICS port in the packet list.</sub></p>

<!-- Source: Q8 · Payload-length filter (PDF pg. 15) -->
<p align="center"><img src="./images/wireshark-large-payload-filter.png" alt="Filtering for data-rich ATG report packets." width="85%" /></p>
<p align="center"><sub>Filtering for data-rich ATG report packets.</sub></p>

<!-- Source: Q15 · DHCP analysis (PDF pg. 23) -->
<p align="center"><img src="./images/wireshark-dhcp-hostname-option12.png" alt="DHCP Option 12 used for host identification." width="85%" /></p>
<p align="center"><sub>DHCP Option 12 used for host identification.</sub></p>

<br>

## Tools

<table>
<tr><th>Tool</th><th>Purpose</th></tr>
<tr><td><code>Wireshark</code></td><td>PCAP analysis, display filters, Follow TCP Stream</td></tr>
<tr><td><code>TCP/IP handshake analysis</code></td><td>SYN / SYN-ACK reasoning</td></tr>
<tr><td><code>DHCP analysis</code></td><td>Asset identification</td></tr>
</table>

<br>

## Full Report

<a href="Lab-Report.pdf"><img src="https://img.shields.io/badge/FULL%20REPORT-PDF-0d1117?style=for-the-badge&logo=adobeacrobatreader&logoColor=white&color=00b4d8" /></a>

<br>

---

<div align="center">

<a href="../README.md"><b>← Back to DFIR &amp; CTF</b></a> &nbsp;·&nbsp;
<a href="../../README.md"><b>← Back to Main Repository</b></a>

</div>
