# cucm-python-workshop
Cisco Call Manager Python AXL API Programming Tools
<p align="center">
  <a href="#Getting-Started">Getting Started</a> •
  <a href="#Prerequisites">Prerequisites</a> •
  <a href="#Code">Code</a> •
  <a href="#Next-Steps">Next Steps</a> •
  <a href="#related">Related</a> •
  <a href="#Authors">Authors</a>
</p>

## Getting Started

## Prerequisites:

- suds-jurko package 
- Cisco AXLSQLToolkit 
- Cisco DevNet Sandboxes https://devnetsandbox.cisco.com/RM/Topology

![](ciscoDevnetSandboxes.gif)


## Code

```python
from suds.client import Client  
   
# Define AXL Authentication Credentials for Cluster  
username = "username"  
password = "password"  
   
# Define AXL URL for Cluster  
url = "https://CUCM:8443/axl/"  
   
# Define WSDL Location 
wsdl = "file:///C:/pathto/AXLAPI.wsdl"  
   
# Build SUDS Client Connection  
client = Client(location=url, url=wsdl, retxml=False, username=username, password=password)
# Open and read csv File, split on new line
data = open("login.csv", "r").read().split("\n")
   
# loop through and break out individual components  
for line in data[1:]:  
  mac,profile,uid = line.split(",") 
  print(mac,profile,uid)
  
  # Call client service "doDeviceLogin" method and pass in the parameters  
  x = client.service.doDeviceLogin(deviceName=dn, loginDuration='0', profileName=pn, userId=uid)  
  print(x)
```

## Next Steps
### Export to CSV 

```python
import csv
 
callmanagerdata = [["customer", "version"],
          ['CustomerA', '10.5'],
          ['CustomerB', '11.5']]
 
File = open('callmanager-data.csv', 'w')
with File:
    writer = csv.writer(File)
    writer.writerows(callmanagerdata)
     
print("Writing complete!")
```

### Export to SQLite

```python
import sqlite3
con_obj = sqlite3.connect("callmanager-data.db")
with con_obj:
            cur_obj = con_obj.cursor()
            cur_obj.execute("""CREATE TABLE cucm_version(customer text, version text)""")

print ("Table created!")
```

## Related

* [Cisco Administrative XML (AXL)](https://developer.cisco.com/site/axl/) - AXL is a Soap based API that enables remote provisioning of Unified CM

* [Python Suds-jurko Library](https://pypi.org/project/suds-jurko/) - Suds is a lightweight SOAP-based web service client for Python licensed under LGPL

* [Python Zeep Library](https://pypi.org/project/zeep/) - A fast and modern Python SOAP client

 

## Authors

* **Javier Baltar** - *Initial work* - [GitHub](https://github.com/JavierBaltar)
