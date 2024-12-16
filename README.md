**D1_SK3_L1 - D1_SK3_L5**

**Run openLANE flow**

**Prepare design**

export WD=~/Desktop/work/tools/openlane_working_dir/openlane

export D=~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a

cd $WD

docker

![image](https://github.com/user-attachments/assets/e92a482f-0b48-4469-9e00-94635dd243e3)

flow.tcl -interactive

package require openlane 0.9

![image](https://github.com/user-attachments/assets/ad651f49-75c1-47db-8642-4d565ed2360d)

prep -design picorv32a

![image](https://github.com/user-attachments/assets/3aa5bec3-3973-407d-81d3-5724129053a8)

**directory ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-12_12-43 created :**

![image](https://github.com/user-attachments/assets/ff2d09f1-fe56-4961-b53f-b26660efd2e4)

**inside: folder structure needed by openLANE flow:**
![image](https://github.com/user-attachments/assets/13da1d7e-eb89-431f-a2c4-67c7cc7531c6)

**tmp/merged.lef created - contains stdcells lef + tech lef**
![image](https://github.com/user-attachments/assets/ff06b1d5-db79-42cf-b493-98f227c2b64e)

**Read about synthesis switches here:**

gedit $WD/configuration/README.md

**The synthesis switches are comming from:**

**$WD/configuration/synthesis.tcl**

![image](https://github.com/user-attachments/assets/418df43a-fc21-43df-8419-610c3d291331)

**$D/config.tcl**

![image](https://github.com/user-attachments/assets/2e73033f-c875-4036-ae1b-f6d16bda6981)

**$D/sky130A_sky130_fd_sc_hd_config.tcl (highest priority**

![image](https://github.com/user-attachments/assets/0f2c726d-f75a-48d5-8422-47ac10577102)

The actual switches used by the flow are put in

$D/$R/config.tcl

**Run synthesis:**

run_synthesis

![image](https://github.com/user-attachments/assets/31126b29-5069-4d09-b2be-45e08c3af9fd)

**Synthesis done, tns=-759.46ns, wns=-24.89ns**

![image](https://github.com/user-attachments/assets/6ae0d4d0-5c1d-4cae-8dbb-eeb453492d09)

**The netlist was created: picorv32a.synthesis.v**

![image](https://github.com/user-attachments/assets/af18136e-869a-4ff6-b841-d0d76a17b3de)

**What was the clock period ?**

![image](https://github.com/user-attachments/assets/357a3a55-1d2e-4ba4-abb8-a301cdd2037a)

**Find out where it was defined:**

![image](https://github.com/user-attachments/assets/f15ba0a8-c576-4399-8dc7-81c53b84113d)
![image](https://github.com/user-attachments/assets/e34a43a8-43c3-4413-901c-09c92fc46da2)

![image](https://github.com/user-attachments/assets/47c2c7d5-3b30-4fd0-aade-bbac8281cbb3)
![image](https://github.com/user-attachments/assets/432d4642-621f-4d4c-b37a-2c748fb37dce)

**Compute flop ratio = (nr of flop-flops)/(total number off stdcells) :**

![image](https://github.com/user-attachments/assets/4594ef7e-4a28-4afd-abe5-ab710ef1824b)

**Flop ratio = 100*1613/14876 = 10.84%**

**re-synthetizing at 10ns (after exiting openLANE), reuse run directory**

cd $WD
docker
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a -tag 16-12_12-43 -overwrite
echo $::env(CLOCK_PERIOD)
set ::env(CLOCK_PERIOD) 10
echo $::env(CLOCK_PERIOD)
run_synthesis

![image](https://github.com/user-attachments/assets/2486cacc-1e30-4bb6-a4bd-baeea024c32d)

**tns -4581.81 wns -28.94**

![image](https://github.com/user-attachments/assets/b865af40-5b33-43cb-a42a-8485a0f8e9f1)

**number of flops: 1,613, number of stdcells 14,876** 
**Flop ratio = 100*1613/14876 = 10.84%**



**D2_SK1_L6**

**Floorplanning:**

**-set die area**

**-set core area**

**-set aspect ratio**

**-set utilization factor**

**-pace I/O cells**

**-macro placement**



**Read about floorplan switches here:**

gedit $WD/configuration/README.md

** The floorplan switches are read (in this order) from: **

** $WD/configuration/floorplan.tcl **

** $D/config.tcl ** 

** $D/sky130A_sky130_fd_sc_hd_config.tcl **

The actual switches used by the flow are put in

$D/$R/config.tcl





