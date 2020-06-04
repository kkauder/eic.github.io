---
title: Software News April
author: Markus Diefenthaler
layout: default
symbol: glyphicon-calendar
until: 2020-12-31
---
<p/>

<img src="{{ '/assets/images/site/EICUG-SWG-News-Banner.png' | relative_url }}" width="800"/>

The EICUG Software Working Group is working on physics and detector simulations that enable for the Yellow Report Initiative a quantitative assessment of the measurement capabilities of the EIC detector(s) and their physics impact. The common simulation tools and workflow environment being setup by the working group allow the EICUG to pursue Yellow Report studies in a manner that is accessible, consistent, and reproducible to the EICUG as a whole.

#### Communication 
The EICUG Software Working Group will start to announce software updates, known bugs, and other software related news on the [eicug-software@eicug.org](mailto:eicug-software@eicug.org) mailing list. While summaries of the announcements will be shared on [eicug-software@eicug.org](mailto:eicug-software@eicug.org) and the monthly newsletter, we encourage all working groups to subscribe to the [eicug-software@eicug.org](mailto:eicug-software@eicug.org).

#### JupyterHub
We are preparing JupyterHub resources at BNL and JLAB that will allow you to run the EIC Software in the cloud and to easily share your analyses with other users. A prototype is being tested at JLAB. 

#### Support us to support you better
The common simulation tools and workflow environment can only grow with user input. The EICUG Software Working Group asks interested users to join our support team to ensure fast response to user requests. This is an ideal opportunity to learn more about the software and its development. 

#### Tutorials 
The tutorials for fast and detector full simulations are available on the <a href="https://www.youtube.com/channel/UCXc9WfDKdlLXoZMGrotkf7w" target="_blank">EICUG YouTube channel</a>.

