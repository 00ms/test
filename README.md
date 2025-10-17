# Vulnerability Scanner

This repository contains a Python-based vulnerability scanner capable of checking targets for 50 high and critical remote code execution (RCE) CVEs across web servers, enterprise appliances, CI/CD platforms, IoT devices, and container infrastructure.

## Features

- Asynchronous scanning with configurable concurrency (default: 50)
- Reads targets from `ip.txt` supporting individual IPs and CIDR ranges
- 50 dedicated CVE detectors grouped by category
- Multiple validation techniques per CVE (version checks, endpoint probes, response fingerprints, safe probes)
- Rich-powered terminal dashboard with progress bars, live findings table, spinner animations and summary panel
- JSON and CSV export of scan results with confidence scoring and remediation guidance
- Designed for safe, non-exploitative detection only

## Project Structure

```
vulnerability_scanner/
├── scanner.py               # CLI entry point
├── config.py                # Scanner configuration defaults
├── requirements.txt         # Python dependencies
├── ip.txt                   # Sample target list
├── cve_detectors/           # CVE-specific detection modules
└── utils/                   # Networking, output, and validation helpers
```

## Installation

1. Create and activate a virtual environment (optional but recommended).
2. Install dependencies:

```bash
pip install -r vulnerability_scanner/requirements.txt
```

## Usage

Basic scan using defaults (targets from `vulnerability_scanner/ip.txt`):

```bash
python -m vulnerability_scanner.scanner
```

Specify a custom target file:

```bash
python -m vulnerability_scanner.scanner --input /path/to/targets.txt
```

Adjust concurrency and enable verbose logging:

```bash
python -m vulnerability_scanner.scanner --threads 100 --verbose
```

Limit scanning to specific CVE categories:

```bash
python -m vulnerability_scanner.scanner --category web_servers,enterprise
```

After each run, JSON and CSV reports are saved in the repository root using the pattern `results_YYYYMMDD_HHMMSS.json` and `.csv`.

## Disclaimer

This scanner is provided for authorized security testing and research purposes only. Ensure you have explicit permission to test every target. The detection techniques are intentionally non-exploitative and rely on publicly observable fingerprints, version checks, and safe probes.
