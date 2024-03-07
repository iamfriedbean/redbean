# redbean
Redbean is a blackbox - fast TCP port and vulnerability scanner utilising artificial intelligence analysis as guide to more effective remediation of vulnerabilities.
## How to install 

Part of Beanscan Suite of tools. See beanscan.

Once installed, just run the app (you may need to close and re-open your console terminal to apply environment configuration)     

```
$redbean -h
```

*****
### Updating
To fetch the latest update, just run:
```
$update-beanscan
```   

*****

## System/Platform Requirements

- Ubuntu Linux 20.04 LTS and above.
- BASH required
- Internet Connection
- SUDO rights (required for Ubuntu package update and headless crawling)
  


## Some Usage examples
Run simple TCP port scan
```
$redbean -ip 192.168.0.0/24 -ports 80,443
```

Run service scan for top 1K ports. This is the default behaviour if no specific ports are specified   
```
$redbean -ip 192.168.0.1 -probe
```

Run TCP portscan against list of IP addresses and ports
```
$redbean -ipfile ~/iplist.txt -portsfile ~/wordlist/65k-ports.txt
```

Run vulnerability scan against target. Also run analysis using artificial-intelligence.
```
$redbean -ip 192.168.0.1 -vscan -category 6
```


Refer to the help section for other command options and features: 

```
|  _ \ ___  __| | |__   ___  __ _ _ __
| |_) / _ \/ _` | '_ \ / _ \/ _` | '_ \ 
|  _ <  __/ (_| | |_) |  __/ (_| | | | |
|_| \_\___|\__,_|_.__/ \___|\__,_|_| |_|v0.20 (experimental)
@iamfriedbean || AI Risk Guided Vulnerability Scanner
=====================================================

Powered by open source. Redbean is a blackbox - fast TCP port and vulnerability scanner utilising
artificial intelligence as guide to effective remediation of vulnerabilities. 

Usage:
   redbean [options] 

PORT SCANNING:                                                             
   -ip          IP address or CIDR range to scan            
   -ports       Comma-separated list of ports to scan (e.g. -ports 21,22,80,443)
   -portsfile   File containing list of ports to scan (e.g. -portsfile ~/.tmp/top1k-ports.txt)
   -ipfile      File containing list of IP addresses to scan (e.g. -ipfile ~/.tmp/iplist.txt)
   -timeout     Scan timeout in milliseconds. Default is 200  (e.g. -timeout 500)
   -threads     Number of threads to use for scanning. Default is 30 (e.g. -threads 50)
   -probe       Probe open ports to determine running service
   -sploit      Search for Metasploit POC when used with -probe flag
   -proxy       Use SOCKS proxy address (e.g., socks5://127.0.0.1:9050). (limited functionalities)
   -udp         Run a UDP port scan. (best-effort)
   -update      Run an update. Ignores all the other flags

VULNERABILITY SCANNING:                                                     
   -vscan     Scans for vulnerabilities.

AI RISK/IMPACT ANALYSIS:
   -azgpt      Use Azure OpenAI Service over default OpenAI (ChatGPT)

   -category   Asset Category to support AI risk guided analysis (e.g., -category 1)
               Valid values:
               1 - Publicly Exposed. Business Critical (Default)
               2 - Publicly Exposed. Important but not Business Critical
               3 - Publicly Exposed. Not Important nor Business Critical
               4 - Internal network only. Business Critical
               5 - Internal network only. Important but not Business Critical
               6 - Internal network only. Not Important nor Business Critical

MISCELLANEOUS:                                                     
   -cvelist    List of testable CVEs. Ignores all the other flags
   -gptassist  Use simple query using OPENAI ChatGPT. Ignores all the other flags
   -azassist   Use simple query using Azure OPENAI Service. Ignores all the other flags

USAGE EXAMPLES:                                                     
   redbean -ip 192.168.0.0/24 -ports 80,443 
   redbean -ipfile ~/.tmp/iplist.txt -ports 80,443 
   redbean -ipfile ~/.tmp/iplist.txt -portsfile ~/wordlist/65k-ports.txt 
   redbean -vscan -ip 192.168.0.1 -portsfile ~/wordlist/65k-ports.txt
 
   redbean -ip 192.168.0.1 -vscan
 
Note: Text file containing IP addresses or ports must only have one item per line. If no port is specified, it will use the default top 1K ports
```


### Additional configuration
  

The configuration file can be found at ~/.config/beanscan/config.env   
Here, you can configure optional headers, API keys and OpenAI Endpoints:

```
#OpenAI GPT Key
GPT_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"


#Azure OpenAI Configuration
AZURE_OPENAI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
AZURE_OPENAI_ENDPOINT="https://xxxxxxxxxx.openai.azure.com/"
```


*****
