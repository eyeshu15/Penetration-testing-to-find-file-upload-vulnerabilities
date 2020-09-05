# FUSE

FUSE is a penetration testing system designed to identify Unrestricted
Executable File Upload (UEFU) vulnerabilities. 
# Setup
## Install

FUSE currently works on Ubuntu 18.04 and Python 2.7.15.

1. Install dependencies
```
# apt-get install rabbitmq-server
# apt-get install python-pip
# apt-get install git
```

2. Clone and build FUSE
```
$ git clone https://github.com/WSP-LAB/FUSE
$ pip install -r requirement.txt
```

* If you plan to leverage headless browser verification using selenium, please
install Chrome and Firefox web driver by refering [selenium
document](https://selenium.dev/selenium/docs/api/py/index.html).

## Usage
### Configuration

* FUSE uses a user-provided [configuration file](configs/default-credential.conf)
that specifies parameters for a target PHP application. The script must be
filled out before testing a target Web application. You can check out
[README](configs/README.md) file and [example configuration files](configs).


* Configuration for File Monitor (Optional)
```
$ vim filemonitor.py

...
 10 MONITOR_PATH='/var/www/html/' <- Web root of the target application
 11 MONITOR_PORT=20174            <- Default port of File Monitor
 12 EVENT_LIST_LIMITATION=8000    <- Maxium number of elements in EVENT_LIST
...
```


### Execution

* FUSE

```
$ python framework.py [Path of configuration file]
```

* File Monitor

```
$ python filemonitor.py
```

* Result
  * When FUSE completes the penetration testing, a [HOST] directory and a [HOST_report.txt] file are created.
  * A [HOST] folder stores files that have been attempted to upload.
  * A [HOST_report.txt] file contains test results and information related to files that trigger U(E)FU.



