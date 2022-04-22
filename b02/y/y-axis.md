## Range y
Opto range: 
70.74..28.48

range= 42.26

set 21 at upper limit

## current
8 amps peak

```
# no log
camonitor -n -g10 TARGET_DU:Y-PosAct TARGET_DU:ec0-s11-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:Y-LimitMax TARGET_DU:Y-LimitMin IOC_TEST:TestNumber TARGET_DU:Y-PosCmd TARGET_DU:Y-TempAct


# log
camonitor -n -g10 TARGET_DU:Y-PosAct TARGET_DU:ec0-s11-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:Y-LimitMax TARGET_DU:Y-LimitMin IOC_TEST:TestNumber TARGET_DU:Y-PosCmd TARGET_DU:Y-TempAct | tee y.log

```
temperature rise from 28 to approx 42

# Y max
Stops at 21.2 (engages before, target velo 0.2, acc 0.1)

# Y max max
Stops and disables at approx 23.0mm

# Y min
Stops at -20.9 (engages before, target velo 0.2, acc 0.1)

# Y min min
Stops and disables at -22.75
