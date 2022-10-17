# Out of round measurements with ILD2300-100 sensor of encoder mount

## Start IOC
```
iocsh start_ild2300-100.script
```

## Log data from sensor
```
camonitor IOC_TEST:m0s000-Enc01-PosAct | tee data.log
```

