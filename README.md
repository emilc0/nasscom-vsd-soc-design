**Run openLANE flow**

**Prepare design**

export WD=~/Desktop/work/tools/openlane_working_dir/openlane

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

**re-synthetizing at 10ns**

prep -design picorv32a -tag 16-12_12-43 - overwrite

![image](https://github.com/user-attachments/assets/3901a140-f98d-4453-aafd-6b5acefdd46b)



