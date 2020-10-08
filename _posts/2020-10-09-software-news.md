---
title: Software News August and September
author: Markus Diefenthaler
layout: default
symbol: glyphicon-calendar
until: 2019-12-31
---
<p/>

{% include images/image.md name='news_banner' width='800' %}

The Software Working Group is working on physics and detector
simulations that enable a quantitative assessment of the measurement
capabilities of the EIC detector(s) and their physics impact for the
Yellow Report Initiative. The common simulation tools and workflow
environment being set up by the working group allow the EICUG to
pursue the Yellow Report studies in a manner that is accessible,
consistent, and reproducible.

## Table of contents

* [General Update](#swg)
    * [Topic](#topic)
* [Software Update](#update)
    * [Fun4All](#fun4all)
    * [Tool](#tool)

---

## General Update {#swg}

### Topic {#topic}

---

## Software Update {#update}

### Tool {#tool}

### Fun4All {#fun4all}
##### TPC Endcap included
For our TPC based simulations we now have a detailed endcap based on the sPHENIX design. This will enable studies how the TPC support material will affect especially the electron identification in the forward hemisphere. The endcap is configurable so it can serve as a basis to develop detailed TPC endcap designs for an eic detector. The endcap is by default disabled in the EIC detector based on the Babar magnet but can be enabled in the [macro](https://github.com/eic/fun4all_macros/blob/master/detectors/EICDetector/Fun4All_G4_EICDetector.C) (set Enable::TPC_ENDCAP = true in line 215).

<img src="{{ '/assets/images/software/fun4all/2020-sept/tpc_endcap_cad.png' | relative_url }}" width="200"/>
*cad drawing*

<img src="{{ '/assets/images/software/fun4all/2020-sept/tpc_endcap_sim.png' | relative_url }}" width="200"/>
*Fun4All Implementation*

more details about the implementation of the TPC endcaps can be found under the [original pull request](https://github.com/sPHENIX-Collaboration/coresoftware/pull/915)

---

#### Recap: How to run Fun4All
As a prerequisite you need to be able to run a singularity container on you local host. We have instructions to install a Ubuntu VM for [windows](https://github.com/eic/Singularity/blob/master/VirtualBox.md) and [macOS](https://github.com/eic/Singularity/blob/master/OSX_installationguide.md)
##### Using a local download of the libraries:
We  provide a [script](https://github.com/eic/Singularity/blob/master/updatebuild.sh) which downloads and installs the needed libraries on your local host. This will give you a working envrionment where you can run simulations but also compile every package and develop new ones.
```
git clone https://github.com/eic/Singularity
cd Singularity
./updatebuild.sh
```
If you have an existing installation, running the updatebuild.sh will update your local installation with the most recent changes. Then issue the two commands which are printed out at the end.

##### Using cmvfs
If you have cvmfs on your host (and an internet connection) - using cvmfs is the prefered way of running. It will give you access to multiple software builds and you do not have to keep it updated yourself. We do provide weekly archival builds if you want to use something stable. In this case you only have to start the singularity container which resides in cvmfs and source the setup script inside it.
```
singularity shell -B /cvmfs:/cvmfs /cvmfs/eic.opensciencegrid.org/singularity/rhic_sl7_ext.simg
source /cvmfs/eic.opensciencegrid.org/x8664_sl7/opt/fun4all/core/bin/eic_setup.sh -n
```
---
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
