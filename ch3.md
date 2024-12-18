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


## Run floorplanner:

run_floorplan

![image](https://github.com/user-attachments/assets/8109629b-5971-4e23-9cda-ba18494c3cc9)

![image](https://github.com/user-attachments/assets/4d0cb450-fbc4-410f-849e-f73c68f1aea6)


## check ioplacerlog:

gedit $D/$R/logs/floorplan/4-ioPlacer.log

## check result:

gedit $D/$R/results/floorplan/picorv32a.floorplan.def &

![image](https://github.com/user-attachments/assets/997b5c05-a245-4e62-bb6d-2e7d1701ecf3)

## read the floorplan .def file with Magic:

magic -T $T lef read $D/$R/tmp/merged.lef def read $D/$R/results/floorplan/picorv32a.floorplan.def &

![image](https://github.com/user-attachments/assets/0d4afac0-ba8c-439d-beed-aa020f9d543a)

***The pins are not equidistant, horizontal pins in metal3, vertical pins in metal2. Checking why.***

![image](https://github.com/user-attachments/assets/37b7940b-0aef-42b6-8a9c-c703da381ed3)

**make the settings match the video D2_SK1_L7 at 03:08:**

![image](https://github.com/user-attachments/assets/e410a4eb-ab79-4a23-8cf5-0032ecbed258)

**modify config.tcl in the design directory:**

![image](https://github.com/user-attachments/assets/1f23c04d-e975-4cca-b223-5e96c49ab8c7)

**and redo the floorplan**

prep -design picorv32a -tag 16-12_12-43

puts "$::env(FP_CORE_UTIL) =50?"

puts "$::env(FP_ASPECT_RATIO) =0.75?"

puts "$::env(FP_CORE_MARGIN) =0?"

puts "$::env(FP_IO_HMETAL) =3?"

puts "$::env(FP_IO_VMETAL) =4?"

puts "$::env(FP_TAPCELL_DIST) =14?"

puts "$::env(FP_IO_MODE) =1?"

run_floorplan

***Now The pins -are- equidistant, horizontal pins in metal2, vertical pins in metal3. Checking why.***

