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
environment being set up by the working group allows the EICUG to
pursue the Yellow Report studies in a manner that is accessible,
consistent, and reproducible.

## Table of contents

* [General Update](#swg)
    * [Communication](#communication)
    * [GitHub for the EICUG](#github)
    * [Support us to support you better](#support)
    * [Tutorials](#tutorials)
    * [Workshop on “Machine Learning for Particle Physics Experiments"](#workshop)
* [Software Update](#update)
    * [eic-smear](#eic-smear)
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

### GitHub for the EICUG {#github}

[https://github.com/eic](https://github.com/eic) is available for the
whole EICUG. For membership, please send your GitHub username to
[eicug-computing-infrastructure-support@eicug.org](mailto:eicug-computing-infrastructure-support@eicug.org?subject=GitHub%20Account). We
encourage you to share your software and documentation on
[https://github.com/eic](https://github.com/eic). Please follow [our
guidelines]() in doing so.

### Support us to support you better {#support}
The common simulation tools and workflow environment can only grow
with user input. The EICUG Software Working Group asks interested
users to join our support team to ensure fast response to user
requests. This is an ideal opportunity to learn more about the
software and its development.

### Tutorials {#tutorials}
The tutorials for fast and detector full simulations are available on the [EICUG YouTube channel](https://www.youtube.com/channel/UCXc9WfDKdlLXoZMGrotkf7w). The next tutorials will be on Monte Carlo Event Generators. 

<img src="{{ '/assets/images/tutorials/SWG-Tutorials.pdf' | relative_url }}" width="500"/>

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
In the June Software News, updates on eic_smear, EicToyModel, and Fun4All are included. 

### eic-smear {#eic-smear}

Kolja will add text. 


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

Chris will add text. 
 
---