## Range z
Opto range: 

range= 21.17..44.14 = 22.97mm range

43.65 -15
-15.0+43.65-21.17=7.48
Set upper homing to 7.5



lim min -1.76mm (also +-2mm)


set xx at upper limit

## current
 amps peak

```
# no log
camonitor -n -g10 TARGET_DU:Z-PosAct TARGET_DU:ec0-s12-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:Z-LimitMax TARGET_DU:Z-LimitMin TARGET_DU:Z-LimitMinPark IOC_TEST:TestNumber TARGET_DU:Z-PosCmd TARGET_DU:Z-TempAct


# log
camonitor -n -g10 TARGET_DU:Z-PosAct TARGET_DU:ec0-s12-EL7201-PosAct IOC_TEST:ILD_DownSample TARGET_DU:Z-LimitMax TARGET_DU:Z-LimitMin TARGET_DU:Z-LimitMinPark IOC_TEST:TestNumber TARGET_DU:Z-PosCmd TARGET_DU:Z-TempAct | tee z.log

```
temperature rise from xx  to approx xx

# Cams

Redesign of low limit cam would be great so it's activated all the way down to park limit. The same for LowLowLim

# GUI
Need to visualize correct limit switch in GUI depending on if parkingrange or not
