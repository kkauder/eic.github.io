---
title: Software News July
author: Markus Diefenthaler
layout: default
symbol: glyphicon-calendar
until: 2020-12-31
---
<p/>

<img src="{{ '/assets/images/site/EICUG-SWG-News-Banner.png' | relative_url }}" width="900"/>

The Software Working Group is working on physics and detector
simulations that enable a quantitative assessment of the measurement
capabilities of the EIC detector(s) and their physics impact for the
Yellow Report Initiative. The common simulation tools and workflow
environment being set up by the working group allow the EICUG to
pursue the Yellow Report studies in a manner that is accessible,
consistent, and reproducible.

## Table of contents

* [General Update](#swg)
    * [Communication](#communication)
    * [Expression of Interest for Software](#eoi)
    * [GitHub for the EICUG](#github)
    * [Support us to support you better](#support)
    * [Tutorials](#tutorials)
    * [Workshop on “Machine Learning for Particle Physics Experiments"](#workshop)
* [Software Update](#update)
    * [EicToyModel](#eictoymodel)
    * [Fun4All](#fun4all)

---

## General Update {#swg}

### Communication {#communication}

The Software Working Group will start to announce software updates,
known bugs, and other software related news on the
[eicug-software@eicug.org](mailto:eicug-software@eicug.org) mailing
list. While summaries will be provided in our
Software News, we encourage all working groups to subscribe to
[eicug-software@eicug.org](mailto:eicug-software@eicug.org).

### Expression of Interest for Software {#eoi}

The Software Working Group is coordinating an [Expression of
Interest](https://www.bnl.gov/eic/EOI.php) for Software. As a next
step, we invite the community to the next Project Greenfield meeting
on DATE. In the meeting, we will leverage everyone’s experience to
define requirements for EIC Software and work together on common
software projects based on these requirements. Project Greenfield
includes all components of EIC Software, simulation, reconstruction,
physics analyses, streaming readout, online monitoring, etc.. Examples
for common software in the community are ACTS, DD4hep, Gaudi, Geant4,
JANA2, Jupyter, or ROOT. The Expression of Interest for Software will
include emerging technologies of Artificial Intelligence and Quantum
Computing.


### GitHub for the EICUG {#github}

[https://github.com/eic](https://github.com/eic) is available for the
whole EICUG. For membership, please send your GitHub username to
o[eicug-computing-infrastructure-support@eicug.org](mailto:eicug-computing-infrastructure-support@eicug.org?subject=GitHub%20Account). We
encourage you to share your software and documentation on
[https://github.com/eic](https://github.com/eic). Please follow [our
guidelines](https://eic.github.io/computing/github.html) in doing so.

### Support us to support you better {#support}
The common simulation tools and workflow environment can only grow
with user input. The EICUG Software Working Group asks interested
users to join our support team to ensure fast response to user
requests. This is an ideal opportunity to learn more about the
software and its development.

### Tutorials {#tutorials}
The tutorials for fast and detector full simulations are available on the [EICUG YouTube channel](https://www.youtube.com/channel/UCXc9WfDKdlLXoZMGrotkf7w). The next tutorials will be on Monte Carlo Event Generators (MCEGs): 

* **August 17** Pythia 8 (Stefan Prestel (LUND)) 
* **August 18** MC-data comparisons with Rivet (Christian Bierlich (LUND))
* **August 19** Herwig 7 (Simon Plaetzer (Vienna))
* **August 20** Sherpa 2 (Stefan Hoeche (FNAL))

Details are available on the [Indico site for the MCEG tutorials](https://indico.bnl.gov/event/9153/). 

<img src="{{ '/assets/images/tutorials/SWG-Tutorials.png' | relative_url }}" width="500"/>

### Workshop on “Machine Learning for Particle Physics Experiments” {#workshop}

The first joint GlueX-PANDA-EIC workshop will take place September
21-15 2020. The online meeting on “Machine Learning for Particle
Physics Experiments” will consist of 3 to 4 lectures a day each 45
minutes long. The workshop aims both at beginners in Machine Learning
and more experienced software developers. Longer sessions for
questions and discussions at the beginning and the end of each working
day are foreseen. A tentative agenda can be found at the [Indico page
of the workshop](​https://indico.gsi.de/event/10576​). Registration is
free and encouraged. 

---

## Software Update {#update}
In the July Software News, updates on the EicToyModel and Fun4All are included. 

### EicToyModel {#eictoymodel}

The [EicToyModel software suite](https://github.com/eic/EicToyModel)
was recently added to the EIC Software collection. This compact
ROOT-based C++ library was developed for EIC Central Detector
configuration purposes, with a goal to synchronize the detector layout
description in various Yellow Report related activities, GEANT4
simulations in particular.

The tool allows users to create various EIC detector configuration
templates (namely, the self-consistent collections of 3D sub-detector
integration volumes), visualize and share the models, and ultimately
make use of them in the GEANT4 simulation environment. An extensive
[README](https://github.com/eic/EicToyModel/blob/master/README.md)
with several usage examples is provided. Interfaces to the EIC
simulation frameworks ESCalate and Fun4All still needs to be
finalized.

### Fun4All {#fun4all}

The macros were reorganized to disentangle the various large detector concepts. The macros which set up the subsystems for the [EIC detector based on the Babar magnet](https://github.com/eic/fun4all_macros/tree/master/common) and for other [EIC detector implementations](https://github.com/eic/fun4all_eicmacros/tree/master/common) were moved into separate areas. They are installed during the build and are available via the ROOT_INCLUDE_PATH (just like any other include). The advantage of this setup is that detector systems can now share these subsystems without having to copy those macros locally. Development is done locally - the local macro takes precedence over the installed macro.

Why should you care?

This makes it much easier to set up your own complete eic detector with components of your choosing (but you are responsible that they fit - better run with overlap check for the first time). We have a handful of pre-defined configurations, all using the proper scalable fieldmaps or constant solenoidal field:
  * [All Silicon Tracker inside the Babar magnet](https://github.com/eic/fun4all_eicmacros/tree/master/detectors/AllSilicon)
<img src="{{ '/assets/images/software/fun4all/2020-july/allsilicon.png' | relative_url }}" width="200"/>
  * [Beast Magnet](https://github.com/eic/fun4all_eicmacros/tree/master/detectors/Beast) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
<img src="{{ '/assets/images/software/fun4all/2020-july/beast_template.png' | relative_url }}" width="200"/>
  * [Partial JLeic](https://github.com/eic/fun4all_eicmacros/tree/master/detectors/JLeic) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
<img src="{{ '/assets/images/software/fun4all/2020-july/jleic.png' | relative_url }}" width="200"/>
  * [LANL Barrel+Forward](https://github.com/eic/fun4all_macros/tree/master/detectors/EICDetector) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
<img src="{{ '/assets/images/software/fun4all/2020-july/lanl.png' | relative_url }}" width="200"/>
  * [EIC detector based on the Babar magnet](https://github.com/eic/fun4all_macros/tree/master/detectors/EICDetector) &nbsp;&nbsp; 
<img src="{{ '/assets/images/software/fun4all/2020-july/eicdetector.png' | relative_url }}" width="200"/>

  * [sPHENIX](https://github.com/eic/fun4all_macros/tree/master/detectors/sPHENIX) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
<img src="{{ '/assets/images/software/fun4all/2020-july/sphenix.png' | relative_url }}" width="200"/>
  * [fsPHENIX](https://github.com/eic/fun4all_macros/tree/master/detectors/fsPHENIX) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;
<img src="{{ '/assets/images/software/fun4all/2020-july/fsphenix.png' | relative_url }}" width="200"/>

You will find a Fun4All_G4_XXX.C and G4Setup_XXX.C macro in those directories. The G4Setup_XXX.C macro set up the magnet and the selection of subsystems which can be used. The Fun4All_G4_XXX.C selects the options what you want to run.

All Fun4All_G4_XXX.C macros can run all our event generators (single particles - gun and distributions, pythia6, pythia8, generators from eic-smear, sartre, hijing, upsilons). The Beast implementation is currently the magnet with the eic beampipe only - lets see if we can fill the empty space. Fast truth based tracking based on genfit is enabled for all eic detectors. sPHENIX and fsPHENIX have actual tracking for the barrel which is under development, if someone is interested to work on eic tracking we have some ideas and some code to start with (caveat: this is an expert operation where some experience is needed). The raw output can be written to root TTrees for inspection.

The macros run out of the box (after sourcing the [/cvmfs/eic.opensciencegrid.org/x8664_sl7/opt/fun4all/core/bin/eic_setup.csh](https://github.com/eic/fun4all_opt_scripts/blob/master/bin/sphenix_setup.csh) script using a single particle generator).

##### Create Your Own Detector Concepts
If you want to create your own you can start with our newest addition to our [tutorial](https://github.com/eic/fun4all_eic_tutorials/tree/master/detectors). They contain the Fun4All_G4 and G4Setup templates for the available magnets (which differ in size and strength):
 
  * [Babar](https://github.com/eic/fun4all_eic_tutorials/tree/master/detectors/Babar)
<img src="{{ '/assets/images/software/fun4all/2020-july/babar_template.png' | relative_url }}" width="200"/>

  * [Beast](https://github.com/eic/fun4all_eic_tutorials/tree/master/detectors/Beast)
<img src="{{ '/assets/images/software/fun4all/2020-july/beast_template.png' | relative_url }}" width="200"/>

  * [Cleo](https://github.com/eic/fun4all_eic_tutorials/tree/master/detectors/Cleo)
<img src="{{ '/assets/images/software/fun4all/2020-july/cleo_template.png' | relative_url }}" width="200"/>

By default the respective fieldmaps are used but you can switch to a constant solenoidal field and the eic beam pipe is included. Once you decided on the volume names of your tracking detectors you can run our [fast genfit based track fitting](https://github.com/eic/fun4all_coresoftware/tree/master/simulation/g4simulation/g4trackfastsim). It supports cylinders and planes (barrel detectors and forward/backward disks).

##### Help with Fun4All
Help is available via [our support channel in Mattermost](https://chat.sdcc.bnl.gov/eic/channels/fun4all-software-support), non BNL Accounts need an invite - contact us.  

---
### About the Software Working Group

Please see our [website](https://eic.github.io) for more information
about the Software Working Group and engage in the discussion on our
[mailing list](mailto:eicug-software@eicug.org). For software
questions, please see our
[tutorials](https://www.youtube.com/channel/UCXc9WfDKdlLXoZMGrotkf7w),
contact us via
[software-support@eicug.org](mailto:software-support@eicug.org), or
join our [Slack channel](https://eicug.slack.com) (see QR code below).

<img src="{{ '/assets/images/support/EICUG-Slack.png' | relative_url }}" width="200"/>

---
