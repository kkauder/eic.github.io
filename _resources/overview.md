---
title: Resources available at BNL and JLab
description: Resources available at BNL and JLab
name: overview
layout: default
---

{% include layouts/title.md %}

BNL and JLab provide computing resources for the worldwide EIC community:

* [**CPUs**](#cpus)
* [**Computing Environment**](#ce)
* [**Storage**](#storage)
  * [User Home](#userhomes)
  * [Data](#data)
  * [Other Storage Services](#otherstorage)
* [**GitHub organization**](#github)

You can use your existing BNL or JLab account or register as new user at the host labs: 

* [Request a BNL computing account](https://docs.google.com/document/d/1Y2JleLOx1NiPoPI69yW97Onl_Dly4WzfInRGjskM274/edit?usp=sharing)
* [Request a JLab computing account](https://misportal.jlab.org/jlabAccess/) (register as `User-remote` and state `EIC` as your sponsor)

 --- 

#### CPUs {#cpus}

| **BNL**                                                                                                                                                    | **JLab**                                                                      |
| Dedicated EIC resources: 7 machines with 64 core, 6 * 64 batch slots = 384 slots and one for interactive use (VMs). Each node have dual CPU AMD EPYC 7351. | JLab operates a common cluster. 25k job slots. Delivering ~ 76M core hours per year normalized to dual CPU AMD EPYC 7351.                                    |
| 1,000 slots allocated from a variety of CPUs (Intel(R) Xeon(R) and AMD EPYC)                                                                               | EIC is currently one of ten projects sharing a 10% fair-share of the cluster. So guaranteed 7.6M core hours if the other nine are idle 0.8M if all are busy. |
| 31k slots available to all experiments that can be dynamically allocated upon priorities (358 M core hours per year).                                      | A further 4MCH/yr dedicated to EIC will be added when demand requires it.                                                                                    |
{:.table-bordered}
{:.table-striped}
<br>

 --- 

#### Computing Environment {#ce}

| **BNL**                                              | **JLab**                                                                      |
| OSG Submit host osgsub01.sdcc.bnl.gov                | OSG submit host                                                               | 
| OSG/EIC jobs landing at BNL are purely opportunistic.| OSG infrastructure to land EIC jobs on the JLab cluster. Counts against quota.|
{:.table-bordered}
{:.table-striped}
<br>

 --- 

#### Storage {#storage}

##### User HOME {#userhomes}

| **BNL**                                              | **JLab**                                                                      |
| OSG Submit host osgsub01.sdcc.bnl.gov                | OSG submit host                                                               | 
| OSG/EIC jobs landing at BNL are purely opportunistic.| OSG infrastructure to land EIC jobs on the JLab cluster. Counts against quota.|
{:.table-bordered}
{:.table-striped}
<br>

##### Data {#data}

| **BNL**                                                           | **JLab**                                                                                                                                                                                                            |
| **/eic/data** 6 TB NFS mounted (GPFS general user use), 72% full  | EIC is allocated 5TB of volatile and 5TB of cache neither of which are close to the limit. The total pool at JLab is 5 PB. Volatile and Cache are auto managed with a deletion policy so allocation can be changed. |
| **/gpfs02/eic/DATA** 400 TB NFS mounted (GPFS data use), 53% full |                                                                                                                                                                                                                     |
| Xrootd/StashCache under preparation.                              | Xrootd/StashCache available.                                                                                                                                                                                        |
| 1 PBytes pool (S3 or Xrootd)                                      |                                                                                                                                                                                                                     |
{:.table-bordered}
{:.table-striped}
<br>

##### Other Storage Services {#otherstorage}

| **BNL**                                                                                      | **JLab**                              |
| CernVM-FS Stratum 0 repository server                                                        | CernVM-FS Stratum 1 repository server |
| Globus for data transfer.                                                                    | Globus for data transfer.             |
| BNLBox data export possible ([documentation](https://eic.github.io/resources/storage.html)). |                                       |
{:.table-bordered}
{:.table-striped}
<br>

 --- 

##### GitHub organization {#github}

The [EIC GitHub organization](https://eic.github.io/github/) is available for the whole EIC community.

 --- 