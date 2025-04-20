<p align="center">
  <img src="https://github.com/Ruhanyat-994/Reconscope/blob/main/Attachments/reconscope.png?raw=true" alt="Description" style="border-radius: 15px; width: 1000px;">
</p>

# ReconScope

**ReconScope** is a simple and modular Bash-based domain reconnaissance automation tool. It performs three key security testing functions — Nmap scanning, directory brute-forcing using Dirsearch, and subdomain certificate gathering using crt.sh. The tool can run in both batch and interactive modes, making it a great addition for penetration testers and software quality assurance (SQA).

---

## Features

-  Scans with **Nmap** for open ports and services.
-  Uses **Dirsearch** to find web directories (PHP extension by default).
-  Queries **crt.sh** for public certificate transparency logs.
-  Automatically generates a consolidated report.
-  Supports both **interactive mode** and **batch processing** via CLI arguments.

---

## Prerequisites

Make sure you have the following installed:

- `bash` (Linux/Mac environment or WSL on Windows)
- [`nmap`](https://nmap.org/)
- [`dirsearch`](https://github.com/maurosoria/dirsearch)
- `curl`
- `jq`

To install the missing tools:

```bash
sudo apt update
sudo apt install nmap curl jq python3
git clone https://github.com/maurosoria/dirsearch.git
```

> **Note**: Ensure `dirsearch.py` is executable or create a symlink to run `dirsearch` as a command.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/Ruhanyat-994/Reconscope.git
cd reconscope
chmod +x reconscope.sh
```

---

## Usage

### Batch Mode (Non-interactive)

Scan one or more domains:

```bash
./reconscope.sh example.com testsite.org
```

Scan using a specific module only:

```bash
./reconscope.sh -m nmap example.com
./reconscope.sh -m dirsearch testsite.org
./reconscope.sh -m crt example.org
```

### Interactive Mode

Launch in interactive mode:

```bash
./reconscope.sh -i
```

Then enter domains one by one. Type `quit` to exit.

---

## Output

For each scanned domain, a directory named `<domain>_recon` will be created containing:

- `nmap` – output of the Nmap scan
- `dirsearch` – output of the Dirsearch scan
- `crt` – raw certificate data from crt.sh
- `report` – consolidated human-readable scan report

Example:

```
example.com_recon/
├── crt
├── dirsearch
├── nmap
└── report
```

---

## Example Report Snippet

```
This scan was created on Fri Apr 19 21:53:21 UTC 2025

Results for nmap:
80/tcp   open  http
443/tcp  open  https

Results for dirsearch:
[Status: 200] /admin/
[Status: 403] /private/

Results for crt:
admin.example.com
login.example.com
```

---

## License

This project is licensed under the MIT License.

---

## Disclaimer

This script is intended for educational and lawful penetration testing/research purposes only. Always get proper authorization before scanning any domains or systems.

