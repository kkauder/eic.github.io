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


## ESCalate

<img src="{{ '/assets/images/diagrams/escalate/escalate-logo.png' | relative_url }}" width="150" style="float:left; padding: 10px 20px 10px 20px;"/>

**ESCalate** is a modern framework, which brings together Monte Carlo event generators, 
[Eic Smear](https://gitlab.com/eic/eic-smear.git) for fast simulations, 
[G4E](https://gitlab.com/eic/escalate/g4e.git) for full detector simulations and
[eJana](https://gitlab.com/eic/escalate/ejana.git) for analysis and reconstruction.
The framework is modular on package and library levels, provides command line interface, 
python and Jupyter APIs for user analysis and ensures data consistency between its loose coupled parts.

<div style="clear: left;"></div>

To run ESCalate: 

- [Run in docker on your machine (Linux, Mac, Win)](https://eic.gitlab.io/documents/quickstart/#ESCalate)
- [Run in singularity on lab farms (or also your machine)]()
[https://gitpod.io/#https://gitlab.com/eic/escalate/workspace](gitpod)

<br>

#### MCEG


<img src="{{ '/assets/images/diagrams/escalate/q2_jb.png' | relative_url }}" width="200" style="float:left; padding: 0px 20px 10px 20px;"/>

**MCEG examples**. [Examples](https://gitlab.com/eic/escalate/workspace/-/tree/master/01_fast_sim_tutorial) of using Pythia6 with radiative corrections and Pythia8+Dire to generate DIS events 
and process them with fast simulations added. With eJana you can instantly see the resulting DIS plots (see Validation section of eJana below)

<div style="clear: left;"></div>

**HepMC3 and file converter** As [HepMC3](https://gitlab.cern.ch/hepmc/HepMC3) was named "stable" with the 3.2.1 release, 
we switched eJana to work with HepMC3 (previously it worked with HepMC2), which can read files of both versions.

We also now provide ```hepmc_writer``` plugin. As eJana can read a number of Lund file formats (Beagle, HepEvents, PythiaEIC, etc.) it can be easily used as a converter
of Beagle and other files to HepMC3 which later can be processed with Delphes, in [python](https://pypi.org/project/HepMC3/), etc.
As there are users adapting [Delphes for EIC](https://github.com/miguelignacio/delphes_EIC). 
We are working on verification and validation of using the feature in Delphes workflow.


Example command to convert Beagle file to HepMC3:

```bash
ejana -Pplugins=beagle_reader,hepmc_writer beagle_file.txt
```

Beagle and other generators provide extended info such as true x, Q2 and other DIS values, one of the advantages of HepMC3
is that it allows to have custom attributes for events and particles, i.e. allows to save those values. At this point only 
basic values are converted, but we are working to ship them all for Beagle and PythiaEIC.




#### Fast simulations 



<img src="https://gitlab.com/eic/escalate/smear/-/raw/master/logo.png" width="150" style="float:left; padding: 10px 20px 10px 20px;"/>

**Fast simulations made simple**. Now it is easy to smear any EIC MCEG supported file as simple as running a console command:

```bash
smear my_mc_file.txt
```
See the [documentation](https://gitlab.com/eic/escalate/smear/) for how to easily select a detector, its versions, and various other options

<div style="clear: left;"></div>

Smear tool can use different *smearing engines* under the hood. Eic-Smear C++ API is the main one, 
but one can also select detectors from Simple Smear written by Yulia Furletova. 
We are now considering integration of Delphes as the third engine.

The ```smear``` command requires installation of ROOT and other packages, so we have instructions for different
scenarios:

1. [Run docker on your local machine](https://gitlab.com/eic/escalate/smear/-/blob/master/simple_instruction_docker.md),
2. [Using singularity (at labs or locally)](https://gitlab.com/eic/escalate/smear/-/blob/master/simple_instruction_singularity.md)
3. [Run directly on IFarm or JLab Jupyterhub](https://gitlab.com/eic/escalate/smear/-/blob/master/simple_instruction_ifarm.md)
 

#### Full simulations

G4E has many changes related to forward and far forward region such as new ZDC, virtual tracking for B0 tracking, etc.
(Results are presented in Pavia's meeting and on [Meson and Kaon structure workshop](https://indico.bnl.gov/event/8315/overview))


<img src="{{ '/assets/images/diagrams/escalate/G4E_with_zdc.png' | relative_url }}" height="250" style="float:left; padding: 10px 20px 10px 20px;"/>

<img src="{{ '/assets/images/diagrams/escalate/g4e_lambda_decay_example.png' | relative_url }}" height="250" style="float:left; padding: 10px 20px 10px 20px;"/>


<div style="clear: left;"></div>


#### Reconstruction and analysis in eJana

**Standalone plugins**  You can always analyze the output of the ESCalate framework with ROOT macros, pyROOT or uproot. 
But to integrate your reconstruction algorithm, physics analysis or extend eJana, users can write their own plugins. 
Assuming that the most convenient workflow keep users' analysis in their own separate repositories, 
we added examples of standalone plugins, which work completely independently of eJana location, 
so no modification of the central repository is needed. 
The [standalone plugins examples are here](https://gitlab.com/eic/escalate/plugins) (and will be expanding).
 
It is also possible to use pyjano to generate and/or compile new plugins on fly. 
Newly generated plugins instantly work with command line, python or in Jupyter. 

**Validation and Analysis**. We added some validation and analysis plugins for ejana, that allows checking fast simulation
results as well as to build DIS plots (x, Q2, t, etc.) with a simple CLI command. 

Here is an example of how to read a Beagle file, build DIS plots with new ```dis``` plugin and write a ROOT tree, which you can analyse with ROOT 
macros or other tools.  

```bash
ejana -Pplugins=beagle_reader,dis,event_writer beagle_file.txt
```

<img src="{{ '/assets/images/diagrams/escalate/tracking_fit_crop.png' | relative_url }}" height="250" style="float:left; padding: 10px 20px 10px 20px;"/>

**Reconstruction**. Recently we've been rehauling our reconstruction part. At this moment we do track fitting through Genfit and vertexing through ACTS and working with ACTS developers on implementing full
ACTS tracking+vertexing so one can select and compare both. We also plan to use ACTS wider and put ACTS Fatras (Fast Tracking Simulation) to G4E. 

<div style="clear: left;"></div>
We try to keep escalate packages easily installable on users machines ([using ejpm](https://gitlab.com/eic/escalate/ejpm)). ACTS requires C++17 and the latest Boost libraries and it might be a problem to build it even
on not very old machines without attaching CVMFS or using Conda. So we made ACTS a peer dependency - if one installs it, ejana is build with its reconstruction plugins. Without ACTS ejana it built with only fast simulation modules and minimal dependencies. 

```
ejpm install acts
ejpm install genfit
ejpm install ejana   # add --force flag to recompile existing version
```




#### Containers

- **In Cloud!**. One can now open ESCalate Jupyter examples in Binder. So no installation needed!  
   [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gl/eic%2Fescalate%2Fworkspace/master)  
   *(It might take some time to load - Binder is free, has limited resources, while our image is large because of ROOT, 
   Geant4 and other packages)* 
   Binder provides limited resources, but we work on adding an ability to submit a job to OSG right from the Jupyter.
   
   For some time now we also have ESCalate image running on [JupyterHub at jupyterhab.jlab.org](https://gitlab.com/eic/escalate/workspace/-/blob/master/RemoteWork.md)
   Hopefully soon we will have it working on BNL JupyterHub also.
   

- **Containers versioning**. One can now get the [full versions table](https://gitlab.com/eic/containers) of all the softare 
   of ESCalate images and [the images change log](https://gitlab.com/eic/containers/-/blob/master/CHANGELOG.rst).
   

#### Help and support

<a href="https://join.slack.com/t/eicug/shared_invite/zt-djjvylq9-zmRphsvRLpDBiYb_jJwgCQ">
<img src="{{ '/assets/images/diagrams/escalate/slack_qr.png' | relative_url }}" height="250" style="float:left; padding: 10px 20px 10px 20px;"/>
</a> 

Get to our Slack channel to get help with the software and participate in other channels like YP analysis. 

<br><br> 
 
