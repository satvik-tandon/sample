# SSLYZE DOCUMENTATION

## 1. INSTALLATION
```
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:deadsnakes/ppa
apt install python3.10 -y 
apt-get -y install python3-pip 
pip install sslyze==5.0.6 
```
## 2. SCANNING AND REPORTING
Use ```sslyze –h``` to check out scanning commands. The following sample command will scan for ssl 2.0 support in ```google.com``` and save the result in ```hello.json``` in the ```/root``` directory:
```
sslyze --sslv2 google.com --json_out /root/hello.json
```
