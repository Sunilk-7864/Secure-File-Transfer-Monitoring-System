# Secure File Transfer Monitoring System

## Project Overview / Description
This project focuses on developing a Secure File Transfer Monitoring System designed to ensure data confidentiality and track file movement across a system or network. 

File transfers—both internal and external—pose significant risks including data leakage, unauthorized access, malware distribution, and insider misuse. 

This monitoring system Provides:
<p><li>File transfer logging</li></p>
<p><li>Unauthorized file movement detection</li></p>
<p><li>File integrity verification</li></p>

## Practical Motivation

Organizations continuously face security threats related to unauthorized file uploads and downloads, data theft, and malicious file modification. Sensitive organizational files may be copied, transferred, altered, or deleted without proper authorization, leading to data leakage and security incidents.

The Secure File Transfer Monitoring System is motivated by the need to monitor and detect suspicious file-related activities within an organization.

## Common Security Threats
<li>Sensitive Data Leakage: Employees or unauthorized users may copy confidential files outside the organization through email, USB devices, cloud storage, or other channels.</li>
<li>Malicious File Tampering: Attackers or malware may modify, replace, or delete important files without authorization.</li>
<li>Unauthorized File Transfers: Files may be transferred through network shares, removable storage devices, or cloud synchronization services without proper approval.</li>
<li>Data Exfiltration: Attackers may attempt to move sensitive information outside the organization's trusted environment.</li>
<li>Insider Threats: Authorized users may misuse their access privileges to copy or transfer confidential information.</li>
<li>Lack of Visibility: Without continuous monitoring, administrators may have difficulty identifying who accessed, modified, uploaded, downloaded, or transferred a particular file.</li>

## What the System Helps Detect

The proposed monitoring system provides an additional layer of security by monitoring file-transfer activities and maintaining relevant activity records. It helps identify:

<p><li>Suspicious file uploads and downloads</li></p>
<p><li>Unauthorized data movement</li></p>
<p><li>Abnormal file-transfer behavior</li></p>
<p><li>File integrity violations</li></p>
<p><li>Potential data-exfiltration attempts</li></p>
<p><li>Unauthorized file modifications or replacements</li></p>

## Importance of the System

A Secure File Transfer Monitoring System improves file visibility, accountability, integrity, and threat detection. By monitoring file activities and identifying suspicious behavior, the system can help organizations protect sensitive information from both internal and external security threats.


## Project Objectives
The main objective of the Secure File Transfer Monitoring System is to monitor, analyze, and secure file-transfer activities while maintaining file integrity and providing effective security auditing.

The key objectives of the system are:

**<li>Monitor and log file transfers:** Record all file upload, download, copy, move, and transfer activities performed on the system.</li>
**<li>Detect unauthorized file movement:** Identify unauthorized transfers of sensitive, confidential, or restricted files.</li>
**<li>Verify file integrity:** Use cryptographic hashing techniques such as SHA-256 and MD5 to detect unauthorized modifications, replacements, or tampering of files.<li/>
**<li>Generate security alerts:** Automatically generate alerts when predefined security policies are violated or suspicious file-transfer activities are detected.</li>
**<li>Maintain detailed audit logs:** Store information such as file name, user, timestamp, source, destination, operation, and transfer status for security investigation.</li>
**<li>Generate security reports:** Provide summarized reports of file-transfer activities, detected violations, integrity failures, and potential security incidents.</li>
**<li>Improve data protection:** Reduce the risk of data leakage, unauthorized file transfers, and malicious file manipulation through continuous monitoring and auditing.</li>
## Features

- File creation, modification, movement, deletion, upload, and download logging
- Sensitive-directory and restricted-file monitoring
- SHA-256 integrity verification
- Unauthorized movement detection
- Security alerts and audit reports

## Ethical Use

This project is intended for systems owned by, or operated with permission
from, the user or organization deploying it. Do not monitor files, users,
devices, or networks without authorization.

## Installation

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python -m file_monitor
```

## Configuration

Copy the example configuration:

```bash
cp .env.example .env
```

Never commit `.env`, real logs, credentials, or confidential file content.

## Limitations

Filesystem monitoring may not reveal every operating-system-level transfer,
especially transfers performed through privileged processes, cloud clients,
or remote systems. Use this tool as a monitoring component, not as a complete
DLP solution.
