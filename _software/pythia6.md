---
title: PYTHIA6
name: pythia6
category: pythia
layout: default
level: 0
---

{% include layouts/title.md %}

# PYTHIA-RAD-CORR - pythia6 with radiative corrections

## About

Currently hosted at
https://gitlab.com/eic/mceg/PYTHIA-RAD-CORR

Documentation in the BNL Wiki
* https://wiki.bnl.gov/eic/index.php/PYTHIA
Note that repository and other technical information in the wiki are superseded by
this document.

Contacts
* Kolja Kauder <kkauder@bnl.gov>
* Elke Aschenauer <elke@bnl.gov>

Based on PYTHIA 6.4.28 with radiative corrections and putput mdifications.

## Prerequisites
- gfortran
- LHAPDF5
- ROOT
- cmake
- CERNLIB

# Basic installation (on RCF, adapt as appropriate):

```shell
cd ${EICDIRECTORY}/PACKAGES
git clone https://gitlab.com/eic/mceg/PYTHIA-RAD-CORR.git
cd ${EICDIRECTORY}/PACKAGES/PYTHIA-RAD-CORR
mkdir build; cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=${EICDIRECTORY}
make -j 8 install
```
This will produce warnings of the form
```
Warning: $ should be the last specifier in format at (1)
```
which should be okay (it is a g77 extension allowed by gfortran).

# Example Run
To run, the pythiaeRHIC executable reads options from standard input
and is controlled via steering cards and input redirection, with
optional output redirection to a log file. The name of the output file
is specified in the steering card.
```
pythiaeRHIC < STEER_FILE > out.log
```

A practical example, assuming $EICDIRECTORY was set and the package
installed as above, is:
```shell
$EICDIRECTORY/bin/pythiaeRHIC < $EICDIRECTORY/PACKAGES/PYTHIA-RAD-CORR/STEER-FILES-Other/ep_noradcor.20x250.quicktest 
```

# Steering files
A variety of steering files can be found in the STEER-*
directories. Which ones appropriately reflect the physics you wish to
implement is beyond the scope of this document. Please contact the EIC
UG for advice.


#### Drivers
- pyMaineRHIC_v2.f
- pythiaMain.cpp uses mainly class interface functions for setup
- UsingCardPythiaMain.cpp can be used in place of the fortran driver


## CHANGES wrt build_pythia6.sh script :

### LHAPDF-related:
- pdfset.f structm.f structp.f are removed (renamed)
- sugra.f is emptied out

### Fix for older pythia versions:
- pyalps.f doesn't need to be changed in 6.4.28
   (build script only affects commented out old code)

### Random number generation change:	
Replace default routine by call to ranlux

- pyr.f
Added ranlux.f v 1.2 (Deleted an include line) to avoid issues linking
against cernlib

### PHYSICS:
- pydiff.f
- pydisg.f
- pygaga.f
- pyrand.f
- pyremn.f
- pysgqc.f
- pysigh.f
- pyxtot.f

### KK Note: On 2/26/2020, I pulled in 
pydata.f
pydisg.f
pyremn.f
pyptdirc.f 
from the original package (they seem to have been overlooked initially)


### Added in top directory:
#### Physics:
- radgen.f
- radgen_event.f
- radgen_init.f
- gmc_random.f
- pyth_xsec.f
- pythia_radgen_extras.f

#  Hard-coding against lhapdf5
Executables require LHAPDF5 installed and links executables against it.





