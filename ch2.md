# Synthesis

## Info about synthesis switches :
gedit $WD/configuration/README.md

## The synthesis switches are comming, in order, from:

**1. $WD/configuration/synthesis.tcl**

![image](https://github.com/user-attachments/assets/418df43a-fc21-43df-8419-610c3d291331)

**2. $D/config.tcl**

![image](https://github.com/user-attachments/assets/2e73033f-c875-4036-ae1b-f6d16bda6981)

**3. $D/sky130A_sky130_fd_sc_hd_config.tcl (highest priority**

![image](https://github.com/user-attachments/assets/0f2c726d-f75a-48d5-8422-47ac10577102)

**The "prep" command stores the actual switches in**
 $D/$R/config.tcl



## Runing the synthesis:
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

## Compute flop ratio = (nr of flop-flops)/(total number off stdcells) :

![image](https://github.com/user-attachments/assets/4594ef7e-4a28-4afd-abe5-ab710ef1824b)

**Flop ratio = 100*1613/14876 = 10.84%**

## Re-synthetizing with a clock period of 10ns (based on the clarification from WhatsApp group)
**(reuse the "run" directory after restarting openLANE)**

cd $WD

docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a -tag 16-12_12-43 -overwrite

echo $::env(CLOCK_PERIOD)

set ::env(CLOCK_PERIOD) 10

echo $::env(CLOCK_PERIOD)

run_synthesis

![image](https://github.com/user-attachments/assets/559fb349-fc33-4854-8d1e-3597c795ad42)
**tns -4606.62 wns -28.94**

![image](https://github.com/user-attachments/assets/b865af40-5b33-43cb-a42a-8485a0f8e9f1)

**number of flops: 1,613, number of stdcells 14,876** 

**Flop ratio = 100*1613/14876 = 10.84%**


## TODO: explain this warning:
![image](https://github.com/user-attachments/assets/b5040775-11d8-4531-9702-6c903dddac6b)

**the library /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.ref/sky130_fd_sc_hd/lib/sky130_fd_sc_hd__ff_n40C_1v95.lib  exists:**
![image](https://github.com/user-attachments/assets/b1d1073c-9a44-4893-bd97-b7c04f5cc1ee)

**and the operating_condition ("ff_n40C_1v95") is defined:**
![image](https://github.com/user-attachments/assets/baf0c47a-8dde-4903-a6ac-f2dca1103a9b)

**the library /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.ref/sky130_fd_sc_hd/lib/sky130_fd_sc_hd__ss_100C_1v60.lib  exists:**
![image](https://github.com/user-attachments/assets/365ded0c-b58f-409f-bbf8-5e4326110897)

**and the operating_condition ("ss_100C_1v60") is defined:**
![image](https://github.com/user-attachments/assets/c56def9a-bcf1-40fe-aa75-98848c9d7b05)






