# SpeedE16

## Overview
SpeedE16 is a server that runs on the 21 network to allow clients to test bandwidth between nodes.  A client can upload/download
files to the server in order to test how long it takes.

A SpeedE16 server can also be asked from a remote client to test the speed between itself and another server running SpeedE16.

## Installation
### Set up the server
To get things up and running:

```
$ git clone https://github.com/pooleja/SpeedE16.git
$ cd SpeedE16
$ sudo easy_install3 pip
$ sudo pip3 install -r requirements.txt
```

Next, start up the server:
```
$ python3 speedE16-server.py -d
```

Next, verify it works by running the client to upload and download a file:
```
$ 21 buy http://localhost:8016/server-status
{
    "numQueudJobs": 0,
    "numRunningJobs": 0,
    "success": true
}
```
### Make Sure it Stays Running
To ensure the server stays running across reboots, you can create a reboot cron job.  This will ensure it will be restarted any time the device comes back online.

To open the cron file:
```
$ crontab -e
```

Edit the file and add a reboot line (replace the path):
```
@reboot cd /your/path/to/SpeedE16/ && python3 speedE16-server.py -d
```

Now you can reboot the device and ensure it is running:
```
$ ps aux | grep python3
twenty     545  2.2  2.5  39928 25884 ?        Sl   17:35   0:07 python3 speedE16-server.py
```
