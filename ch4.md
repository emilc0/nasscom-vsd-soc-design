# Placement

**D2 SK2 L5**


![image](https://github.com/user-attachments/assets/0a8d91c2-9abc-4be2-8d1f-e0df4250f36a)

![image](https://github.com/user-attachments/assets/66ceefbb-6809-4455-aff8-09798300d1d2)


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

![image](https://github.com/user-attachments/assets/ba9178f1-b531-44ff-be9c-f0e0e52c07c3)

puts "$::env(FP_SIZING) ="absolute ?"

puts "$::env(DIE_AREA) = 0 0 1250 1250 ?"

run_floorplan

$D/$R/results/floorplan/picorv32a.floorplan.def:
![image](https://github.com/user-attachments/assets/8765f2d9-997d-41d1-adc1-dfe08805c69d)

DIEAREA ( 0 0 ) ( 1250000 1250000 ) ;

(as requested)

run_placement

![image](https://github.com/user-attachments/assets/23247c9c-9beb-4d48-8609-b536c08e4200)

The utilization is 10% (very low, but at least the placement passes. 
Will look later for min DIE_SIZE for which the placement do not give the previous error.


![image](https://github.com/user-attachments/assets/8614ef12-ec08-4086-86b8-c40653be93aa)






