# Advanced Vulnerability Verification Scanner

This repository contains an active vulnerability verification scanner that performs multi-method detection for fifty high-impact CVEs across web servers, frameworks, enterprise appliances, CI/CD tooling, IoT devices, and infrastructure platforms.

## Features

- **Active verification** for 50 CVEs with 3–5 independent confirmation methods per vulnerability.
- **Multi-threaded scanning** with connection pooling for high throughput across large target lists.
- **Service-aware filtering** to avoid false positives on closed or patched systems.
- **Rich-powered live dashboard** displaying scan progress, detection feed, and performance metrics.
- **Portable architecture** with modular detector implementations and reusable network utilities.

## Project Structure

```
vulnerability_scanner/
├── config.py
├── detectors/
│   ├── base_detector.py
│   ├── cve_*.py (50 detector modules)
│   └── __init__.py
├── utils/
│   ├── network.py
│   ├── output.py
│   ├── port_scanner.py
│   ├── validators.py
│   └── __init__.py
├── ip.txt
├── requirements.txt
└── scanner.py
```

## Usage

1. **Install dependencies**

   ```bash
   pip install -r vulnerability_scanner/requirements.txt
   ```

2. **Populate target list**

   Add IP addresses or hostnames to `vulnerability_scanner/ip.txt` (one per line). Lines beginning with `#` are ignored.

3. **Run the scanner**

   ```bash
   python -m vulnerability_scanner.scanner --targets vulnerability_scanner/ip.txt
   ```

   During execution, a live dashboard will display overall progress, real-time detections, and throughput metrics.

## Notes

- The scanner prioritises critical CVEs defined in `config.py` and skips detectors when prerequisite services/ports are closed.
- Detection methods are non-destructive and rely on behavioural cues such as path traversal responses, template expression evaluation, protocol handshakes, and metadata exposures.
- Evidence gathered for each positive detection is retained in the scan results for auditing.

## Disclaimer

Use this tool responsibly and only against systems you are authorised to assess. The authors assume no liability for misuse.
