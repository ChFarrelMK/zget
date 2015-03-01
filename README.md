zget
====

[![Build Status](https://travis-ci.org/nils-werner/zget.svg?branch=master)](https://travis-ci.org/nils-werner/zget)
[![Latest Version](https://pypip.in/version/zget/badge.svg)](https://pypi.python.org/pypi/zget/)
[![Supported Python versions](https://pypip.in/py_versions/zget/badge.svg)](https://pypi.python.org/pypi/zget/)
[![License](https://pypip.in/license/zget/badge.svg)](https://pypi.python.org/pypi/zget/)

A simple, Zeroconf-based, peer to peer file transfer utility, for situations where you and your peer are sitting next to each other and want to transfer a file quickly (and can shout the filename across the room).

Files and peers are recognized by the filename they want to transfer, not by their hostnames or IPs.

zget uses the fact that the filename is known to both parties as a security feature (*): The sender only advertises the sha1 sum of the filename on the network. Since the receiver must also know the filename, it can look for the sha1 using zeroconf.

If a match was found, a simple HTTP request is made: For transferring the file the actual filename is then requested from the sender. If this filename wasn't correct, the process is aborted.

Installation
------------

    $ pip install zget

Usage
-----

zget works both ways:

 - `zput` for sharing a file
 - `zget` for receiving


### Sharing

To share some nice pictures do:

    $ zput my_holiday_pictures.zip

then shout

> Hey Tom, I am zgetting you my_holiday_pictures.zip!

Tom will then do

    $ zget my_holiday_pictures.zip

Done.


### Receiving

You want to have some very important annual reports from Marcy:

    $ zget annual_reports.xlsx

then shout

> Hey Marcy, can you zget me annual_reports.xlsx?

Marcy then does

    $ zput annual_reports.xlsx

Boom. Done.

(*) Although I say "security feature" you should be aware that the filename and your data are sent in plaintext over the network. So do not use this tool for sensitive data (unless you're encrypting it first).
