# Introduction
It's kind of a pain to find your Raspberry Pi's ip address when you connect it to a new network. I created this tool to quickly find my raspberry pi.

This is version 2. Version 1 is written in Perl, and everything is in clear text. This time, I decided to learn AES encryption.

# Description

You need Python on your machine and on the Pi.

There are two programs needed.

- rasPyFinderd: A little daemon that runs on the Pi.
- rasPyFinder: A Program that runs in a linux shell (might work on windows too... untested).

First, pifinder broadcasts an encrypted message on the network. Upon reveiving that message, the daemon responds with it's hostname and ip addresses.

# Installation

### On the Pi

To install the daemon on the Pi (Requires root access or sudo):
- Navigate to the directory where you want to put the script (ex: cd /usr/local/bin)
- `git clone https://github.com/michaudm/rasPyFinder.git`
- `cd rasPyFinder`
- Edit rasPyFinderd.service with your favorite editor (vi, nano, ...)
- Change ExecStart=<Your Path Here> to add the path to your rasPyFinder (ex: ExecStart=/usr/local/bin)
- Save your file (nano-> Ctrl+X, vi-> :wq)
- `sudo cp rasPyFinder.service /etc/systemd/system`
- `sudo systemctl daemon-reload`
- `sudo systemctl enable rasPyFinder.service`  
The daemon should start automatically after the next reboot.

If you want to start it immediatly: `sudo service rasPyFinder start`


### On your PC

- Navigate to the directory where you want to install the script.
- `git clone https://github.com/michaudm/rasPyFinder.git`
- `cd rasPyFinder`
- `chmod 755 rasPyFinder`

Run with `./rasPyFinder` in a linux shell

# TODO

- Almost everything. This readme has been copied from the first project.

# Note

All Comments in the scripts are in french... sorry.
