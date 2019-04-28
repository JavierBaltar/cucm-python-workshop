# cucm-python-workshop
Cisco Call Manager Python AXL API Programming Tools

<p align="center">
  <a href="#Getting-Started">Getting Started</a> •
  <a href="#Code">Code</a> •
  <a href="#Next-Steps">Next Steps</a> •
  <a href="#related">Related</a> •
  <a href="#Authors">Authors</a>
</p>

## Getting Started


### Relevant Libraries

zeep

`$ python --version`

### Cisco DevNet Sandboxes
https://devnetsandbox.cisco.com/RM/Topology

![](ciscoDevnetSandboxes.gif)

### Toolkit

- Python. I am using Python 2 and PyCharm IDE.
- A CUCM instance
- AXLSQLToolkit 
- zeep
- A Coffee mug 

## Code

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

 

## Authors

* **Javier Baltar** - *Initial work* - [GitHub](https://github.com/JavierBaltar)
