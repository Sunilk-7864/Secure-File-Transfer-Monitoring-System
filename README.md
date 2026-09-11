# Secure File Transfer Monitoring System

A Python-based defensive monitoring tool that records file activity,
checks file integrity, detects policy violations, and generates audit reports.

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
