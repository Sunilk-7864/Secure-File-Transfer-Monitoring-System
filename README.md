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


## Practical Scope of the Project

The Secure File Transfer Monitoring System focuses on monitoring file-related activities, detecting unauthorized data movement, verifying file integrity, and generating security reports. The practical scope of the project includes the following components:

### 1. File Transfer Logging

The system continuously monitors and records file-related activities performed on the system.

Monitor file copy, move, delete, upload, and download events.
Record important details such as:
File name and file type
Timestamp of the activity
Source path
Destination path
User account
Process or application name
Type of file operation
Maintain structured audit logs that can be used for security analysis and investigation.


Each event can be recorded with:

Timestamp<br>
Event Type<br>
File Name<br>
File Path<br>
File Hash<br>
Process Information<br>
Security Status

Example:

2026-09-12 16:30:21<br>
Event: File Created<br>
File: confidential.pdf<br>
Path: D:\Monitored\confidential.pdf<br>
Hash: SHA-256: ...<br>
Status: Logged

### 2. Unauthorized Movement Detection

The system identifies suspicious or unauthorized movement of sensitive files.

Maintain a configurable list of sensitive directories, confidential files, and restricted locations.
Detect unauthorized access, copying, or movement of protected files.
Generate alerts when defined security policies are violated.
Monitor suspicious outbound transfers involving:
USB/removable storage devices
Network shares
Cloud-synchronized folders
Other external destinations
Identify unusual file-transfer activities that may indicate potential data exfiltration.
### 3. File Integrity Checks

The system uses cryptographic hashing to verify that files have not been modified or tampered with during or after transfer.

<li>Calculate pre-transfer and post-transfer hash values.</li>
<li>Support hashing algorithms such as SHA-256 and MD5.</li>
<li>Compare hash values to identify changes in file contents.</li>
<li>Detect:</li>
         <li>Unauthorized modifications</li>
<li>File tampering</li>
<LI>File corruption</LI>
<LI>Unexpected file replacement</LI>
<LI>Highlight integrity mismatches for further investigation.</LI>

When a file is detected, the system can calculate its SHA-256 hash using Python's hashlib module.</p>

For example:

File: report.pdf

Original Hash:
8f14e45fceea167a5a36dedd4bea2543...

Current Hash:
91c3d4e7a2b1c9d8e6f5a4b3c2d1e0f9...

Status: FILE MODIFIED


### 4. Reporting and Alert System

The system provides security alerts and detailed reports based on monitored file activities.

<LI>Generate logs for all monitored file events.</LI>
<LI>Highlight policy violations and suspicious file transfers.</LI>
<LI>Generate alerts when unauthorized activities or integrity violations are detected.</LI>
<LI>Maintain a searchable audit trail for security investigations.</LI>

**Produce a final audit report summarizing:**
<LI>File-transfer activities</LI>
<LI>Unauthorized movements</LI>
<LI>Integrity violations</LI>
<LI>Detected policy violations</LI>
<LI>Security alerts</LI>
Overall monitoring results

## Overall Scope

The project provides a centralized approach to file-transfer monitoring, unauthorized movement detection, integrity verification, and security auditing. It can help organizations improve visibility into file activities and identify potential security incidents before they result in significant data loss or unauthorized disclosure.

## Tools & Technologies Used

### Programming languages:

<li>Python</li>

#### Models / Tools
Install the required library:

pip install watchdog

A basic monitoring program can be implemented as follows:

import hashlib
import logging
import os
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler


MONITOR_FOLDER = "D:/Monitored"


logging.basicConfig(
    filename="file_monitor.log",
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)


def calculate_hash(file_path):
    """Calculate SHA-256 hash of a file."""
    sha256 = hashlib.sha256()

    try:
        with open(file_path, "rb") as file:
            for block in iter(lambda: file.read(4096), b""):
                sha256.update(block)

        return sha256.hexdigest()

    except (FileNotFoundError, PermissionError):
        return None


class FileMonitorHandler(FileSystemEventHandler):

    def on_created(self, event):
        if not event.is_directory:
            file_hash = calculate_hash(event.src_path)

            logging.info(
                "FILE CREATED | Path=%s | SHA256=%s",
                event.src_path,
                file_hash
            )

            print(f"[CREATED] {event.src_path}")
            print(f"SHA-256: {file_hash}")

    def on_modified(self, event):
        if not event.is_directory:
            file_hash = calculate_hash(event.src_path)

            logging.info(
                "FILE MODIFIED | Path=%s | SHA256=%s",
                event.src_path,
                file_hash
            )

            print(f"[MODIFIED] {event.src_path}")
            print(f"SHA-256: {file_hash}")

    def on_deleted(self, event):
        if not event.is_directory:
            logging.warning(
                "FILE DELETED | Path=%s",
                event.src_path
            )

            print(f"[DELETED] {event.src_path}")

    def on_moved(self, event):
        if not event.is_directory:
            logging.info(
                "FILE MOVED | From=%s | To=%s",
                event.src_path,
                event.dest_path
            )

            print(
                f"[MOVED] {event.src_path} -> {event.dest_path}"
            )


if __name__ == "__main__":

    event_handler = FileMonitorHandler()

    observer = Observer()
    observer.schedule(
        event_handler,
        MONITOR_FOLDER,
        recursive=True
    )

    observer.start()

    print("Secure File Transfer Monitoring System")
    print(f"Monitoring folder: {MONITOR_FOLDER}")
    print("Press Ctrl+C to stop.")

    try:
        while True:
            pass

    except KeyboardInterrupt:
        observer.stop()

    observer.join()

    
<li>hashlib</li>

**The system can follow this process:**

File Received/Transferred
          ↓
   Read File Contents
          ↓
 Generate SHA-256 Hash
          ↓
 Store Hash in Database/Log
          ↓
     Later Verification
          ↓
 Generate New Hash
          ↓
 Compare with Original
       ↙       ↘
    Same       Different
     ↓             ↓
  Integrity     File Modified
   Verified       / Alert

**Python Code Using hashlib**

import hashlib

def calculate_sha256(file_path):
    sha256_hash = hashlib.sha256()

    with open(file_path, "rb") as file:
        for data in iter(lambda: file.read(4096), b""):
            sha256_hash.update(data)

    return sha256_hash.hexdigest()

## Example Output

File: D:/Monitored/sample.pdf

SHA-256:
a7f5f35426b927411fc9231b56382173...

file_path = "D:/Monitored/sample.pdf"

file_hash = calculate_sha256(file_path)

print("File:", file_path)
print("SHA-256:", file_hash)

## win32api / PowerShell Get-ChildItem (optional for Windows)

For a Secure File Transfer Monitoring System using Python on Windows, win32api and PowerShell's Get-ChildItem can be used as optional Windows-specific tools. They are useful for obtaining file information and performing additional checks alongside Python's watchdog and hashlib.
**1. win32api**

win32api is part of the PyWin32 package and provides Python access to Windows API functions.

Install it with:
pip install pywin32

It can be used to obtain information such as:

    File attributes
    File timestamps
    File paths
    Windows-specific file information
    File-system operations

For example:

import win32api

file_path = r"D:\Monitored\sample.pdf"

info = win32api.GetFileAttributes(file_path)

print("File Attributes:", info)

For a monitoring project, this information can be added to the security log along with the file's SHA-256 hash.