##### Uproot and Awkward Array Tutorial
* Jim Pivarski (Princeton), known for innovative software in DIANA/HEP, IRIS-HEP and other projects, will give tutorials on how to process and analyze Root files with pure Python libraries: uproot and awkward array The tutorials are aimed for anyone who would like to learn more about using data science tools in Python for Nuclear Physics analysis. 
* Wednesday, April 8, at 10:00 a.m. (EDT)
* Remote access will be provided via BlueJeans: [https://bluejeans.com/920347364](https://bluejeans.com/920347364)
* The tutorial will be recorded. 
* More details are available on: [https://indico.bnl.gov/event/8242/](https://indico.bnl.gov/event/8242/)

##### Advanced Fast Simulations Tutorial
* Dmitry Romanov (JLAB) and Kolja Kauder (BNL) will give an advanced tutorial on fast simulations based on the feedback and requests of the last months. 
* Thursday, April 9, at 10:00 a.m. (EDT)
* Remote access will be provided via BlueJeans: [https://bluejeans.com/920347364](https://bluejeans.com/920347364)
* The tutorial will be recorded. 
* More details are available on: [https://indico.bnl.gov/event/8243/](https://indico.bnl.gov/event/8243/)

#### Software Update
In our first Software News, updates on eic_smear and ESCalate are included. Further updates on these and other packages will be in future newsletters.

##### eic_smear 
__Legacy version (1.0.3-final)__ The version used for the EIC White Paper (with a minor fix and some new tests) was fixed to 1.0.3-final for preservation.

__Yellow Report versions (1.0.4+)__ The current version, tentatively named 1.0.4-RC, has a few impactful updates:
1. The code was made compliant to `C++17`, the latest stable `C++` standard. 
2. A bug was found and fixed that translated negative smeared values into NaN. This affects only a small phase space, mostly for very small phi values, but it is nevertheless recommended to update at your earliest opportunity and check for differences in your studies.
3. Calculations for x and y according to the Jacquet Blondel method can produce a slew of warnings because values slightly smaller than 0 or larger than 1 are generated through roundoff errors. This is fixed. 
4. Testing and Q&A macros have been added in the `tests/` directory. 

In the works: 
* Implementations according to the Electron-Ion Collider Detector Requirements and R&D Handbook: Once out, this should be the default used by everybody until vetted reference detectors are compiled. Note that none of the existing smearers were ever meant as truly representative of their namesakes, mostly as starting points.
* pT and pz smearing is currently not functional. While no existing smearers rely on them, this is nevertheless a bug that will be fixed in the next update. More examples and QA are to follow as well.

##### ESCalate framework
A lightweight modular fast and full simulation framework for EIC. 
[https://gitlab.com/eic/escalate](https://gitlab.com/eic/escalate)

Previously separate packages, G4E and eJana, are now distributed as the ESCalate framework. ESCalate brings together [Monte Carlo event generators](https://gitlab.com/eic/mceg), [eic-smear](https://gitlab.com/eic/eic-smear) for fast simulations, [G4E](https://gitlab.com/eic/escalate/g4e) for full detector simulations, as well as [JANA2](https://github.com/JeffersonLab/JANA2) and [eJana](https://gitlab.com/eic/escalate/ejana) for reconstruction. 

The structure of the ESCalate framework is shown below. Part of ESCalate are [ejpm](https://gitlab.com/eic/escalate/ejpm) for distributing the software and a variety of smaller tools. In addition to [tutorials](https://www.youtube.com/channel/UCXc9WfDKdlLXoZMGrotkf7w), examples for [Geant4 detectors](https://gitlab.com/eic/escalate/g4e/-/tree/master/examples), [eJANA plugins for reconstruction and physics analyses](https://gitlab.com/eic/escalate/plugins), and [analyses in JupyterLab](https://gitlab.com/eic/escalate/workspace) are provided. 

ESCalate provides modularity in two ways: 
1. Subpackage modularity: Each package inside the framework can be used solely and separately from the rest of the framework. 
2. Subprocess modularity: JANA2 (and eJana) modularize code in small libraries called plugins allowing to run tasks in a seamless multithreaded way. 

The framework itself ensures that data between packages is consistent and output of one package can be correctly read from another. ESCalate provides Python orchestration to facilitate the configuration of each package and allow for a workflow between the packages. 

<img src="{{ '/assets/images/diagrams/escalate/ESCalate-Structure.png' | relative_url }}" width="597"/>

<br />

#### Fun4All
Fun4All is a well established simulation/reconstruction framework initially developed to reconstruct and analyze data from the PHENIX experiment. In recent years it has provided the simulations to shepherd the sPHENIX experiment from the first drawing on a napkin all the way through CD1. For the EIC it was used to develop a concept for an [EIC detector based on the Babar magnet](https://arxiv.org/pdf/1402.1209.pdf) and [an EIC detector Built around the sPHENIX Solenoid](https://indico.bnl.gov/event/5283/attachments/20546/27556/eic-sphenix-dds-final-2018-10-30.pdf). It can be used interactively (run a few events, have a look, run a few more, look again) as well as running massive productions on large farms (and as of recent also on CORI and on the OSG). For more details (and program flow charts) have a look at the [presentation](https://indico.in2p3.fr/event/18281/contributions/71607/) at the 2019 EIC User Group Meeting.

##### New developments
All fieldmaps (Babar, Beast and JLeic) are now available. They can be chosen on the ROOT macro level for details have a look at this [tutorial](https://github.com/eic/fun4all_eic_tutorials/tree/master/MagneticField).

<img src="{{ '/assets/images/diagrams/fun4all/fun4all_fieldmaps.png' | relative_url }}" width="800"/>

The magnetic field was verified using charged geantinos (shown here are 0.5, 1, 2, 3 GeV/c) compared to constant solenoidal fields as shown on the right for the Beast magnet.

Importing detectors via gdml files has its quirks but is now well understood and fully supported. It is not possible to do this generically since one has to address the volumes by name but this only needs minor modifications to existing code and is largely cut and paste.

<img src="{{ '/assets/images/diagrams/fun4all/fun4all_gdml.png' | relative_url }}" width="800"/>

Here are the latest additions to our selection of implemented detectors (all of which can be combined in a ROOT macro). We have a detailed model of the [Beast magnet](https://github.com/eic/fun4all_eicdetectors/tree/master/source) (already used in the fieldmap plots) as well as the [*All Silicon Tracker*](https://github.com/eic/g4lblvtx) and the EIC beam pipe.

The ability to combine these (and other detectors) at will is shown here:

<img src="{{ '/assets/images/diagrams/fun4all/fun4all_allsilicon.png' | relative_url }}" width="800"/>

where the *All Silicon Tracker* is put inside the Beast magnet and is being used as central tracker inside the EIC detector based on the Babar magnet.


##### Verification
Fun4All is also being used to reconstruct test beam data which allows a direct comparison of simulations with data. sPHENIX has performed extensive test beam campaigns for its detectors at energies which are relevant for EIC detectors. The calorimeter test beam results have been [published](https://ieeexplore.ieee.org/document/8519782) recently, the analysis of TPC and Maps detector data is ongoing. A good agreement with previous EICRoot based simulations has been found for the All Silicon Tracker ([slide 8](https://indico.bnl.gov/event/7894/contributions/37609/attachments/28098/43125/200514_AllSi_in_Fun4All_2.pdf))

##### Help
Help is available via [our support channel in Mattermost](https://chat.sdcc.bnl.gov/eic/channels/fun4all-software-support), non Scientific Data Center Accounts need an invite - contact us
