# SQLi-Scanner

A Python tool for detecting SQL Injection vulnerabilities in web applications. Supports crawling to discover URLs and direct testing of specific targets. Part of my Python learning projects, similar to FilesOrganizer and Python-currency-converter-ksh.

![Banner](https://img.shields.io/badge/Python-3.6%2B-blue) ![License](https://img.shields.io/badge/License-MIT-green) ![GitHub Repo](https://img.shields.io/badge/GitHub-Ian--Lusule-orange)

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [Command-Line Arguments](#command-line-arguments)
- [How It Works](#how-it-works)
- [Limitations](#limitations)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Introduction

SQL Injection (SQLi) is a critical vulnerability where attackers inject malicious SQL code into queries, potentially leading to data breaches. This scanner tests URLs by injecting vectors and checking for error patterns or time delays in responses.

Built for educational purposes, aligning with my GitHub repos focused on Python scripts for fun and practice. Use ethically—test only on authorized sites.

**Disclaimer:** Educational tool only. Unauthorized use may be illegal.

## Features

- **Modes:**
  - **Crawling:** BFS crawling to find and test URLs.
  - **Target Testing:** Multi-threaded testing of URL lists.

- **SQLi Vectors:** Includes error-based, boolean, time-based, and union payloads like `' OR '1'='1'--` and `1 UNION SELECT NULL,version(),NULL--`.

- **Detection:** Checks for database error signatures (MySQL, PostgreSQL, Oracle) and time delays.
- **Threading & Customization:** Adjustable threads, timeout, user-agent.
- **Output:** Immediate terminal print (colored) and file append.
- **Banner & UI:** ASCII banner, screen clear.

## Installation

1. **Clone:**
```bash
git clone https://github.com/Ian-Lusule/SQLi-Scanner.git
cd SQLi-Scanner
```

2. **Dependencies:**
```bash
pip install requests beautifulsoup4 colorama
```

3. **Executable:**
```bash
chmod +x sqli_scanner.py
```

## Usage
```bash
python3 sqli_scanner.py [options]
```

## Examples

1. **Target Mode:**
```bash
python3 sqli_scanner.py -Tt -f urls.txt -o vulnerable_sqli.txt
```

2. **Crawling:**
```bash
python3 sqli_scanner.py -d 3 -u http://testsite.com -o output.txt
```

3. **Custom:**
```bash
python3 sqli_scanner.py -Tt -f urls.txt -T 10 -a "CustomUA"
```

## Command-Line Arguments

- **Modes:** `-Tt`, `-d <depth>`
- **Targets:** `-u <URL>`, `-f <file>`
- **Options:** `-t <threads>`, `-T <timeout>`, `-a <UA>`, `-o <file>`, `-h`

## How It Works

1. **Injection:** Modifies query params with vectors.
2. **Check:** Looks for errors or delays (>50% timeout).
3. **Crawling:** Parses links, tests those with queries.
4. **Concurrency:** ThreadPool for speed.

## Limitations

- **GET Only:** No POST or cookie injection.
- **Blind SQLi:** Basic time-based; may miss advanced cases.
- **False Results:** Needs manual confirmation.
- **No Evasion:** Basic vectors; sites with WAF may block.
- **Ethical:** Risk of detection/bans.

## Contributing

Fork, issue, PR welcome. Add vectors or improve detection.

## License

MIT License.

## Contact

- GitHub: [Ian-Lusule](https://github.com/Ian-Lusule)
- See my other projects like Cs-Blogs for more.
