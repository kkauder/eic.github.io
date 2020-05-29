---
title: PEPSI
name: pepsi
category: pepsi
layout: default
level: 0
---
{% include layouts/title.md %}

**Note: By now it is better to use DJANGOH for polarised studies as it is the more complete generator**

  * TOC
  {:toc}

PEPSI (Polarised Electron Proton Scattering Interactions) is a Monte Carlo generator for polarised deep inelastic scattering (pDIS). It is based on the LEPTO 6.5 Monte Carlo for unpolarised DIS.
See L. Mankiewicz, A. Schäfer and M. Veltri, Comp. Phys. Comm. 71, 305-318 (1992),
[PEPSI.paper.pdf](https://wiki.bnl.gov/eic/upload/PEPSI.paper.pdf).

#### Parton distribution functions

The distribution function to use in polarised leptoproduction is set via the variable <tt>LST(15)</tt> in the LEPTO <tt>COMMON</tt> block <tt>/LEPTOU/</tt>.
[Tables 1 and 2](https://wiki.bnl.gov/eic/index.php/PEPSI-pdf) list internal allowed values of <tt>LST(15)</tt> for polarised and unpolarised distributions respectively.

Pepsi is linked with the pdflib such that all PDFs included in there can be used by setting <tt>LST(15)</tt> to the respective PDF-ID

##### PEPSI processes important in ep

| Subprocess | \# | Description |
|:---:|:---:|:---:|
| DIRECT |||
| γ<sup>*</sup>q → q | 1 | LO DIS |
| γ<sup>*</sup>q → qg | 2| QCDC |
| γ<sup>*</sup>g → q qbar | 3| PGF |
{:.table-bordered}
{:.table-striped}

<br />
*QCDC*: QCD-Compton, radiation of a gluon from incoming or outgoing quark lines
<br />
*PGF*: Photon Gluon Fusion

#### Running PEPSI
In the standard setup in the singularity cvmfs envirtonment or at BNL, the code can be found in
```
$EICDIRECTORY/PACKAGES/pepsi
```

The executables are in the same directory and called `pepsieRHICnoRAD` and `pepsieRHICwithRAD`, respectively. There are several steer files (named `input.data.XXXXX.eic`) provided in this directory to run PEPSI and get reasonable output.

PEPSI has to be run twice if polarized asymmetries should be generated, once for parallel, lepton and proton beam spin direction, and once antiparallel.
Charge Current events can only be generated in the unpolarized mode.
The <tt>LST(8)</tt> can only be different from 0 or 1 in the unpolarized mode.

Note that the executables expect the `pdf/` directory in the directory of execution. Easiest way to achieve this is a softlink (adapt to your location)
```
ln -s $EICDIRECTORY/PACKAGES/PEPSI/pdf
```

##### Without radiative corrections
Choose or create a steering file. Some that are provided in `$EICDIRECTORY/PACKAGES/pepsi/STEER-FILES`:
* `input.data_noradcor.eic.pol.anti` is an example to run PEPSI with settings tuned for Hermes, and/or H1 and ZEUS for the antiparallel polarized cross-section
* `input.data_noradcor.eic.pol.par`: for the parallel polarized cross-section
* `input.data_noradcor.eic.unpol`: for the unpolarised cross-section

You can then run:
```
./pepsieRHICnoRAD < STEER-FILES/input.EW_noradcor.eic.posi.test > XXX.log
```
where the output redirect to `XXX.log` is optional.

##### With radiative corrections

**Note: DO NOT USE radiative corrections. Currently this is no longer supported. See [Known Issues](#known-issues)**

#### Output file structure

The output file is in a text format which has the following structure:
* 1st line: <tt> PEPSI EVENT FILE</tt>
* 2nd line: <tt>============================================</tt>
* 3rd line: Information on event wise variables stored in the file:

| I:                                                                                 | 0 (line index)                                                                                               |
| ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| ievent:                                                                            | eventnumber running from 1 to XXX                                                                            |
| genevent:                                                                          | trials to generate this event                                                                                |
| process:                                                                           | pepsi subprocess (LST(23)), for details see table above                                                      |
| subprocess:                                                                        | pythia subprocess (LST(24)), for details see table above                                                     |
| nucleon:                                                                           | hadron beam type (LST(22))                                                                                   |
| struckparton:                                                                      | parton hit in the target (LST(25))                                                                           |
| partontrack:                                                                       | \# or parton track (LST(26))                                                                                 |
| truey, trueQ2, truex, trueW2, trueNu:                                              | are the kinematic variables of the event.                                                                    |
|                                                                                    | If radiative corrections are turned **on** they are **different** from what is calculated from the scattered lepton. |
|                                                                                    | If radiative corrections are turned **off** they are **the same** as what is calculated from the scattered lepton    |
| mcfixedweight                                                                      | weight calculated from generation limits                                                                     |
| weight                                                                             | total weight including everything                                                                            |
| dxsec                                                                              | cross section included in the weight                                                                         |
| mcextraweight                                                                      | Pepsi total cross section in pb from numerical integration parl(23)                                          |
| dilut, F1, F2, A1, A2, R, Depol, d, eta, eps, chi                                  | true variables needed to calculate g1                                                                        |
| gendilut, genF1, genF2, genA1, genA2, genR, genDepol, gend, geneta, geneps, genchi | variables needed to calculate g1                                                                             |
| SigRadCor:                                                                         | information used and needed in the radiative correction code                                                 |
| EBrems:                                                                            | energy of the radiative photon in the nuclear rest frame                                                     |
| nrTracks:                                                                          | number of tracks in this event, includes also virtual particles<br><br>                                      |
{:.table-bordered}
{:.table-striped}

* 4th line: <tt>============================================</tt>
* 5th line: Information on track-wise variables stored in the file:

| I:      | line index, runs from 1 to nrTracks                                                                      |
| ------- | -------------------------------------------------------------------------------------------------------- |
| K(I,1): | status code KS (1: stable particles 11: particles which decay 55; radiative photon)                      |
| K(I,2): | particle KF code (211: pion, 2112:n, ....)                                                               |
| K(I,3): | line number of parent particle                                                                           |
| K(I,4): | normally the line number of the first daughter; it is 0 for an undecayed particle or unfragmented parton |
| K(I,5): | normally the line number of the last daughter; it is 0 for an undecayed particle or unfragmented parton. |
| P(I,1): | px of particle                                                                                           |
| P(I,2): | py of particle                                                                                           |
| P(I,3): | pz of particle                                                                                           |
| P(I,4): | Energy of particle                                                                                       |
| P(I,5): | mass of particle                                                                                         |
| V(I,1): | x vertex information                                                                                     |
| V(I,2): | y vertex information                                                                                     |
| V(I,3): | z vertex information<br><br>                                                                             |
{:.table-bordered}
{:.table-striped}

* 6th line: <tt>============================================</tt>
* 7th line: event information for first event
* 8th line: <tt>============================================</tt>
* 9th to X-1 line: track-wise info of 1st event
* Xth line <tt>============================================</tt>

**For each subsequent event, lines 7 through X repeat analogously.**

#### Installation

Can be built using "make".
The "install" target should be customized to your environment before using

Ignore warnings of the form:
```
 Warning: $ should be the last specifier in format
```
 Which should be okay (it is a g77 extension allowed by gfortran).
 As well as:
```
Warning: Deleted feature: PAUSE statement at (1)
```
This feature is deleted in F95; here, it should eventually be replaced by write() + read().

#### Changes
Multiple warnings like this:
```pepsi/setctq5.F:9.10:
     >   './pdf/cteq5hj.tbl',                                           
          1
Warning: Initialization string starting at (1) was truncated to fit the variable (16/17)
```

indicate a too short variable length. Changed to
```fortran
      Character Flnm(Isetmax)*100
```
in line 6 (of setctq5.F).

#### Known Issues
**Note: DO NOT USE radiative corrections. Currently does not work.**

If radiative corrections are restored, this would be the procedure to use them:

* Create a directory called `radgen` in the area you want to run the code.
* You either need to generate the lookup table for your cuts and beam energy settings first
```
   pepsieRHICwithRAD < input.data_make-radcor.eic.unpol
```
or you can use one of the files already generated in the directory
`$EICDIRECTORY/PACKAGES/pepsi/radgen`
and called `xytab1unp.04.050.dat` or `xytab1ant.04.050.dat` or `xytab1par.04.050.dat`.
* To run the code than with radiative corrections simply change the steer file to either `input.data_radcor.eic.unpol` or `input.data_radcor.eic.pol.par` or ... and run
```
   pepsieRHICwithRAD < input.data_radcor.eic.unpol > XXX.log
```

However, as noted above, they cannot currently be used.
```
./pepsieRHICwithRAD < STEER-FILES/input.data_radcor.eic.pol.anti

At line 514 of file pepsiMaineRHIC_radcorr.v2.F (unit = 29, file =
'pepsi.ep.4x100.1Mevents.pol-anti.RadCor=1.txt')
Fortran runtime error: Expected REAL for item 42 in formatted
transfer, got INTEGER
```
