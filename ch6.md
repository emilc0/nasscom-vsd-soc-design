D4_SK1_L7

Try a timing-driven synthesis (strike a balance delay/area)

**SYNTH_STRATEGY: Strategies for abc logic synthesis and technology mapping
Possible values are DELAY/AREA 0-4/0-3; the first part refers to the optimization target of the synthesis strategy (area vs. delay) and the second one is an index.
(Default: AREA 0)**

Initially:

set ::env(SYNTH_STRATEGY) "AREA 0"

echo $::env(SYNTH_STRATEGY)

=> "AREA 0"

SYNTH_STRATEGY=2 => area 228,590, tns=-1529.21, wns=-15.96



set ::env(SYNTH_STRATEGY) 1

Area will increase, timing will improve:



## set ::env(SYNTH_STRATEGY) "AREA 0"  (flow default)

Chip area for module '\picorv32a': 149084.233600

tns -4560.27

wns -28.03



## set ::env(SYNTH_STRATEGY) 2  (used in the videos ?! , not accepted by the tool)



## set ::env(SYNTH_STRATEGY) "DELAY 2"

Chip area for module '\picorv32a': 206839.625600

tns -773.56

wns -6.26



## set ::env(SYNTH_STRATEGY) "DELAY 0"

Chip area for module '\picorv32a': 198778.144000

tns -788.53

wns -5.52


## set ::env(SYNTH_STRATEGY) "DELAY 3"

Chip area for module '\picorv32a': 181510.332800

tns -983.13

wns -7.05



**choose set ::env(SYNTH_STRATEGY) "DELAY 0"**





