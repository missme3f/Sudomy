# Sudomy
[![License](https://img.shields.io/badge/license-MIT-red.svg)](https://github.com/Screetsec/Sudomy/blob/master/LICENSE.md)  [![Build Status](https://travis-ci.org/Screetsec/Sudomy.svg?branch=master)](https://travis-ci.org/Screetsec/Sudomy)  [![Version](https://img.shields.io/badge/Release-1.1.6-blue.svg?maxAge=259200)]()  [![Build](https://img.shields.io/badge/Supported_OS-Linux-yellow.svg)]()  [![Build](https://img.shields.io/badge/Supported_WSL-Windows-blue.svg)]() [![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/screetsec/sudomy/issues)  [![Youtube](https://img.shields.io/badge/Youtube-Demo-red.svg)](https://www.youtube.com/watch?v=DpXIBUtasn0)
### Subdomain Enumeration & Analysis
![ff](https://user-images.githubusercontent.com/17976841/63212795-b8d57300-c133-11e9-882a-f604d67819cc.png)

***Sudomy*** is a subdomain enumeration tool, created using a bash script, to analyze domains and collect subdomains in fast and comprehensive way.

## Features !
##### For recent time, ***Sudomy*** has these 15 features:
-  Easy, light, fast and powerful. Bash script is available by default in almost all Linux distributions. By using bash script multiprocessing feature, all processors will be utilized optimally.
-  Subdomain enumeration process can be achieved by using **active** method or **passive** method
    - **Active Method**
        - *Sudomy* utilize Gobuster tools because of its highspeed performance in carrying out DNS Subdomain Bruteforce attack (wildcard support). The wordlist that is used comes from combined SecList (Discover/DNS) lists which contains around 3 million entries

    - **Passive Method**
        - By **selecting** the **good** third-party sites, the enumeration process can be **optimized**. More results will be obtained with less time required. *Sudomy* can collect data from these  well-curated 20 third-party sites:

                https://dnsdumpster.com
                https://web.archive.org
                https://shodan.io
                https://virustotal.com
                https://crt.sh
                https://www.binaryedge.io
                https://securitytrails.com
                https://sslmate.com/certspotter
                https://censys.io
                https://threatminer.org
                http://dns.bufferover.run
                https://hackertarget.com
                https://www.entrust.com/ct-search/
                https://www.threatcrowd.org
                https://riddler.io
                https://findsubdomains.com
                https://rapiddns.io/
                https://otx.alienvault.com/
                https://index.commoncrawl.org/
                https://urlscan.io/
- Test the list of collected subdomains and probe for working http or https servers. This feature uses a third-party tool, [httprobe](https://github.com/tomnomnom/httprobe "httprobe").
- Subdomain availability test based on Ping Sweep and/or by getting HTTP status code.
- The ability to detect virtualhost (several subdomains which resolve to single IP Address). Sudomy will resolve the collected subdomains to IP addresses, then classify them if several subdomains resolve to single IP address. This feature will be very useful for the next penetration testing/bug bounty process. For instance, in port scanning, single IP address won’t be scanned repeatedly
- Performed port scanning from collected subdomains/virtualhosts IP Addresses
- Testing Subdomain TakeOver attack
- Taking Screenshots of subdomains
- Identify technologies on websites
- Detection urls, ports, title, content-length, status-code, response-body probbing.
- Smart auto fallback from https to http as default.
- Data Collecting/Scraping open port from 3rd party (Default::Shodan), For right now just using Shodan [Future::Censys,Zoomeye]. More efficient and effective to collecting port from list ip on target [[ Subdomain > IP Resolver > Crawling > ASN & Open Port ]]
- Collecting Juicy URL & Extract URL Parameter ( Resource Default::WebArchive, CommonCrawl, UrlScanIO) 
- Define path for outputfile (specify an output file when completed) 
- Report output in HTML & CSV format

## How Sudomy Works
*Sudomy* is using cURL library in order to get the HTTP Response Body from third-party sites to then execute the regular expression to get subdomains. This process fully leverages multi processors, more subdomains will be collected with less time consumption.

## Publication
- [Sudomy: Information Gathering Tools for Subdomain Enumeration and Analysis](https://iopscience.iop.org/article/10.1088/1757-899X/771/1/012019/meta) -  IOP Conference Series: Materials Science and Engineering, Volume 771, 2nd International Conference on Engineering and Applied Sciences (2nd InCEAS) 16 November 2019, Yogyakarta, Indonesia

## User Guide
- Offline User Guide : [Sudomy - Subdomain Enumeration and Analysis User Guide v1.0](https://github.com/Screetsec/Sudomy/blob/master/doc/Sudomy%20-%20Subdomain%20Enumeration%20%26%20Analaysis%20User%20Guide%20v1.0.pdf)
- Online User Guide : [Subdomain Enumeration and Analysis User Guide](https://sudomy.screetsec.web.id/features) - Up to date

## Comparison
The following are the results of passive enumeration DNS testing of *Sublist3r, Subfinder*, and *Sudomy*. The domain that is used in this comparison is ***bugcrowd.com***.

|  Sudomy | Subfinder   | Sublister |
| ------------  | ------------ | ------------ |
|<img align="left" width="420" height="363" src="https://user-images.githubusercontent.com/17976841/63593207-b9f81b80-c5dd-11e9-9f46-f0cc53e032d4.gif">| <img align="left" width="430" height="363" src="https://user-images.githubusercontent.com/17976841/63592469-d85d1780-c5db-11e9-9e45-421653b65bad.gif"> | <img align="left" width="430" height="363" src="https://user-images.githubusercontent.com/17976841/63592249-55d45800-c5db-11e9-8ad0-80a5b70411c1.gif">   |

Asciinema :
- [Subfinder](https://asciinema.org/a/260323)
- [Sudomy](https://asciinema.org/a/260324)
- [Sublist3r](https://asciinema.org/a/260325)

## Installation
*Sudomy* is currently extended with the following tools. Instructions on how to install & use the application are linked below.

### To Download Sudomy From Github
```bash
# Clone this repository
git clone --recursive https://github.com/screetsec/Sudomy.git
```

### Dependencies
```
$ pip install -r requirements.txt
```
*Sudomy* requires [jq](https://stedolan.github.io/jq/download/) to run and parse. Information on how to download and install jq can be accessed [here](https://stedolan.github.io/jq/download/)

```bash
# Linux
apt-get update
apt-get install jq nmap phantomjs npm
npm i -g wappalyzer

# Mac
brew cask install phantomjs 
brew install jq nmap npm
npm i -g wappalyzer
```

## Running in a Docker Container
```bash
# Pull an image from DockerHub
docker pull screetsec/sudomy:v1.1.6-dev

# Run an image, you can run the image on custom directory but you must copy/download config sudomy.api on current directory
docker run -v "${PWD}/output:/usr/lib/sudomy/output" -v "${PWD}/sudomy.api:/usr/lib/sudomy/sudomy.api" -it --rm screetsec/sudomy:v1.1.6-dev [argument]

or define API variable when executed an image.

docker run -v "${PWD}/output:/usr/lib/sudomy/output" -e "SHODAN_API=xxxx" -e "VIRUSTOTAL=xxxx" -it --rm screetsec/sudomy:v1.1.6-dev [argument]
```

### Post Installation
API Key is needed before querying on third-party sites, such as ```Shodan, Censys, SecurityTrails, Virustotal,``` and ```BinaryEdge```.
- The API key setting can be done in sudomy.api file.
```bash
# Shodan
# URL :  http://developer.shodan.io
# Example :
#      - SHODAN_API="VGhpc1M0bXBsZWwKVGhmcGxlbAo"

SHODAN_API=""

# Censys
# URL : https://censys.io/register

CENSYS_API=""
CENSYS_SECRET=""

# Virustotal
# URL : https://www.virustotal.com/gui/
VIRUSTOTAL=""


# Binaryedge
# URL : https://app.binaryedge.io/login
BINARYEDGE=""


# SecurityTrails
# URL : https://securitytrails.com/
SECURITY_TRAILS=""
```

## Usage

```text
 ___         _ _  _
/ __|_  _ __| (_)(_)_ __ _  _
\__ \ || / _  / __ \  ' \ || |
|___/\_,_\__,_\____/_|_|_\_, |
                          |__/ v{1.1.5#dev} by @screetsec
Sud⍥my - Fast Subdmain Enumeration and Analyzer
	 http://github.com/screetsec/sudomy

Usage: sud⍥my.sh [-h [--help]] [-s[--source]][-d[--domain=]]

Example: sud⍥my.sh -d example.com
         sud⍥my.sh -s Shodan,VirusTotal -d example.com
         sud⍥my.sh -pS -rS -sC -nT -sS -d example.com

Optional Arguments:
  -a,  --all             Running all Enumeration, no nmap & gobuster 
  -b,  --bruteforce      Bruteforce Subdomain Using Gobuster (Wordlist: ALL Top SecList DNS) 
  -d,  --domain          domain of the website to scan
  -h,  --help            show this help message
  -o,  --outfile         specify an output file when completed 
  -s,  --source          Use source for Enumerate Subdomain
  -aI, --apps-identifier Identify technologies on websites from domain list
  -dP, --db-port         Collecting port from 3rd Party default=shodan
  -eP, --extract-params  Collecting URL Parameter from Engine
  -tO, --takeover        Subdomain TakeOver Vulnerabilty Scanner
  -pS, --ping-sweep      Check live host using methode Ping Sweep
  -rS, --resolver        Convert domain lists to resolved IP lists without duplicates
  -sC, --status-code     Get status codes, response from domain list
  -nT, --nmap-top        Port scanning with top-ports using nmap from domain list
  -sS, --screenshot      Screenshots a list of website
  -nP, --no-passive      Do not perform passive subdomain enumeration 
       --httpx           Perform httpx multiple probers using retryablehttp 
       --dnsprobe        Perform multiple dns queries (dnsprobe) 
       --no-probe        Do not perform httprobe 
       --html            Make report output into HTML 


```
To use all 20 Sources and Probe for working http or https servers:
```
$ sudomy -d hackerone.com
```
To use one or more source:
```
$ sudomy -s shodan,dnsdumpster,webarchive -d hackerone.com
```
To use one or more plugins:
```
$ sudomy -pS -sC -sS -d hackerone.com
```
To use all plugins: testing host status, http/https status code, subdomain takeover and screenshots. 

Nmap,Gobuster and wappalyzer Not Included.
```
$ sudomy --all -d hackerone.com
```

To create report in HTML Format
```
$ sudomy --all -d hackerone.com --html
```

HTML Report Sample:

| Dashboard	| Reports	|
| ------------  | ------------ |
|![Index](https://user-images.githubusercontent.com/17976841/63597336-6ab6e880-c5e7-11e9-819e-91634e347b0c.PNG)|![f](https://user-images.githubusercontent.com/17976841/63597476-bbc6dc80-c5e7-11e9-8985-6a73348a2e02.PNG)|



## Tools Overview
- Youtube Videos : Click [here](http://www.youtube.com/watch?v=DpXIBUtasn0)


## Translations
- [Indonesia](https://github.com/Screetsec/Sudomy/blob/master/doc/README_ID.md)
- [English](https://github.com/Screetsec/Sudomy/blob/master/doc/README_EN.md)
- [Portuguese - Brazil](https://github.com/Screetsec/Sudomy/blob/master/doc/README_PT_BR.md)


## Changelog
All notable changes to this project will be documented in this [file](https://github.com/Screetsec/sudomy/blob/master/CHANGELOG.md).



## Alternative Best Tool - Subdomain Enumeration
- [Subfinder](https://github.com/projectdiscovery/subfinder) - Projectdiscovery
- [Sublist3r](https://github.com/aboul3la/Sublist3r) - aboul3la
- [Findomain](https://github.com/Edu4rdSHL/findomain) - Edu4rdSHL
- [Amass)](https://github.com/OWASP/Amass) - OWASP

## Credits & Thanks
- [Tom Hudson](https://github.com/tomnomnom/) - Tomonomnom
- [OJ Reeves](https://github.com/OJ/) - Gobuster
- [ProjectDiscovery](https://github.com/projectdiscovery) - Security Through Intelligent Automation
- [Thomas D Maaaaz](https://github.com/maaaaz) - Webscreenshot
- [christophetd](https://github.com/christophetd/censys-subdomain-finder) - Censys
- [Daniel Miessler](https://github.com/danielmiessler/) - SecList
- [EdOverflow](https://github.com/EdOverflow/) - can-i-take-over-xyz
- [jerukitumanis](https://github.com/myugan) - Docker Maintainer
- [NgeSEC](https://ngesec.id/) - Community
- [Zerobyte](http://zerobyte.id/) - Community
- [Gauli(dot)Net](https://gauli.net/) - Lab Hacking Indonesia
- [Bugcrowd](https://www.bugcrowd.com/) & [Hackerone](https://www.hackerone.com/)
