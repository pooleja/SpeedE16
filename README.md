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
Running upload/download test against: ::
Created temp file: /home/ubuntu/SpeedE16/client-data/EHZ8X25KSSSECL7OS29N
Generated a hash of the temp file: 2d81e1ec98c9b0cf48990463f1965784766ab107d9000e62406c9d1de61167a1
Uploaded the file.  Elapsed time: 0.753319501876831
Upload shows success
Downloading: http://[::]:8016/download?file=P354TQLHY42867SZTJ5V to: /home/ubuntu/SpeedE16/client-data/P354TQLHY42867SZTJ5V
Downloaded the file.  Elapsed Time: 0.6069188117980957
Download shows success
Deleted the temp downloaded file: /home/ubuntu/SpeedE16/client-data/EHZ8X25KSSSECL7OS29N
Upload Speed: 10.619664007195732 Mbps
Download Speed: 13.181334709825023 Mbps
```
Here you see the upload and download speeds are reported when running against localhost.

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
