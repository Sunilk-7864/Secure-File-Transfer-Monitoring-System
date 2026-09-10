# Project 1: Secure-File-Transfer-Monitoring-System

## Overview/ Description
This project focuses on developing a Secure File Transfer Monitoring System designed to ensure data confidentiality and track file movement across a system or network.<p>File transfers—both internal and external—pose significant risks including data leakage, unauthorized access, malware distribution, and insider misuse.</p>
<p>This Monitoring system provides:</p>
<p><li>File transfer logging</li></p>
<p><li>Unauthorizing file movement detection</li></p>
<p><li>File intigirti verification</li></p>

## Practical Motivation
Organizations face constant threats involving unauthorized file uploads/downloads, data theft, and malicious file tampering.

### Examples include:
<p><li>Employees copying sensitive data outside the organization</li></p>
<p><li>Malware modifying or replacing files</li></p>
<p><li>Unauthorized transfers via USB, network shares, or cloud sync tools</li></p>

### A monitoring system helps detect:
<p><li>Suspicious file transfers</li></p>
<p><li>Unauthorized data movement</li></p>
<p><li>Integrity validations</li></p>
<p><li>Potential exfiltration attempts</li></p>

## Project Objectives
<p><li>Log all file transfers performed on the system.</li></p> 
<p><li>Detect unauthorized movement of sensitive or restricted files.</li></p>
<p><li> Implement file integrity checks using hashing (SHA256/MD5).</li></p>
<p><li>Generate alerts on policy violations.</li></p>
<p><li>Produce detailed audit logs and security reports.</li></p>

## Practical Scope of the Project

### File Transfer Logging:
<p><li>Monitor file copy, move, delete, upload, download events.</li></p>
<p><li>Log timestamp, source path, destination path, user, and process name.</li></p>

### Unauthorized Movement
<p><li>Maintain a list of sensitive directories or restricted files.</li></p>
<p><li>Trigger alerts when such files are moved or accessed without permission.</li></p>
<p><li> Detect suspicious outbound transfers (USB, network shares, cloud folders).</li></p>

### File Integrity Checks:
<p><li>Calculate pre- and post-transfer hash values.</li></p>
<p><li>Detect tampering, corruption, or unauthorized modifications.</li></p>
<p><li>Highlight mismatches in integrity.</li></p>

### Reporting & Alert System:
<P><li>Generate logs of all file events</li></P>
<p><li>High light violation and suspicious transfers</li></p>
<p><li>Produce a final audit report summarizing activity</li></p>

## Tool & Technologies Used

### Programming languages:
<p><li>Python (recommended)</li></p>
<p><li>Python (optional)</li></p>

### Modules/tools:
<p><li>Word</li></p>
<p><li>Draw.io for architecture diagrams</li></p>

## Practical Techniques Implemented

### Security Techniques:
<p><li>File system activity monitoring</li></p>
<p><li>Tamper detection through hashing</li></p>
<p><li>Unauthorized access alerting</li></p>

### Blue Team Techniques:
<p><li>Detecting insider threats</li></p>
<p><li>Monitoring suspicious date </li></p>
<p><li>Monitorig suspicius</li></p>
<p><li>Identifying modified or replaced files</li></p>
<p><li>Strengthening data Loss prevention (DLP) strategies</li></p>
