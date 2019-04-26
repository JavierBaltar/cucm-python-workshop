<p align="center">
  <a href="#Getting-Started">Getting Started</a> •
  <a href="#Prerequisites">Prerequisites</a> •
  <a href="#Installing">Installing</a> •
  <a href="#credits">Credits</a> •
  <a href="#related">Related</a> •
  <a href="#license">License</a>
</p>

# cucm-python-workshop
Cisco Call Manager Python AXL API Programming Tools

### Getting Started


#### Relevant Libraries

zeep

`$ python --version`

#### Cisco DevNet Sandboxes
https://devnetsandbox.cisco.com/RM/Topology

![](ciscoDevnetSandboxes.gif)

#### Toolkit

- Python. I am using Python 2 and PyCharm IDE.
- A CUCM instance
- AXLSQLToolkit 
- zeep
- A Coffee mug 


### Export to CSV 

### Export to SQLite

`$ import sqlite3

con_obj = sqlite3.connect("test.db")
with con_obj:
            cur_obj = con_obj.cursor()
            cur_obj.execute("""CREATE TABLE books(title text, author text)""")

print ("Table created")`

`

### Licence
