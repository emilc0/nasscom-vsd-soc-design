Run openLANE flow / Prepare design

export WD=~/Desktop/work/tools/openlane_working_dir/openlane

cd $WD

docker

![image](https://github.com/user-attachments/assets/e92a482f-0b48-4469-9e00-94635dd243e3)

flow.tcl -interactive

package require openlane 0.9

![image](https://github.com/user-attachments/assets/ad651f49-75c1-47db-8642-4d565ed2360d)

prep -design picorv32a

![image](https://github.com/user-attachments/assets/3aa5bec3-3973-407d-81d3-5724129053a8)

(directory ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-12_12-43 created)
![image](https://github.com/user-attachments/assets/ff2d09f1-fe56-4961-b53f-b26660efd2e4)

(inside: folder structure needed by openLANE flow)
![image](https://github.com/user-attachments/assets/13da1d7e-eb89-431f-a2c4-67c7cc7531c6)

(tmp/merged.lef created - contains stdcells lef + tech lef)
![image](https://github.com/user-attachments/assets/ff06b1d5-db79-42cf-b493-98f227c2b64e)

(run synthesis)
run_synthesis
![image](https://github.com/user-attachments/assets/31126b29-5069-4d09-b2be-45e08c3af9fd)

(synthesis done, tns=-759.46ns, wns=-24.89ns)
![image](https://github.com/user-attachments/assets/4ae09d85-c520-4c9c-b2ef-bbaf0b22121f)

(what is the clock period?)
![image](https://github.com/user-attachments/assets/357a3a55-1d2e-4ba4-abb8-a301cdd2037a)

