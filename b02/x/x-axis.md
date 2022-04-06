## Range x
Opto range: 28.83..70.82

41.99mm range

set 21 at upper limit


## current
8 amps peak

```
# no log
camonitor -n -g10 TARGET_DU:X-PosAct TARGET_DU:ec0-s10-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:X-LimitMax TARGET_DU:X-LimitMin IOC_TEST:TestNumber TARGET_DU:X-PosCmd


# log
camonitor -n -g10 TARGET_DU:X-PosAct TARGET_DU:ec0-s10-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:X-LimitMax TARGET_DU:X-LimitMin IOC_TEST:TestNumber TARGET_DU:X-PosCmd | tee x.log

```


temperature increase from 28 to 48degC
