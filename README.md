# OSWASP-ZAP Scanner Documentation 

## 1. INSTALLATION
Download the scanner using the following command: 
`wget https://github.com/zaproxy/zaproxy/releases/download/v2.12.0/ZAP_2.12.0_Linux.tar.gz`
Extract the downloaded tar file: 
```tar -xvzf ZAP_2.9.0_Linux.tar.gz ```
Change the directory to the ZAP folder: 
```cd  ZAP_2.12.0```
## 2. CONFIGURATION
Start zap GUI using this command: 
```./zap.sh -port 8080```
OSWASP ZAP GUI will load up. Now go to Tools>Options>API>API Key and copy the key from there and then exit the GUI by using Ctrl+C in the CLI. 
Start daemon mode with configured key using the following command: 
```./zap.sh -daemon -config api.key=<API_KEY> -port 8080 &```
## 3. Spider Scan
To start the Spider scan (Response: Scan ID): 
``` curl "http://localhost:8080/JSON/spider/action/scan/?apikey=<API_KEY>&url=<URL>&contextName=&recurse=true"```
the “recurse” parameter is used to specify whether to recursively scan a target. This means that ZAP will follow any links in the target and scan the linked pages as well. You can specify a maximum depth for the recursion using the “maxChildren” parameter: 
```curl "http://localhost:8080/JSON/spider/action/scan/?apikey=<API KEY>&url=<URL>&contextName=&recurse=true&maxChildren=<NUMBER>"```
To view the scan status/ percentage of work done: 
```curl "http://localhost:8080/JSON/spider/view/status/?apikey=<API_KEY>&scanId=<SCAN_ID>"```
To view the scan results: 
```curl "http://localhost:8080/JSON/spider/view/results/?apikey=<API_KEY>&scanId=<SCAN_ID>"```
To stop the Scanning 
```curl "http://localhost:8080/JSON/spider/action/stop/?apikey=<API_KEY>&scanId=<SCAN_ID>"```
