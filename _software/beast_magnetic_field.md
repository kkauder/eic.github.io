---
title: BeAST Magnetic Field
name: beast_magnetic_field
layout: default
level: 0
div: yes
weight: 99
---
# BeAST solenoid magnetic field map 

##### The repository contains an ASCII file with the field map, a C++ class to handle it and a GDML model

{% include layouts/software-link.md category='beast' %}

<div class="row">
  <div class="col-sm-12 blog-main">
    <hr>
    <left>
      <div class=row>
        <div class="col-sm-6">
	  <img src="/assets/images/site/beast-opera-map.png" width="400"/>
        </div>
        <div class="col-sm-6">
    	<center> 
          <p class="lead">
	      Open solenoid design (no field clamps) 
	  </p>
          <p class="lead">
	      Homogeneous (less than than 4% variation) 3T central field in the TPC volume 
	  </p>
          <p class="lead">
	      Fringe field is tuned in order and minimize charge particle bending in the forward
	      gaseous RICH volume (less than 1mrad RMS for 10 GeV/c particles up to 25 degree
	      polar angles)
	  </p>   
          <p class="lead">
	      Field map originally produced by a collection of Open Source tools (Elmer, Netgen,
	      ROOT)
	  </p> 
    	</center>   
	</div>
      </div>
    </left>
  </div>
</div>
