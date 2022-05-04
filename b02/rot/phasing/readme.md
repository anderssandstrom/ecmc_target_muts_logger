# Phasing
Phasing for atleast one hour like stated in chess doc

Phase mode:

Mode=Superimpose

Noise after approx 1h running, maybe encoder scratching against encoder ring

## Log data:
```
camonitor -g10  TARGET_DU:Rotation-PhaseErrorMMAct TARGET_DU:Rotation-VelLastSectorAct | tee phase0x.log
```
