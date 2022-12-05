# Test startup torque with and without radial load

camonitor -g10 TARGET_DU:Rotation-PosAct TARGET_DU:Rotation-TorqueAct TARGET_DU:Rotation-VelAct | tee torque_0x.log0

5 starts with load and 5 without radial load was executed. No big difference in startup torque could be observed.

The first startup with radial load was the first startup after weekend with a cold system and the startup torque is clearly higher. 
The temp of the motor at the very first trial was 15.1 deg according to PV.



