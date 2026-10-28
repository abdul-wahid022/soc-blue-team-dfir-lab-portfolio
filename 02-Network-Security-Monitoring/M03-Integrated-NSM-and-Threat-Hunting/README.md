<div align="center">

<img src="./images/cover.png" alt="Integrated NSM &amp; Threat Hunting" width="100%" />

<br><br>

<h1>Integrated NSM &amp; Threat Hunting</h1>
<h3>Suricata + Zeek + RITA — Signature Detection, Network Metadata &amp; Behavioural Hunting</h3>

<br>

<img src="https://img.shields.io/badge/MODULE-M03-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/DOMAIN-NSM-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
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
<tr><td>Objective</td><td>Build a full NSM pipeline and validate it with simulated reconnaissance, beaconing and DNS-anomaly attacks</td></tr>
<tr><td>Topology</td><td>Ubuntu sensor (Suricata, Zeek, MongoDB, RITA) + Kali attacker on an isolated network</td></tr>
<tr><td>Workflow</td><td>Real-time alert (Suricata) → rich logging (Zeek) → behavioural hunting (RITA)</td></tr>
<tr><td>Modes</td><td>Suricata IDS and IPS (NFQUEUE) with custom local rules</td></tr>
</table>

<br>

## Key Findings

<table>
<tr><th>Area</th><th>Result</th></tr>
<tr><td>Suricata</td><td>Installed, rule-updated (Emerging Threats Open) and extended with custom rules for Nmap UA, SQLi patterns and Host-header policy; tested in IDS and IPS (drop) mode</td></tr>
<tr><td>Zeek</td><td>Compiled from source, standalone node, JSON logging enabled; conn/http/dns logs used for context</td></tr>
<tr><td>Port scan</td><td>2,100+ SYN-scan alerts correlated with many short-lived S0 connections in Zeek</td></tr>
<tr><td>DNS tunnelling</td><td>55 tunnelling-attempt alerts; RITA flagged exploded-DNS on two simulated C2 domains (35 and 40 subdomains)</td></tr>
<tr><td>Beaconing</td><td>RITA surfaced several beacon candidates, highest score 0.917</td></tr>
<tr><td>ATT&amp;CK mapping</td><td>T1071.001 · T1071.004 · T1573 · T1046 · T1595.001 · T1048.003</td></tr>
</table>

<br>

## Evidence

<!-- Source: Part 3 · Attack 1 Port Scan (PDF pg. 37) -->
<p align="center"><img src="./images/suricata-nmap-syn-scan-alerts.png" alt="Suricata fast.log showing SYN-scan alerts from the attacker host." width="85%" /></p>
<p align="center"><sub>Suricata fast.log showing SYN-scan alerts from the attacker host.</sub></p>

<!-- Source: Part 3 · Attack 1 Zeek view (PDF pg. 38) -->
<p align="center"><img src="./images/zeek-conn-log-s0-scan-pattern.png" alt="Zeek conn.log with many S0 connection states from the scan." width="85%" /></p>
<p align="center"><sub>Zeek conn.log with many S0 connection states from the scan.</sub></p>

<!-- Source: Part 3 · Attack 3 SQLi (PDF pg. 40) -->
<p align="center"><img src="./images/suricata-sqli-alert-detected.png" alt="Custom rule firing on a SQL-injection-style HTTP request." width="85%" /></p>
<p align="center"><sub>Custom rule firing on a SQL-injection-style HTTP request.</sub></p>

<!-- Source: Part 5 · RITA analysis (PDF pg. 52) -->
<p align="center"><img src="./images/rita-exploded-dns-and-beacons.png" alt="RITA exploded-DNS and beacon results from imported Zeek logs." width="85%" /></p>
<p align="center"><sub>RITA exploded-DNS and beacon results from imported Zeek logs.</sub></p>

<!-- Source: MITRE ATT&amp;CK Mapping (PDF pg. 54) -->
<p align="center"><img src="./images/nsm-mitre-attack-mapping-table.png" alt="Simulated attacks mapped to techniques and detecting tool." width="85%" /></p>
<p align="center"><sub>Simulated attacks mapped to techniques and detecting tool.</sub></p>

<br>

## Tools

<table>
<tr><th>Tool</th><th>Purpose</th></tr>
<tr><td><code>Suricata</code></td><td>Signature IDS/IPS</td></tr>
<tr><td><code>Zeek</code></td><td>Network metadata and forensics</td></tr>
<tr><td><code>RITA (rita-legacy)</code></td><td>Beacon, DNS and long-connection analytics</td></tr>
<tr><td><code>MongoDB (Docker)</code></td><td>RITA datastore</td></tr>
<tr><td><code>Nmap · curl</code></td><td>Attack and traffic simulation</td></tr>
</table>

<br>

## Full Report

<a href="Lab-Report.pdf"><img src="https://img.shields.io/badge/FULL%20REPORT-PDF-0d1117?style=for-the-badge&logo=adobeacrobatreader&logoColor=white&color=00b4d8" /></a>

<br>

---

<div align="center">

<a href="../README.md"><b>← Back to Network Security Monitoring</b></a> &nbsp;·&nbsp;
<a href="../../README.md"><b>← Back to Main Repository</b></a>

</div>
