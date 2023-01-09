# OSWASP-ZAP Scanner Documentation 

## 1. INSTALLATION
Download the scanner using the following command: 
```
wget https://github.com/zaproxy/zaproxy/releases/download/v2.12.0/ZAP_2.12.0_Linux.tar.gz 
```
Extract the downloaded tar file: 
```
tar -xvzf ZAP_2.9.0_Linux.tar.gz 
```
Change the directory to the ZAP folder: 
```
cd  ZAP_2.12.0
```
## 2. CONFIGURATION
Start zap GUI using this command: 
```
./zap.sh -port 8080
```
OSWASP ZAP GUI will load up. Now go to Tools>Options>API>API Key and copy the key from there and then exit the GUI by using Ctrl+C in the CLI. 
Start daemon mode with configured key using the following command: 
```
./zap.sh -daemon -config api.key=u39bcefvkn6is3k7jjmb3ebqpf -port 8080 &
```
## 3. Spider Scan
To start the Spider scan (Response: Scan ID): 
``` 
curl "http://localhost:8080/JSON/spider/action/scan/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&url=http://192.168.1.13:9392&contextName=&recurse=true"
```
the “recurse” parameter is used to specify whether to recursively scan a target. This means that ZAP will follow any links in the target and scan the linked pages as well. You can specify a maximum depth for the recursion using the “maxChildren” parameter: 
```
curl "http://localhost:8080/JSON/spider/action/scan/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&url=http://192.168.1.13:9392&contextName=&recurse=true&maxChildren=<NUMBER>"
```
To view the scan status/ percentage of work done: 
```
curl "http://localhost:8080/JSON/spider/view/status/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&scanId=<SCAN_ID>"
```
To view the scan results: 
```
curl "http://localhost:8080/JSON/spider/view/results/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&scanId=<SCAN_ID>"
```
To stop the Scanning:
```
curl "http://localhost:8080/JSON/spider/action/stop/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&scanId=<SCAN_ID>"
```
## 4. Ajax Spider Scan
To start the Ajax spider:
```
curl "http://localhost:8080/JSON/ajaxSpider/action/scan/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&url=http://192.168.1.13:9392&inScope=&contextName=&subtreeOnly="
```
To view the status:
```
curl "http://localhost:8080/JSON/ajaxSpider/view/status/?apikey=u39bcefvkn6is3k7jjmb3ebqpf" 
```
To view the results:
```
curl "http://localhost:8080/JSON/ajaxSpider/view/fullResults/?apikey=u39bcefvkn6is3k7jjmb3ebqpf" 
```
To stop the Ajax Spider:
```
curl "http://localhost:8080/JSON/ajaxSpider/action/stop/?apikey=u39bcefvkn6is3k7jjmb3ebqpf"
```
## 5. Passive Scanner
To view the number of records left to be scanned: 
```
curl "http://localhost:8080/JSON/pscan/view/recordsToScan/?apikey=u39bcefvkn6is3k7jjmb3ebqpf" 
```
To view the alerts of passive scan: 
```
curl "http://localhost:8080/JSON/core/view/alerts/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&baseurl=http://192.168.1.13:9392&start=0&count=<NUMBER>" 
```
# 6. Active Scan
To start the the active scan:
```
curl "http://localhost:8080/JSON/ascan/action/scan/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&url=http://192.168.1.13:9392&recurse=true&inScopeOnly=&scanPolicyName=&method=&postData=&contextId=" 
```
To view the the status of active scan:
```
curl "http://localhost:8080/JSON/ascan/view/status/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&scanId=<SCAN_ID>" 
```
To stop the active scan:
```
curl "http://localhost:8080/JSON/ascan/action/stop/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&scanId=<SCAN_ID>" 
```
To view the alerts:
```
curl “http://localhost:8080/JSON/alert/view/alerts/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&baseurl=http://192.168.1.13:9392&start=0&count=5000&riskId=” 
```
To view alerts by risk category:
```
curl “http://localhost:8080/JSON/alert/view/alertsByRisk/?apikey=u39bcefvkn6is3k7jjmb3ebqpf&url=http://192.168.1.13:9392&recurse=”
```
To get a list of all scan ids:
```
curl "http://localhost:8080/JSON/ascan/view/scans?apikey=u39bcefvkn6is3k7jjmb3ebqpf" 
```
# Reports
To get the copy of report in html format:
```
curl “http://localhost:8080/OTHER/core/other/htmlreport/?scanId=<SCAN_ID>&apikey=u39bcefvkn6is3k7jjmb3ebqpf” -o report.html   
```





























