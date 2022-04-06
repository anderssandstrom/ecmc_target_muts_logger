## Range y
Opto range: 

```
# no log
camonitor -n -g10 TARGET_DU:Y-PosAct TARGET_DU:ec0-s10-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:Y-LimitMax TARGET_DU:Y-LimitMin IOC_TEST:TestNumber TARGET_DU:Y-PosCmd TARGET_DU:Y-TempAct


# log
camonitor -n -g10 TARGET_DU:Y-PosAct TARGET_DU:ec0-s10-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:Y-LimitMax TARGET_DU:Y-LimitMin IOC_TEST:TestNumber TARGET_DU:Y-PosCmd TARGET_DU:Y-TempAct | tee y.log

```
