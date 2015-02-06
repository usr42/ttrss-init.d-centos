# ttrss-init.d-centos

This is an init.d script for CentOS 6 to start the Tiny Tiny RSS update script as daemon. The ttrss update script, which updates the news articles, does not automatically daemonize (e.g. detach from the terminal). So you need a workaround to let it run in the background. This script allows to run the update script as a service and even start it at boot time.

Requirements
------------
* a CentOS (6) system, maybe other versions of CentOS
* **daemonize** must be installed (can be found at EPEL)
  *make sure EPEL is configured as repository
  * execute:
`sudo yum install daemonize`

Installation
------------
* Download the [tt-rss script](https://raw.githubusercontent.com/usr42/ttrss-init.d-centos/master/tt-rss) or the [whole repository](https://github.com/usr42/ttrss-init.d-centos/archive/master.zip) or clone this repository with following command:  
`git clone https://github.com/usr42/ttrss-init.d-centos`
* Copy the tt-rss script to /etc/init.d/tt-rss
* Check if the variables at the start of the script fit your system.
* Create the logfiles and make them writable for the script:
```touch /var/log/tt-rss-update.log /var/log/tt-rss-update-error.log  
chown apache:apache /var/log/tt-rss-update.log /var/log/tt-rss-update-error.log```
* Make the script executable and let it automatically start when system boots:
```chmod +x /etc/init.d/tt-rss  
chkconfig tt-rss on  
service tt-rss start```

Thanks to
---------
* Tiny Tiny RSS http://tt-rss.org
* [daemonize](http://software.clapper.org/daemonize/) and its developer [Brian M. Clapper](https://github.com/bmc/)
