# Measuring of wobbling of target wheel

Measure veritcal movements in z1 and z2 and horizontal movement in x1

--------------------------- Moderator high
                  z1 v
               ---------------------- target wheel high
              /
             /
      x1<-> |
             \
              \
               ---------------------- target wheel low
                  z2 ^                
--------------------------- Moderator low

Wheel has not been moved or rotated since teh measueremnts of alignment team. So zero position is in the fiducial points.. The optical sensors should be positioned to measuer in the fiducial points before start to use as zero position.

Extra sensors:
1. ILD230-50 (vertical from above)
2. ILD230-100 (vertical from below)
3. Micro Epsilon fork sensor,46mm (horizontal)


## Logging should include:

* velocity last sector
* actual psoition
* eddy current sensors
* all optical micro epsilon sensors (teh extra sensors)

camonitor 

From drive system:
TARGET_DU:Rotation-PosAct 
TARGET_DU:Rotation-VelLastSecorAct 

From muts logger system:
TARGET_MUTS_LOGGER:m0s00x-AI01
TARGET_MUTS_LOGGER:m0s00x-AI02
TARGET_MUTS_LOGGER:m0s00x-AI03
TARGET_MUTS_LOGGER:m0s00x-AI04

Extra sensors:
TARGET_MUTS_LOGGER:m0s00x-Enc01
TARGET_MUTS_LOGGER:m0s00x-Enc01
TARGET_MUTS_LOGGER:m0s00x-Enc01






