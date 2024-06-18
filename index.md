---
layout: home
---

## `❯` whoami 2

I'm a seasoned security research leader with over a decade of experience in various fields, including penetration testing, static code analysis, reverse engineering, software development, and more. I'm currently the Head of Research at [Oxeye Security](https://www.oxeye.io/), leading the security research endeavours of the organization.

> ✨ "If I had 8 hours to chop down a tree, I would spend 6 of those hours sharpening my axe."

## Employment Background

| **Company** | **Years** | **Position** |
| [Oxeye](https://www.oxeye.io/) | _2021-2024_ | Head of Research |
| [Akamai](https://www.akamai.com/) | _2016-2021_ | Principal Security Research Lead |
| [Avnet](https://www.rockwellautomation.com/en-us/capabilities/industrial-cybersecurity/it-solutions.html) | _2014-2016_ | Senior Security Researcher |

## Public Appearnace

| **Conference** | **Year** | **Topic** |
| BlueHat IL | 2023 | [The Story of a Backstage RCE](https://www.youtube.com/watch?v=PKUdLqLLAes&ab_channel=MicrosoftIsraelR%26DCenter) |
| Blackhat Arsenal USA | 2022 | [Ox4Shell - Deobfuscate Log4Shell payloads with ease](https://www.blackhat.com/us-22/arsenal/schedule/#oxshell---deobfuscate-logshell-payloads-with-ease-27997) |
| BSides Las Vegas | 2020 | [Abusing the Service Workers Web API](https://www.youtube.com/watch?v=b7V5_xnXA1U&ab_channel=BSidesLV)
| Blackhat Arsenal USA | 2019 | [JSShell - An interactive XSS Managment Tool](https://www.blackhat.com/us-19/arsenal/schedule/#jsshell-an-interactive-xss-management--browser-debugging-tool-14984) |
| Blackhat Arsenal USA | 2018 | [MQTT-PWN Your IoT Swiss Army Knife](https://www.blackhat.com/us-18/arsenal/schedule/index.html#mqtt-pwn-your-iot-swiss-army-knife-11974) |

## Blog Posts

- [Take Me to Prom - Exploiting an RCE in openTSDB through Prometheus](https://www.oxeye.io/resources/take-me-to-prom-exploiting-an-rce-in-opentsdb-through-prometheus)
- [Gophers & Bees - parsing Golang structures in memory with eBPF](https://www.oxeye.io/resources/parsing-golang-structures-in-memory-with-ebpf)
- [RCE through SQL Injection Vulnerability in Hashicorp's Vault](https://www.oxeye.io/resources/rce-through-sql-injection-vulnerability-in-hashicorps-vault)
- ["BreakStage" – an Unauthenticated Remote Code Execution in Spotify’s Backstage](https://www.oxeye.io/resources/remote-code-execution-in-spotifys-backstage)
- [Enter "Sandbreak" - Vulnerability In vm2 Sandbox Module Enables Remote Code Execution (CVE-2022-36067)](https://www.oxeye.io/resources/vm2-sandbreak-vulnerability-cve-2022-36067)
- [Guess Who’s (R)BAC?](https://www.oxeye.io/resources/guess-whos-rbac)
- [“ParseThru” – Exploiting HTTP Parameter Smuggling in Golang](https://www.oxeye.io/resources/golang-parameter-smuggling-attack)
- [Client Side Threats & How Could Website Owners Mitigate Them?](https://web.archive.org/web/20210228195217/https://blogs.akamai.com/2019/09/client-side-threats-how-could-website-owners-mitigate-them.html)

## Projects

### [Ox4Shell](https://github.com/ox-eye/Ox4Shell?tab=readme-ov-file) - Deobfuscate Log4Shell payloads with ease

Since the release of the Log4Shell vulnerability (CVE-2021-44228), many tools were created to obfuscate Log4Shell payloads, making the lives of security engineers a nightmare. This tool intends to unravel the true contents of obfuscated Log4Shell payloads.

Resources:

- [Black Hat USA: Log4j de-obfuscator Ox4Shell ‘dramatically’ reduces analysis time](https://portswigger.net/daily-swig/black-hat-usa-log4j-de-obfuscator-ox4shell-dramatically-reduces-analysis-time)
- [Oxeye Mitigates Log4Shell Vulnerability with Ox4Shell – Payload Deobfuscation Tool](https://www.oxeye.io/press-releases/oxeye-mitigates-log4shell-vulnerability-with-ox4shell-open-source)
- [Oxeye Tool Can Counter Log4j Obfuscation Attacks](https://securityboulevard.com/2022/01/oxeye-tool-can-counter-log4j-obfuscation-attacks/)

### [JSShell](https://github.com/Den1al/JSShell) - An interactive multi-user web based javascript shell

An interactive multi-user web based javascript shell. It was initially created in order to debug remote esoteric browsers during experiments and research. This tool can be easily attached to XSS (Cross Site Scripting) payload to achieve browser remote code execution (similar to the BeeF framework).

Resources:

- [JSShell takes cross-site scripting to new highs](https://portswigger.net/daily-swig/jsshell-takes-cross-site-scripting-to-new-highs)
- [10 Top Tools for Threat Hunters from Black Hat USA 2019](https://securityboulevard.com/2019/09/10-top-tools-for-threat-hunters-from-black-hat-usa-2019/)

### [MQTT-PWN](https://github.com/akamai-threat-research/mqtt-pwn) - A one-stop-shop for IoT Broker penetration-testing

MQTT is a machine-to-machine connectivity protocol designed as an extremely lightweight publish/subscribe messaging transport and widely used by millions of IoT devices worldwide. MQTT-PWN intends to be a one-stop-shop for IoT Broker penetration-testing and security assessment operations, as it combines enumeration, supportive functions and exploitation modules while packing it all within command-line-interface with an easy-to-use and extensible shell-like environment.

Resources:

- [mqtt-pwn: IoT Broker penetration-testing and security assessment operations](https://securityonline.info/mqtt-pwn/)
