# xyz motion tests

## Startup script 
```
iocsh start_ioc_xyz.script
```
## Data collection

* IOC_TEST:m0s002-Enc01-PosAct ILD2300-100mm (used as ref sensor for xyz tests)
* IOC_TEST:m0s011-Enc01-PosAct ILD2300-50mm  (hight measurement of target wheel)
* IOC_TEST:m0s005-AI01 (eddy current sensor (horizontal 0deg)
* IOC_TEST:m0s005-AI02 (eddy current sensor (horizontal 120deg)
* IOC_TEST:m0s005-AI03 (eddy current sensor (horizontal 240deg)
* IOC_TEST:m0s005-AI04 (eddy current sensor (vertical)
* TARGET_DU:X-PosAct   (open loop counter X)
* TARGET_DU:Y-PosAct   (open loop counter Y)
* TARGET_DU:Z-PosAct   (open loop counter Z)
* TARGET_DU:X-PosAct02 (open loop counter X)
* TARGET_DU:Y-PosAct02 (open loop counter Y)
* TARGET_DU:Z-PosAct02 (open loop counter Z)

```
camonitor -g10 IOC_TEST:m0s002-Enc01-PosAct IOC_TEST:m0s011-Enc01-PosAct IOC_TEST:m0s005-AI01 IOC_TEST:m0s005-AI02 IOC_TEST:m0s005-AI03 IOC_TEST:m0s005-AI04 TARGET_DU:X-PosAct TARGET_DU:Y-PosAct TARGET_DU:Z-PosAct TARGET_DU:X-PosAct02 TARGET_DU:Y-PosAct02 TARGET_DU:Z-PosAct02
```


Seems ILD2300-100 is not good.. needs to redo tests with 50mm sensor..
