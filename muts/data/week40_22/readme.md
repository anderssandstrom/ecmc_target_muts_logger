# Calibrating system with aligment team XYZ position

## in bucket Z
Zero motor in bucket -12.219

Zero laser 19.559


## 3mm up Z

motor -9.219
laser 21.423  

increase in laser 21.423-19.559=1.87mm

## Move 10mm more up Z

motor setpoint then 0.781
opto 31.555=> movement optical 31.555-21.423=10.132mm


## move y 2mm
logs

## move y 2.3 more (to 4.3)
logs

now teh eddy current sensors show rather equal values.

## move x minus 0.2

## Now at operating position in xyz
Took log (have not homed motors)

took some resolver measurements camonitor -g10 TARGET_DU:ec0-s10-EL7201-PosAct TARGET_DU:ec0-s11-EL7201-PosAct TARGET_DU:ec0-s12-EL7201-PosAct | tee resolver_zero_op_pos.log
also:

