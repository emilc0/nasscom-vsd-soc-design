# Floorplanning:

# D2_SK1_L6 ... D2_SK1_L8

**During the floorplanning we will:**

**-set die area**

**-set core area**

**-set aspect ratio**

**-set utilization factor**

**-pace I/O cells**

**-macro placement**

**-power distribution**



## Read about floorplan switches here:

gedit $WD/configuration/README.md &



## The floorplan switches are read (in this order) from:

gedit $WD/configuration/floorplan.tcl &

gedit $D/config.tcl &

gedit $D/sky130A_sky130_fd_sc_hd_config.tcl &

**The actual switches used by the flow are put in:**

gedit $D/$R/config.tcl &

**make the settings match the video D2_SK1_L7 at 03:08:**

![image](https://github.com/user-attachments/assets/e410a4eb-ab79-4a23-8cf5-0032ecbed258)

**modify config.tcl in the design directory:**

![image](https://github.com/user-attachments/assets/1f23c04d-e975-4cca-b223-5e96c49ab8c7)

**as an example, let's see the requested metal for pads:**

![image](https://github.com/user-attachments/assets/25a673e6-1f87-477d-a4bd-c48492506881)


## Run floorplanner:

cd $WD

docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a -tag 16-12_12-43


puts "$::env(FP_CORE_UTIL) =50?"

puts "$::env(FP_ASPECT_RATIO) =0.75?"

puts "$::env(FP_CORE_MARGIN) =0?"

puts "$::env(FP_IO_HMETAL) =3?"

puts "$::env(FP_IO_VMETAL) =4?"

puts "$::env(FP_TAPCELL_DIST) =14?"

puts "$::env(FP_IO_MODE) =1?"


set ::env(LIB_SYNTH_COMPLETE) 1

run_floorplan

![image](https://github.com/user-attachments/assets/8109629b-5971-4e23-9cda-ba18494c3cc9)

![image](https://github.com/user-attachments/assets/4d0cb450-fbc4-410f-849e-f73c68f1aea6)


## check ioplacerlog:

gedit $D/$R/logs/floorplan/4-ioPlacer.log

## check result:

gedit $D/$R/results/floorplan/picorv32a.floorplan.def &

![image](https://github.com/user-attachments/assets/997b5c05-a245-4e62-bb6d-2e7d1701ecf3)

**check the metal layers used for pads: met3 and met4 (no met5)**

![image](https://github.com/user-attachments/assets/d68f0a9c-5e53-4677-8513-bf600b1d4c97)

![image](https://github.com/user-attachments/assets/d1ff2ad6-c752-4f8f-be44-bcbdae9fccec)


## read the floorplan .def file with Magic:

magic -T $T lef read $D/$R/tmp/merged.lef def read $D/$R/results/floorplan/picorv32a.floorplan.def &

![image](https://github.com/user-attachments/assets/0d4afac0-ba8c-439d-beed-aa020f9d543a)


![image](https://github.com/user-attachments/assets/37b7940b-0aef-42b6-8a9c-c703da381ed3)



***Now The pins are equidistant, horizontal pins in metal2, vertical pins in metal3***


# Die area

![image](https://github.com/user-attachments/assets/a04af4e3-3e6d-4d33-afad-13843ddf2dd5)

**(641560/1000) x (494650/1000) = 317,347um2**


## debugging place error

![image](https://github.com/user-attachments/assets/fca8b0a7-b080-447a-9607-d4e0da1415a6)

**in $D/$R/config.tcl:
set ::env(FP_SIZING) "relative"
DIE_AREA not defined**

https://openlane.readthedocs.io/en/2023.09.07/reference/configuration.html

**FP_SIZING: Whether to use relative sizing by making use of FP_CORE_UTIL or absolute one using DIE_AREA.
(Default: "relative" - accepts "absolute" as well)**

**DIE_AREA: Specific die area to be used in floorplanning when FP_SIZING is set to absolute. Specified as a 4-corner rectangle “x0 y0 x1 y1”. Units in μm
(Default: unset)**

after synthesis: 0.149mm2
DIEAREA ( 0 0 ) ( 641560 494650 )    0.317mm2   util 50%
DIEAREA ( 0 0 ) ( 564045 436515 )    0.245mm2   util 65%


