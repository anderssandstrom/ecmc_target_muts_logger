## Range z
Opto range: 


range= 

set xx at upper limit

## current
 amps peak

```
# no log
camonitor -n -g10 TARGET_DU:Z-PosAct TARGET_DU:ec0-s12-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:Z-LimitMax TARGET_DU:Z-LimitMin IOC_TEST:TestNumber TARGET_DU:Z-PosCmd TARGET_DU:Z-TempAct


# log
camonitor -n -g10 TARGET_DU:Z-PosAct TARGET_DU:ec0-s12-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:Z-LimitMax TARGET_DU:Z-LimitMin IOC_TEST:TestNumber TARGET_DU:Z-PosCmd TARGET_DU:Z-TempAct | tee y.log

```
temperature rise from xx  to approx xx