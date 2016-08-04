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
Server running...
```

Next, verify it works by running the client to upload and download a file:
```
$ python3 client.py
Running upload/download test against: 0.0.0.0
Created temp file: /home/ubuntu/SpeedE16/client-data/RLUHL142GN0OMISBMGJ1
Uploaded the file.  Elapsed time: 0.6815180778503418
Deleted the temp uploaded file: /home/ubuntu/SpeedE16/client-data/RLUHL142GN0OMISBMGJ1
Upload shows success
Downloading: http://0.0.0.0:8016/download?file=71KE80KRQ3MZPE0TOXKN to: /home/ubuntu/SpeedE16/client-data/71KE80KRQ3MZPE0TOXKN
Downloaded the file.  Elapsed Time: 0.6839721202850342
Download shows success
Deleted the temp downloaded file: /home/ubuntu/SpeedE16/client-data/RLUHL142GN0OMISBMGJ1
Error: File digests to not match.
Uploaded File Digest: 14575a5b4f42353db6af278d195e246ef979ec5278c9c41bded4d1a413383139
Downloaded File Digest: dc23933049d8b06808e15916d9cc735bd5c82fc87e5f3a970442f6fc04f5a275
Upload Speed: 11.738500063320055 Mbps
Download Speed: 11.696383175188677 Mbps
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
