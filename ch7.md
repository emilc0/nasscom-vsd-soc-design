# Building the clock tree

D4_SK1_L7

echo $::env(SYNTH_BUFFERING)
echo $::env(SYNTH_SIZING)
echo $::env(SYNTH_DRIVING_CELL)

magic -T $T lef read $D/$R/tmp/merged.lef def read $D/$R/results/placement/picorv32a.placement.def &
