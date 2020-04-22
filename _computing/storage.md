---
title: Storage
description: Storage
name: storage
layout: default
level: 0
---

{% include layouts/title.md %}

#### Pre-generated Monte Carlo data at BNL

The EIC group at BNL has a large amount (26 TB and growing) of
pre-generated events from Pythia, Milou, Djangoh, and others available
for download via NextCloud/BNLbox at
```
https://bnlbox.sdcc.bnl.gov
```

You can log in using a guest account
```
eicslinger@gmail.com
```
The password will be changed semi-frequently and made available to you
upon request.

A WEBDAV interface exists and can be accessed under the base url
```
bash
export slingerurl='https://bnlbox.sdcc.bnl.gov/remote.php/dav/files/eicslinger@gmail.com'
csh
setenv slingerurl 'https://bnlbox.sdcc.bnl.gov/remote.php/dav/files/eicslinger@gmail.com'
```

##### Download via web interface and curl

You can navigate and download individual files directly from the web
interface.

To use the curl instead, identify the path to it from the web
interface and use
```
curl -O -u ‘eicslinger@gmail.com:<password>'
${slingerurl}/path/to/file
```
For example,
```
curl -O -u 'eicslinger@gmail.com:' ${slingerurl}/EIC_Data/PYTHIA/ep/TREES/5x50.lepton.png
```

##### Navigation and Download via cadaver
A more feature-rich command line tool is cadaver,
http://www.webdav.org/cadaver/.

You enter a session with the username and password:
```
r$ cadaver $slingerurl 
Authentication required for BNL Box on server `bnlbox.sdcc.bnl.gov':
Username: eicslinger@gmail.com
Password: 
dav:/remote.php/dav/files/eicslinger@gmail.com/>
```
And you can use ls, cd, get, etc. to navigate the file system.

To avoid repeatedly entering the credentials, you can create a .netrc
file in your home directory:
```
 cat ~/.netrc
machine bnlbox.sdcc.bnl.gov
login eicslinger@gmail.com
password <password>
```

##### Download entire directories
For entire directories at once, we provide a ruby script at
[need to upload to github or so].
To use it, first prepare a file called .bnlbox in your home directory
and give it the right permissions:
```
$ cat ~/.bnlbox 
user:eicslinger@gmail.com
pwd:<password>
$ chmod 600 ~/.bnlbox
```
Then, you can use it to recursively download entire directories, e.g.
```
ruby copy_bnl_box.rb box:/EIC_Data/PYTHIA/ep/TREES
```
where the "box:" prefix makes the usage uf $slingerurl
unnecessary. Note that this script is still in development, and
otherwise convenience and feedback to the user are right now rather sparse.

##### IMPORTANT #####
* These are shared credentials for the whole community. With the
  password, you have the power to change it, turn on additional
  security features and so on. Please DO NOT do so, since it will make
  it unusable for everyone else.

* You cannot log into this gmail account, and emails sent to it will
  be ignored. It is purely a throwaway account.

* Note to RCF users, you can access this data directly at
```
/gpfs02/eic/DATA
```

* To repeat for emphasis, DO NOT change the password or otherwise
  impede others from using it. If this mechanism is repeatedly abused,
  the community guest account will be deleted and sharing can only be
  done individually on request.



#### Adding to the collection ####
There is more than enough space available to fulfill all storage needs
of the Yellow Report effort as reported in the recent poll to working
groups. To make use of it, please contact the software working group
so we can determine together the most efficient way to upload your
data and make it accessible to the whole community!







