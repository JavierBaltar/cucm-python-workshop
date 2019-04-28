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
The Administrative XML Web Service (AXL) is a XML/SOAP based interface that provides a mechanism for inserting, retrieving, updating and removing data from the Unified Communication configuration database. SOAP messages are defined by the CUCM Web Service Description Language (WSDL)

## Prerequisites:

- suds-jurko Python library
- Cisco AXLSQLToolkit 
- Cisco DevNet Sandboxes https://devnetsandbox.cisco.com/RM/Topology

![](ciscoDevnetSandboxes.gif)


## Code

```python
# Import modules
from os.path import abspath
from urllib.parse import urljoin
from urllib.request import pathname2url
import ssl
from suds.client import Client

# Create a Client object
WSDL = urljoin('file:', pathname2url(abspath('schema/AXLAPI.wsdl')))

# Allow insecure connections
if hasattr(ssl, '_create_unverified_context'):
    ssl._create_default_https_context = ssl._create_unverified_context

Connect_object = Client(WSDL, location='https://%s:8443/axl/' % ('10.10.20.1'),
                username='administrator', password='cisco')
                    
```
#### List end users and telephone numbers

```python
                    
response = Connect_object.service.listUser(
        searchCriteria={
            'userid': '%'
        },
        returnedTags={
            'userid': True,
            'telephoneNumber': True
        })
    
    print(response['return']['user'])
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
