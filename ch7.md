# Repair slack after synthesis

D4_SK1_L7

echo $::env(SYNTH_STRATEGY)

DELAY 0

echo $::env(SYNTH_BUFFERING)

(1, already on, fine)

echo $::env(SYNTH_SIZING)

set ::env(SYNTH_SIZING) 1

(was 0, put it at 1)

echo $::env(SYNTH_DRIVING_CELL)

(sky130_inv8, ok)

gedit 2-opensta.timing.rpt  &

![image](https://github.com/user-attachments/assets/9e8ddfb4-ef6a-4014-a1f0-e9dfd6652730)


## SET_strategy in the video is ko

set ::env(SYNTH_STRATEGY) 1

![image](https://github.com/user-attachments/assets/944bee52-d364-4916-b7a8-2945e5c0fb1d)

Old description:
`SYNTH_STRATEGY` | Strategies for abc logic synthesis and technology mapping <br> Possible values are `DELAY/AREA 0-3/0-2`; the first part refers to the optimization target of the synthesis
"setting 1 => area will increase, timing will improve compared to setting 2"





magic -T $T lef read $D/$R/tmp/merged.lef def read $D/$R/results/placement/picorv32a.placement.def &
