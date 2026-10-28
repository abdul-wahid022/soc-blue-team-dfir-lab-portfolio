<div align="center">

<img src="./images/bannernsm.png" alt="Network Security Monitoring" width="100%" />

<br><br>

<h1>Network Security Monitoring</h1>
<h3>Suricata, Zeek and RITA — From Alert to Hunt</h3>

<br>

<img src="https://img.shields.io/badge/LABS-1-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/DOMAIN-Network%20Security%20Monitoring-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/STATUS-COMPLETED-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />

<br><br>

<a href="#overview"><b>Overview</b></a> &nbsp;·&nbsp;
<a href="#labs"><b>Labs</b></a> &nbsp;·&nbsp;
<a href="#detection-workflow"><b>Workflow</b></a> &nbsp;·&nbsp;
<a href="../README.md"><b>Back</b></a>

</div>

<br>

---

## Overview

This section builds an integrated NSM stack. Suricata supplies signature alerts, Zeek supplies deep network metadata and RITA turns that metadata into behavioural hunting leads such as beacons and exploded DNS.

<br>

## Labs

<table>
<tr><th>#</th><th>Module</th><th>Focus</th><th>Core Tools</th></tr>
<tr><td>M03</td><td><a href="./M03-Integrated-NSM-and-Threat-Hunting/">Integrated NSM &amp; Threat Hunting</a></td><td>Suricata + Zeek + RITA — Signature Detection, Network Metadata &amp; Behavioural Hunting</td><td><code>Suricata</code> <code>Zeek</code> <code>RITA (rita-legacy)</code></td></tr>
</table>

<br>

## Detection Workflow

<table>
<tr><th>Stage</th><th>Tool</th><th>Role</th><th>Output</th></tr>
<tr><td>1. Alert</td><td><code>Suricata</code></td><td>Signature and custom-rule detection</td><td>fast.log / eve.json alerts</td></tr>
<tr><td>2. Context</td><td><code>Zeek</code></td><td>Connection, DNS and HTTP metadata</td><td>conn / dns / http logs (JSON)</td></tr>
<tr><td>3. Hunt</td><td><code>RITA</code></td><td>Behavioural analytics</td><td>Beacons, exploded DNS, long connections</td></tr>
<tr><td>4. Correlate</td><td>All</td><td>Link alert → metadata → behaviour</td><td>ATT&amp;CK-mapped findings</td></tr>
</table>

<br>

---

<div align="center">

<a href="../README.md"><b>← Back to Main Repository</b></a>

</div>
