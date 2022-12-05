
# homing
Seems the centre of sector 1 is approx. 195 deg offset from homing position. The centre of homing sensor hole is then in the direction of the x axis. Need alignment team to confirm.

camonitor -g10 TARGET_DU:Rotation-PosCmd TARGET_DU:Rotation-PosAct TARGET_DU:Rotation-TorqueAct TARGET_DU:Rotation-VelAct | tee homingProc.log
