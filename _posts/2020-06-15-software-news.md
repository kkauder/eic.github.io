---
title: Software News June
author: Markus Diefenthaler
layout: default
symbol: glyphicon-calendar
until: 2020-12-31
---
<p/>

<img src="{{ '/assets/images/site/EICUG-SWG-News-Banner.png' | relative_url }}" width="800"/>

The EICUG Software Working Group is working on physics and detector simulations that enable for the Yellow Report Initiative a quantitative assessment of the measurement capabilities of the EIC detector(s) and their physics impact. The common simulation tools and workflow environment being setup by the working group allow the EICUG to pursue Yellow Report studies in a manner that is accessible, consistent, and reproducible to the EICUG as a whole.



#### Software Update
In our first Software News, updates on eic_smear and ESCalate are included. Further updates on these and other packages will be in future newsletters. 

#### Worldwide data storage and sharing solution with Petrel

We are happy to announce that we can offer the community
a large new data storage allocation on Petrel
to address the increasing need for an easy-to-access high-performance
storage solution for the Yellow Report Initiative.
Petrel is a Globus-enabled data service for researchers that provides a 
simple and intuitive interface for self-managed project-based data 
sharing. Our Petrel allocation is 100TB (more can be added if needed). 
The existing pre-grenerated Monte-Carlo data from BNL (13TB and growing)
are mirrored in the `BNL-gpfs02-data` directory, and available JLab data
will be added soon as well.  You can find more info on Petrel 
[here](https://petrel.alcf.anl.gov/). 
Petrel is supported and maintained by ALCF.

​
Because of the Globus back-end it is easy to move, share and discover 
data via a single interface, regardless if you are working with on a HPC 
facility, computer farm or your local machine. All major laboratories 
and supercomputing facilities, as well as most universities support 
Globus. This allows you to use your existing laboratory (ANL, BNL, JLab, 
LBNL, etc.) or even university credentials to access the files. To 
access the storage space, [log in to globus.org](https://globus.org) 
with your existing laboratory or university credentials and access the 
`petrel#eic` endpoint. It's as easy as that!

​
Write-access is available to anyone in the EIC Globus Group.
If you want write-access to the storage space, 
or if you encounter any issues, 
you can contact [Sylvester](mailto:sjoosten@anl.gov) or 
[Markus](mailto:mdiefent@jlab.org).
​

##### eic-smear

###### Stand-alone detector repository with versioning

We have separated the detector smearing scripts from the main code. If you have eic-smear installed, use [this repository](https://github.com/eic/eicsmeardetectors) to quickly select and experiment with different versions simply via
```
$ git clone https://github.com/eic/eicsmeardetectors.git
$ root -l
root[] gSystem->Load("libeicsmear")
root[] .L eicsmeardetectors/SmearHandBook_1_2.cxx
root[] SmearTree(BuildHandBook_1_2(), "in.root", "out.root")
```
The README.md, which nicely displays on the github page, has a table with all available versions and more instructions.
Improvements to eic-smear for comfortable compiling a local detector script and/or using a library of all available ones is in the works.


###### Advanced usage example

In order to demonstrate some of the more subtle issues of eic-smear output, we created an [example project](github.com:eic/eicsmear-jetexample.git).

The repo just has two cxx files, meant to be self-documenting, and a detailed README. The first example demonstrates how to use just smeared output, the second how to compare to the truth level and/or how to extract some information from the truth level that should be in the smeared level but as of now isn't yet.

It is intentionally meant to be stand-alone, with a very simple Makefile and no cmake complications.
Please note that while the sample analysis is jet-specific, this is purely because that is a natural application to show 4-vector calculations from partial information.


##### Fun4All
Fun4All is a well established simulation/reconstruction framework initially developed to reconstruct and analyze data from the PHENIX experiment. In recent years it has provided the simulations to shepherd the sPHENIX experiment from the first drawing on a napkin all the way through CD1. For the EIC it was used to develop a concept for an [EIC detector based on the Babar magnet](https://arxiv.org/pdf/1402.1209.pdf) and [an EIC detector Built around the sPHENIX Solenoid](https://indico.bnl.gov/event/5283/attachments/20546/27556/eic-sphenix-dds-final-2018-10-30.pdf). It can be used interactively (run a few events, have a look, run a few more, look again) as well as running massive productions on large farms (and as of recent also on CORI and on the OSG). For more details (and program flow charts) have a look at the [presentation](https://indico.in2p3.fr/event/18281/contributions/71607/) at the 2019 EIC User Group Meeting.

###### New developments
All fieldmaps (Babar, Beast and JLeic) are now available. They can be chosen on the ROOT macro level for details have a look at this [tutorial](https://github.com/eic/fun4all_eic_tutorials/tree/master/MagneticField).

<img src="{{ '/assets/images/diagrams/fun4all/fun4all_fieldmaps.png' | relative_url }}" width="800"/>

The magnetic field was verified using charged geantinos (shown here are 0.5, 1, 2, 3 GeV/c) compared to constant solenoidal fields as shown on the right for the Beast magnet.

Importing detectors via gdml files has its quirks but is now well understood and fully supported. It is not possible to do this generically since one has to address the volumes by name but this only needs minor modifications to existing code and is largely cut and paste.

<img src="{{ '/assets/images/diagrams/fun4all/fun4all_gdml.png' | relative_url }}" width="800"/>

Here are the latest additions to our selection of implemented detectors (all of which can be combined in a ROOT macro). We have a detailed model of the [Beast magnet](https://github.com/eic/fun4all_eicdetectors/tree/master/source) (already used in the fieldmap plots) as well as the [*All Silicon Tracker*](https://github.com/eic/g4lblvtx) and the EIC beam pipe.

The ability to combine these (and other detectors) at will is shown here:

<img src="{{ '/assets/images/diagrams/fun4all/fun4all_allsilicon.png' | relative_url }}" width="800"/>

where the *All Silicon Tracker* is put inside the Beast magnet and is being used as central tracker inside the EIC detector based on the Babar magnet.


###### Verification
Fun4All is also being used to reconstruct test beam data which allows a direct comparison of simulations with data. sPHENIX has performed extensive test beam campaigns for its detectors at energies which are relevant for EIC detectors. The calorimeter test beam results have been [published](https://ieeexplore.ieee.org/document/8519782) recently, the analysis of TPC and Maps detector data is ongoing. A good agreement with previous EICRoot based simulations has been found for the All Silicon Tracker ([slide 8](https://indico.bnl.gov/event/7894/contributions/37609/attachments/28098/43125/200514_AllSi_in_Fun4All_2.pdf))

###### Help
Help is available via [our support channel in Mattermost](https://chat.sdcc.bnl.gov/eic/channels/fun4all-software-support), non Scientific Data Center Accounts need an invite - contact us
