## Range x
Opto range: 28.83..70.82

41.99mm range

set 21 at upper limit


## current
8 amps peak

```
# no log
camonitor -n -g10 TARGET_DU:X-PosAct TARGET_DU:ec0-s10-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:X-LimitMax TARGET_DU:X-LimitMin IOC_TEST:TestNumber TARGET_DU:X-PosCmd TARGET_DU:X-TempAct


# log
camonitor -n -g10 TARGET_DU:X-PosAct TARGET_DU:ec0-s10-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:X-LimitMax TARGET_DU:X-LimitMin IOC_TEST:TestNumber TARGET_DU:X-PosCmd TARGET_DU:X-TempAct | tee x.log

```

Forgot to log temp in first test but temperature increase from 28 to 48degC

# X max
Stops at ca 21.18mm (engages before, target velo 0.2, acc 0.1)

# X max max
Stops and disables at ca 23.12mm

# X min
Stops at -21.15 (engages before, target velo 0.2, acc 0.1)

# X min min
Stops and disables at -22.9mm
