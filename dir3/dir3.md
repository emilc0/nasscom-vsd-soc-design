
# Floorplanning:

# D2_SK1_L6 ... D2_SK1_L8

**will:**
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

**and run the floorplaner**

cd $WD

docker

flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a -tag 16-12_12-43

puts "$::env(FP_CORE_UTIL) =50?"

puts "$::env(FP_ASPECT_RATIO) =0.75?"

puts "$::env(FP_CORE_MARGIN) =0?"

puts "$::env(FP_IO_HMETAL) =3?"

puts "$::env(FP_IO_VMETAL) =4?"

puts "$::env(FP_TAPCELL_DIST) =14?"

puts "$::env(FP_IO_MODE) =1?"

run_floorplan

![image](https://github.com/user-attachments/assets/8109629b-5971-4e23-9cda-ba18494c3cc9)

![image](https://github.com/user-attachments/assets/4d0cb450-fbc4-410f-849e-f73c68f1aea6)


## check ioplacerlog:

gedit $D/$R/logs/floorplan/4-ioPlacer.log

## check result:

gedit $D/$R/results/floorplan/picorv32a.floorplan.def &

![image](https://github.com/user-attachments/assets/997b5c05-a245-4e62-bb6d-2e7d1701ecf3)

horizontal pads are indeed in met2:

![image](https://github.com/user-attachments/assets/e889cbb2-cdd8-45d8-a66e-787aff5191cc)

vertical pads are indeed in met3:

![image](https://github.com/user-attachments/assets/3fe933bf-d230-4555-bc98-bce44864e515)


## read the floorplan .def file with Magic:

magic -T $T lef read $D/$R/tmp/merged.lef def read $D/$R/results/floorplan/picorv32a.floorplan.def &

![image](https://github.com/user-attachments/assets/0d4afac0-ba8c-439d-beed-aa020f9d543a)

![image](https://github.com/user-attachments/assets/f9c7907b-519f-4189-8365-8902548e6c45)

![image](https://github.com/user-attachments/assets/75a3ab6b-1ea0-4f1f-8ce4-718088f7a493)




**The pins are equidistant, horizontal pins in metal2, vertical pins in metal3**
