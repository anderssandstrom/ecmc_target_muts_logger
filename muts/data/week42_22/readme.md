# Out of round measurements with ILD2300-100 sensor of encoder mount

## Start IOC
```
iocsh start_ild2300-100.script
```

## Log data from sensor
```
camonitor IOC_TEST:m0s000-Enc01-PosAct | tee data.log
```

# Start test

## before ref xyz motors

Before zeroing the unit was in position:
```
TARGET_DU:X-PosAct             2022-10-19 10:27:20.636836 -0.1999976074  
TARGET_DU:X-PosAct02           2022-10-19 10:31:09.800605 13321345  
TARGET_DU:Y-PosAct             2022-10-19 10:27:20.636842 4.299998401 HIGH MINOR
TARGET_DU:Y-PosAct02           2022-10-19 10:31:09.346567 4294387172  
TARGET_DU:Z-PosAct             2022-10-19 10:27:20.636849 0.780999918  
TARGET_DU:Z-PosAct02           2022-10-19 10:31:09.395193 4224719658

X dir laser:
IOC_TEST:m0s011-Enc01-PosAct   2022-10-19 10:31:10.680508 30.716488  
IOC_TEST:m0s011-Enc01-PosAct   2022-10-19 10:31:10.780508 30.715876  
IOC_TEST:m0s011-Enc01-PosAct   2022-10-19 10:31:10.880504 30.715672  
IOC_TEST:m0s011-Enc01-PosAct   2022-10-19 10:31:11.180548 30.71608  
IOC_TEST:m0s011-Enc01-PosAct   2022-10-19 10:31:11.380509 30.715876  
IOC_TEST:m0s011-Enc01-PosAct   2022-10-19 10:31:11.480508 30.715264  
IOC_TEST:m0s011-Enc01-PosAct   2022-10-19 10:31:11.580506 30.71506 

Z dir laser:
IOC_TEST:m0s002-Enc01-PosAct   2022-10-19 10:31:09.780509 22.817  
IOC_TEST:m0s002-Enc01-PosAct   2022-10-19 10:31:09.880509 22.817816  
IOC_TEST:m0s002-Enc01-PosAct   2022-10-19 10:31:09.980546 22.818224  
IOC_TEST:m0s002-Enc01-PosAct   2022-10-19 10:31:10.080507 22.818632  
IOC_TEST:m0s002-Enc01-PosAct   2022-10-19 10:31:10.180506 22.819448  
IOC_TEST:m0s002-Enc01-PosAct   2022-10-19 10:31:10.280507 22.817  
IOC_TEST:m0s002-Enc01-PosAct   2022-10-19 10:31:10.380507 22.813736  

Eddy current:
IOC_TEST:m0s005-AI02           2022-10-19 10:31:10.880504 12.09795551  
IOC_TEST:m0s005-AI03           2022-10-19 10:31:10.880504 11.59000533  
IOC_TEST:m0s005-AI04           2022-10-19 10:31:10.880504 12.10958332  
IOC_TEST:m0s005-AI02           2022-10-19 10:31:10.980508 12.10256345  
IOC_TEST:m0s005-AI03           2022-10-19 10:31:10.980508 11.59107384  
IOC_TEST:m0s005-AI04           2022-10-19 10:31:10.980508 12.10814299  
IOC_TEST:m0s005-AI01           2022-10-19 10:31:11.080509 10.79134204  
IOC_TEST:m0s005-AI02           2022-10-19 10:31:11.080509 12.10717138  
IOC_TEST:m0s005-AI03           2022-10-19 10:31:11.080509 11.59214234  
IOC_TEST:m0s005-AI04           2022-10-19 10:31:11.080509 12.10742282  
IOC_TEST:m0s005-AI01           2022-10-19 10:31:11.180548 10.79230579  
IOC_TEST:m0s005-AI02           2022-10-19 10:31:11.180548 12.10870736  
IOC_TEST:m0s005-AI04           2022-10-19 10:31:11.180548 12.10958332  
IOC_TEST:m0s005-AI01           2022-10-19 10:31:11.280506 10.80001581  
IOC_TEST:m0s005-AI04           2022-10-19 10:31:11.280506 12.10886315  
IOC_TEST:m0s005-AI01           2022-10-19 10:31:11.380509 10.7980883  
IOC_TEST:m0s005-AI02           2022-10-19 10:31:11.380509 12.10102747  
IOC_TEST:m0s005-AI03           2022-10-19 10:31:11.380509 11.59107384  
IOC_TEST:m0s005-AI01           2022-10-19 10:31:11.480508 10.7942333  
IOC_TEST:m0s005-AI03           2022-10-19 10:31:11.480508 11.59000533  
IOC_TEST:m0s005-AI01           2022-10-19 10:31:11.580506 10.79230579  
IOC_TEST:m0s005-AI02           2022-10-19 10:31:11.580506 12.10870736  
IOC_TEST:m0s005-AI03           2022-10-19 10:31:11.580506 11.59534786 
```
## after ref xyz motors

Now motors in 0,0,0
```
TARGET_DU:X-PosAct             2022-10-19 10:36:02.774290 0  
TARGET_DU:X-PosAct02           2022-10-19 10:37:19.802651 13321329

TARGET_DU:Y-PosAct             2022-10-19 10:36:06.319200 0  
TARGET_DU:Y-PosAct02           2022-10-19 10:37:19.848564 4294387202

TARGET_DU:Z-PosAct             2022-10-19 10:36:11.867072 0  
TARGET_DU:Z-PosAct02           2022-10-19 10:37:19.897147 4224719651
```
# Data collection ISO test

```
camonitor -g10 -n IOC_TEST:m0s002-Enc01-PosAct IOC_TEST:m0s011-Enc01-PosAct IOC_TEST:m0s005-AI01 IOC_TEST:m0s005-AI02 IOC_TEST:m0s005-AI03 IOC_TEST:m0s005-AI04 TARGET_DU:X-PosAct TARGET_DU:Y-PosAct TARGET_DU:Z-PosAct TARGET_DU:X-PosAct02 TARGET_DU:Y-PosAct02 TARGET_DU:Z-PosAct02 IOC_TEST:TestNumber TARGET_DU:X-LimitMax TARGET_DU:X-LimitMin TARGET_DU:Y-LimitMax TARGET_DU:Y-LimitMin TARGET_DU:Z-LimitMax TARGET_DU:Z-LimitMin TARGET_DU:X-PosCmd TARGET_DU:Y-PosCmd TARGET_DU:Z-PosCmd | tee x_axis_lim.log
```

## X axis

* Loose brakes  OK
* Check switches OK

Low -5.4
Low Low -6
Hi  5.6
Hi Hi 6.4

Seems axis is slipping.. Test higher current..

## Y axis

Low -4.8
Low Low -6.9

Hi  5.5
Hi Hi 5.6

## Z Axis

Z zero is 0.6-0.7mm higher than b02 tests since adjustment of feet of drive unit is to low. Therefore the z range is shifted approx 0.6 in negative direction (swithces are not moved).

Low     -2.0
Low Low -3.0
Hi       7.0
Hi Hi    8.1

Parking swithes not tested since we do not want to park the wheel. Reason is manual measurements of axis out of round could be affected (theory is that the shaft can be offset to the socket/collar then it could resolut in different centere point of axis every time it is offloaded/parked. The size of the movement could then be determined as the play between the shaft and the socket/collar)..
BTW, the measured out of round was approx 0.15mm (shaft centre offset vs "bearing"/rotation-centre).
