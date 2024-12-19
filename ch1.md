***D1_SK3_L1 ... D1_SK3_L5***

**Prepare design**

export WD=~/Desktop/work/tools/openlane_working_dir/openlane

export D=~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a

export T=$WD/../pdks/sky130A/libs.tech/magic/sky130A.tech

cd $WD

docker

![image](https://github.com/user-attachments/assets/e92a482f-0b48-4469-9e00-94635dd243e3)

flow.tcl -interactive

package require openlane 0.9

![image](https://github.com/user-attachments/assets/ad651f49-75c1-47db-8642-4d565ed2360d)

prep -design picorv32a

**if restaring the flow or restarting docker:**

**starting anew**

prep -design picorv32a -tag 16-12_12-43 -overwrite

**start from where we left**

prep -design picorv32a -tag 16-12_12-43

![image](https://github.com/user-attachments/assets/3aa5bec3-3973-407d-81d3-5724129053a8)

**directory ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-12_12-43 created :**

![image](https://github.com/user-attachments/assets/ff2d09f1-fe56-4961-b53f-b26660efd2e4)

**inside: folder structure needed by openLANE flow:**
![image](https://github.com/user-attachments/assets/13da1d7e-eb89-431f-a2c4-67c7cc7531c6)

**tmp/merged.lef created - contains stdcells lef + tech lef**
![image](https://github.com/user-attachments/assets/ff06b1d5-db79-42cf-b493-98f227c2b64e)


**Useful files:**

gedit $WD/configuration/README.md $WD/configuration/synthesis.tcl $D/config.tcl $D/sky130A_sky130_fd_sc_hd_config.tcl $D/$R/config.tcl &


