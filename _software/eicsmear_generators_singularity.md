---
title: Eic-smear and Generators with Singularity
name: eicsmear_generators_singularity
category: singularity
layout: default
level: 0
---

{% include layouts/title.md %}

The simplest way to use eic-smear and a wide range of HERA generators is to take advantage of cvmfs and singularity to be placed directly into the  environment that's running natively at BNL. This combination is widely available at national labs, CERN, and many other facilities, as long as $CVMFS_REPOSITORIES  contains eic.opensciencegrid.org. But simple instructions for any system can be found below.

In all cases, a single line
```
%  singularity shell --writable -B /cvmfs:/cvmfs /cvmfs/eic.opensciencegrid.org/singularity/rhic_sl7_ext
```
and one setup script
```
% source /cvmfs/eic.opensciencegrid.org/x8664_sl7/MCEG/releases/etc/eic_bash.sh
```
will place you in the same environment where the libraries are installed natively. All libraries and executables are in your $PATH and $LD_LIBRARY_PATH, and the full packages can be found under $EICDIRECTORY. That means you can directly copy and paste instructions from https://eic.github.io/software/eicsmear.html and the README's of MCEG packages at https://gitlab.com/eic/mceg

For example
```
% cp -r $EICDIRECTORY/PACKAGES/eic-smear/tests .
% cp $EICDIRECTORY/PACKAGES/eic-smear/scripts/smearHandBook.cxx .
% pythiaeRHIC < tests/input.data.ep_hiQ2.20x250.small.eic
```
will create pythia e+P output.
```
% root -l
root[] gSystem->Load("libeicsmear");
root[] BuildTree ("tests/ep_hiQ2.20x250.small.txt");
root[] .L smearHandBook.cxx
root[] SmearTree(BuildHandBookDetector(), "ep_hiQ2.20x250.small.root")
```
will smear the result. The documentation in
https://eic.github.io/software/eicsmear.html
contains instructions on how to work with the result, and files in $EICDIRECTORY/PACKAGES/eic-smear/tests
provide practical examples. 

Also in the $EICDIRECTORY/PACKAGES and $EICDIRECTORY/bin are the generators BeAGLE, Milou, DJANGOH, RAPGAP, and PEPSI.

Of course, eic-smear and many MCEGs are also part of the escalate package:
https://eic.gitlab.io/documents/quickstart/
  Instructions and examples on how to use it in conjunction with PYTHIA8, how to write your own eJana plugins, how to perform analyses within JupyterLab or on the command line and much more are part of the included tutorial, and the recording of the recent tutorial is (soon) in our YouTube channel:

  https://www.youtube.com/channel/UCXc9WfDKdlLXoZMGrotkf7w

#### Singularity+cvmfs at JLAB:
On your computer
```  
ssh login.jlab.org
```
On login.jlab.org
```
ssh ifarm1802
```
ifarm1802.jlab.org
```  
module load /apps/modulefiles/singularity/3.4.0
```

#### Singularity+cvmfs anywhere
You can also install these easily on most UNIX systems. It's tested on a minimal Ubuntu 18.04 install via VirtualBox.  On OSX, using the VirtualBox solution is also recommended, since cvmfs isn't as well supported.
  
cvmfs:
```  
https://cernvm.cern.ch/portal/filesystem/quickstart
```
Singularity:
```
sudo apt install singularity singularity-container
```
Ensure that
CVMFS_REPOSITORIES contains eic.opensciencegrid.org
and when in doubt, use
CVMFS_REPOSITORIES=eic.opensciencegrid.org
(both usually in /etc/cvmfs/default.local)

#### At BNL
No need for containers, just add
```  
setenv EIC_LEVEL dev
source /cvmfs/eic.opensciencegrid.org/x8664_sl7/MCEG/releases/etc/eic_cshrc.csh
```  
to your ~/.cshrc.

(source /afs/rhic.bnl.gov/eic/restructured/etc/eic_cshrc.csh also works. But in the future we will probably switch completely to using the cvmfs mirror as the new standard location)

For more information on singularity, see Wouter's excellent
introduction here: https://eic.github.io/software/escalate_singularity_1.html
