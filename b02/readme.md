# B02 tests

## ILD2300 sensor
```
IOC_TEST:m0s005-Enc01-PosAct
```

## Resolver PVs
```
TARGET_DU:ec0-s10-EL7201-PosAct
TARGET_DU:ec0-s11-EL7201-PosAct
TARGET_DU:ec0-s12-EL7201-PosAct
```

## Open loop counter
```
TARGET_DU:X-PosAct
TARGET_DU:Y-PosAct
TARGET_DU:Z-PosAct
```

## Limits
```
TARGET_DU:X-LimitMax
TARGET_DU:X-LimitMin
TARGET_DU:X-LimitMaxMax
TARGET_DU:X-LimitMinMin

TARGET_DU:Y-LimitMax
TARGET_DU:Y-LimitMin
TARGET_DU:Y-LimitMaxMax
TARGET_DU:Y-LimitMinMin

TARGET_DU:Z-LimitMax
TARGET_DU:Z-LimitMin
TARGET_DU:Z-LimitMaxMax
TARGET_DU:Z-LimitMinMin
```

## camanitor
```
camonitor IOC_TEST:m0s005-Enc01-PosAct TARGET_DU:ec0-s10-EL7201-PosAct
```
