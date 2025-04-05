
# AuthCracker - Advanced Multi-Service Brute Force Tool
[![Python Version](https://img.shields.io/badge/Language-Python-blue.svg)](https://www.python.org/) [![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT) 



AuthCracker is a powerful and versatile brute force tool designed to test credentials across multiple services including SSH, FTP, and HTTP. With features like Tor support, proxy rotation, and random password generation, it's an essential tool for penetration testers and security researchers.

## Table of Contents

 - [Features]()
 - [Installation]()
 
 - [License]()


## Features
- **Multi-Service Support**: Attack SSH, FTP, and HTTP services with a single tool

- **Smart Authentication Detection**: Auto-detects SSH authentication types

- **Anonymity Options**: Built-in Tor support and proxy rotation

- **Resume Capability**: Continue interrupted attacks from where you left off

- **Verbose Mode**: Detailed logging for debugging and analysis

- **Random Password Generation**: Generate passwords on-the-fly with customizable length

- **User-Friendly Output**: Color-coded console output for easy reading


## Installation

### Prerequisites

```bash
pip install paramiko requests colorama pysocks
```
### Download

```bash
git clone https://github.com/SDX442/AuthCracker.git
cd AuthCracker
chmod +x authcracker.py
```  
### Usage
- Full Option List :
```bash
./authcracker.py -h
usage: authcracker.py [-h] --service SERVICE [SERVICE ...] (-w WORDLIST | -r MIN_LEN MAX_LEN) 
                      [-u USER] [--users USERS] --ip IP [--tor] [--proxies PROXIES] 
                      [-i {3,4,5,6,7,8,9}] [--resume] [--verbose] [--random-agent] 
                      [--http-post HTTP_POST] [--success-content-length SUCCESS_CONTENT_LENGTH] 
                      [--failure-content-length FAILURE_CONTENT_LENGTH] [--success-pattern SUCCESS_PATTERN] 
                      [--failure-pattern FAILURE_PATTERN]

options:
  -h, --help            show this help message and exit
  --service SERVICE [SERVICE ...]
                        Service to test (http,ftp,ssh) with optional port
  -w WORDLIST, --wordlist WORDLIST
                        Password wordlist file
  -r MIN_LEN MAX_LEN, --rand MIN_LEN MAX_LEN
                        Generate random passwords (length MIN-MAX)
  -u USER, --user USER  Single username to test
  --users USERS         File containing username list
  --ip IP               Target IP/Domain
  --tor                 Enable Tor routing
  --proxies PROXIES     Proxy list file (ip:port format)
  -i {3,4,5,6,7,8,9}, --iterations {3,4,5,6,7,8,9}
                        Attempts per user (default: 3)
  --resume              Restore previous session
  --verbose             Enable detailed logging
  --random-agent        Randomize HTTP User-Agent
  --http-post HTTP_POST
                        HTTP POST parameters (use ^USER^, ^PASS^)
  --success-content-length SUCCESS_CONTENT_LENGTH
                        Expected success content length
  --failure-content-length FAILURE_CONTENT_LENGTH
                        Expected failure content length
  --success-pattern SUCCESS_PATTERN
                        Success response pattern
  --failure-pattern FAILURE_PATTERN
                        Failure response pattern
```
- SSH Credential Testing  
```bash
./authcracker.py --service ssh -u admin -w passwords.txt --ip 192.168.1.100
```  
- FTP Audit with Random Passwords  
```bash
./authcracker.py --service ftp --users employees.txt -r 8 12 --ip ftp.example.com
```
- HTTP Form Testing  
```bash
./authcracker.py --service http --ip webapp.com \
--http-post "login=^USER^&pass=^PASS^&submit=1" \
--failure-pattern "Incorrect"  --failure-content-length 32
```
- Anonymous Testing via Tor  
```bash
./authcracker.py --service ssh -u root -w rockyou.txt --ip 10.10.10.10 --tor
```
## License



This project is licensed under the MIT License- See [LICENSE](https://choosealicense.com/licenses/mit/) for details.
## 

Happy Hacking !


