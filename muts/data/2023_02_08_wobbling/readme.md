# Measuring of wobbling of target wheel

Measure veritcal movements in z1 and z2 and horizontal movement in x1
```
--------------------------- Moderator high
                  z1 v
               ---------------------- target wheel high
              /
             /
      x1<-> |
             \
              \
               ---------------------- target wheel low
                  z2 ^                
--------------------------- Moderator low
```
Wheel has not been moved or rotated since teh measueremnts of alignment team. So zero position is in the fiducial points.. The optical sensors should be positioned to measure in the fiducial points before start to use as zero position.

Extra sensors:
1. ILD230-50 (vertical from below)
2. ILD230-100 (vertical from above)
3. Micro Epsilon fork sensor,46mm (horizontal)

## ioc
ecmc_target_muts_logger:

start_ioc_wobbling_20230208.script

then also data from TARGET_DU ioc

## Logging should include:

* velocity last sector
* actual psoition
* eddy current sensors
* all optical micro epsilon sensors (teh extra sensors)

```
camonitor 

From drive system:
TARGET_DU:Rotation-PosAct 
TARGET_DU:Rotation-VelLastSecorAct 

From muts logger system:
TARGET_MUTS_LOGGER:m0s002-AI01
TARGET_MUTS_LOGGER:m0s002-AI02
TARGET_MUTS_LOGGER:m0s002-AI03
TARGET_MUTS_LOGGER:m0s002-AI04


Extra sensors:
Above: smaller value then lower position of wheel
TARGET_MUTS_LOGGER:m0s013-Enc01-PosAct 
Horizontal 
TARGET_MUTS_LOGGER:m0s014-Enc01-PosAct
Below smmaler value higher position of wheel
TARGET_MUTS_LOGGER:m0s015-Enc01-PosAct


TARGET_MUTS_LOGGER:m0s00x-Enc01
TARGET_MUTS_LOGGER:m0s00x-Enc01
TARGET_MUTS_LOGGER:m0s00x-Enc01

camonitor TARGET_MUTS_LOGGER:m0s013-Enc01-PosAct TARGET_MUTS_LOGGER:m0s014-Enc01-PosAct TARGET_MUTS_LOGGER:m0s015-Enc01-PosAct TARGET_MUTS_LOGGER:m0s002-AI01 TARGET_MUTS_LOGGER:m0s002-AI02 TARGET_MUTS_LOGGER:m0s002-AI03 TARGET_MUTS_LOGGER:m0s002-AI04 TARGET_DU:Rotation-PosAct TARGET_DU:Rotation-VelLastSectorAct
```






zero.log standstill

test01.log ramp up and stop due to indrawarning.

test02.log rampup to 5rpm (high torque)

test03.log a few revs at 5rpm constant velo

test04.log a few revs at 5rpm constant velo same smaple rate on all

test05.log a few revs at 5rpm constant velo same smaple rate on 200Hz 

test06.log a few revs at 5rpm constant velo same smaple rate on 1000Hz 

test07.log a rampup 5-9.5rpm

test08.log a at 10rpm 1khz

test09.log a at 15rpm 1khz

test10.log a at 18rpm 1khz

test11.log a at 20rpm 1khz

test12.log a at 23.333rpm 1khz

test13.log a at 23.333rpm 1khz

test14.log rampup to 23.8 1khz

test15.log to test23 rampup to from 24.x to 1khz

test24.log 25 rpm constant velo
test25.log 25 rpm constant velo


test26.log rampdown 25rpm to 0rpm disable (no power)


## Zero
```

Sensor s13: above (100mm range)
TARGET_MUTS_LOGGER:m0s013-Enc01-PosAct[746] 33.2977..33.3042, mean: 33.30164798927614, std: 0.001173330759960683

Sensor s14: Horizontal
TARGET_MUTS_LOGGER:m0s014-Enc01-PosAct[397] 14.446..14.449, mean: 14.447725440806048, std: 0.0007116749460704261

Sensor s15: below (50mm range)
TARGET_MUTS_LOGGER:m0s015-Enc01-PosAct[116] 18.6795..18.6815, mean: 18.680729310344823, std: 0.00045957574914655695


```

## s13
```
cat test_25.log | grep s013 | python ~/sources/ecmccomgui/pyDataManip/add.py -33.30165 | python ~/sources/ecmccomgui/pyDataManip/scale.py -1 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py

```

## s14
```
cat test_25.log | grep s014 | python ~/sources/ecmccomgui/pyDataManip/add.py -14.447725 | python ~/sources/ecmccomgui/pyDataManip/scale.py -1 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
```

## s15
```
cat test_25.log | grep s015 | python ~/sources/ecmccomgui/pyDataManip/add.py -18.680729 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
```

# Rampdown

## s13
```
cat test_26.log | grep s013 | python ~/sources/ecmccomgui/pyDataManip/add.py -33.30165 | python ~/sources/ecmccomgui/pyDataManip/scale.py -1 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py

```

## s14
```
cat test_26.log | grep s014 | python ~/sources/ecmccomgui/pyDataManip/add.py -14.447725 | python ~/sources/ecmccomgui/pyDataManip/scale.py -1 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
```

## s15
```
cat test_26.log | grep s015 | python ~/sources/ecmccomgui/pyDataManip/add.py -18.680729 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
```



# Test at 20 rpm test_11

## s13
```
cat test_11.log | grep s013 | python ~/sources/ecmccomgui/pyDataManip/add.py -33.30165 | python ~/sources/ecmccomgui/pyDataManip/scale.py -1 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py

```

## s14
```
cat test_11.log | grep s014 | python ~/sources/ecmccomgui/pyDataManip/add.py -14.447725 | python ~/sources/ecmccomgui/pyDataManip/scale.py -1 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
```

## s15
```
cat test_11.log | grep s015 | python ~/sources/ecmccomgui/pyDataManip/add.py -18.680729 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
```

# Test at 5 rpm test_03

## s13
```
cat test_03.log | grep s013 | python ~/sources/ecmccomgui/pyDataManip/add.py -33.30165 | python ~/sources/ecmccomgui/pyDataManip/scale.py -1 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py

```

## s14
```
cat test_03.log | grep s014 | python ~/sources/ecmccomgui/pyDataManip/add.py -14.447725 | python ~/sources/ecmccomgui/pyDataManip/scale.py -1 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
```

## s15
```
cat test_03.log | grep s015 | python ~/sources/ecmccomgui/pyDataManip/add.py -18.680729 | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
```
