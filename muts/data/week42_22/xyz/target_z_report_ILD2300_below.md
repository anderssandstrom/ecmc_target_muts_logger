# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/z_axis.log
* Date        : Thu Oct 20 15:12:25 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | -.00184 | 5.74079 | 50.00000 | 344.84114970
Target Position | Reference | 1.00829 | -30.96013 | 50.00000 | .00980046

# ISO 230-2 motion test

## Configuration

Setting | Value
--- | --- |
Data file | sys.stdin
Reference position source | IOC_TEST:m0s011-Enc01-PosAct
Target position source | TARGET_DU:Z-PosCmd
Test number source | IOC_TEST:TestNumber
Position count | 5 (i=1..5)
Cycle count |5 (j=1..5)
Unit | mm


## Input data

### Data forward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]


i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-1.5|-1.51821|-1.52273|-1.51389|-1.51636|-1.51883|
2|0.5|0.53131|0.52328|0.5239|0.51835|0.51876|
3|2.5|2.51294|2.50821|2.50883|2.5078|2.50574|
4|4.5|4.49684|4.49787|4.48676|4.4808|4.47874|
5|6.5|6.49205|6.48547|6.4865|6.48033|6.47498|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-1.5|-1.49785|-1.4962|-1.49805|-1.49394|-1.50114|
2|0.5|0.51362|0.49181|0.49922|0.50086|0.50086|
3|2.5|2.48456|2.48456|2.48929|2.4971|2.49093|
4|4.5|4.51186|4.50651|4.50445|4.50281|4.50116|
5|6.5|6.51653|6.51098|6.51427|6.51879|6.51756|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.01821|-0.02273|-0.01389|-0.01636|-0.01883|-0.018|
2|0.03131|0.02328|0.0239|0.01835|0.01876|0.02312|
3|0.01294|0.00821|0.00883|0.0078|0.00574|0.0087|
4|-0.00316|-0.00213|-0.01324|-0.0192|-0.02126|-0.0118|
5|-0.00795|-0.01453|-0.0135|-0.01967|-0.02502|-0.01613|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.00215|0.0038|0.00195|0.00606|-0.00114|0.00257|
2|0.01362|-0.00819|-0.00078|0.00086|0.00086|0.00127|
3|-0.01544|-0.01544|-0.01071|-0.0029|-0.00907|-0.01071|
4|0.01186|0.00651|0.00445|0.00281|0.00116|0.00536|
5|0.01653|0.01098|0.01427|0.01879|0.01756|0.01563|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|-0.00772|-0.02057|
2|0.0122|0.02184|
3|-0.001|0.01942|
4|-0.00322|-0.01715|
5|-0.00025|-0.03176|

B_avg = Axis avg. reversal error [mm]

B_avg = -0.00564 [mm]

**B = Axis reversal error [mm]**

**B = 0.03176 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.00327|0.00265|0.01307|0.01058|0.0324|
2|0.00523|0.00785|0.02092|0.03139|0.048|
3|0.00264|0.00521|0.01055|0.02084|0.03511|
4|0.00887|0.00414|0.03547|0.01655|0.04317|
5|0.00648|0.00308|0.02592|0.01234|0.05089|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.03547 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.03139 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.03547 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.04112 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.02634 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.03383 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.01992 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.06311 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.04293 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.06311 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/z_axis.log |
Reference position source | IOC_TEST:m0s011-Enc01-PosAct |
Reference gear ratio | 1.0082938424 |
Reference offset | -30.9601346857 |
Low Limit source | TARGET_DU:Z-LimitMin |
High Limit source | TARGET_DU:Z-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | -1.91746 | -1.65643 |
2 | -1.90985 | -1.65972 |
3 | -1.91602 | -1.65890 |
4 | -1.91519 | -1.66260 |
5 | -1.91334 | -1.66919 |
6 | -1.91273 | -1.66754 |
7 | -1.91129 | -1.66836 |
8 | -1.91355 | -1.66631 |
9 | -1.91129 | -1.66878 |
10 | -1.91314 | -1.66816 |
AVG   | -1.91338 | -1.66460 |
STD   | 0.00220 | 0.00451 |
Range | 0.00761 | 0.01275 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 6.84276 | 6.72181 |
2 | 6.83700 | 6.72428 |
3 | 6.83309 | 6.72469 |
4 | 6.82815 | 6.72654 |
5 | 6.83330 | 6.72613 |
6 | 6.83844 | 6.72572 |
7 | 6.83371 | 6.72510 |
8 | 6.83885 | 6.72325 |
9 | 6.83679 | 6.72634 |
10 | 6.83967 | 6.72757 |
AVG   | 6.83618 | 6.72514 |
STD   | 0.00396 | 0.00162 |
Range | 0.01460 | 0.00576 |

## Summary

**Low limit engage range    = 0.00761 [mm]**

**Low limit disengage range = 0.01275 [mm]**

**High limit engage range    = 0.01460 [mm]**

**High limit disengage range = 0.00576 [mm]**

**Total  travel range (engage to engage) = 8.74956 [mm]**


# Resolver Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/z_axis.log |
Resolver position source | TARGET_DU:ec0-s12-EL7201-PosAct |
Resolver gain | -0.0018487348 |
Resolver offset | 5.7407950591 |
Target position source | TARGET_DU:Z-PosCmd |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Resolver reading over one turn
Measured at 8 positions offset by 45deg resolver shaft angle.
The distrubution values are based on 10 values at each location.

Test | Setpoint [mm] | Resolver AVG[mm] | Diff [mm] | Resolver STD[mm]
--- | --- | --- | --- | --- |
1 | 5.74080 | 0.0000000 | 0.0000000 | 0.0000000
2 | 5.74080 | 0.0000000 | 0.0000000 | 0.0000000
3 | 5.74080 | 0.0000000 | 0.0000000 | 0.0000000
4 | 5.74080 | 0.0000000 | 0.0000000 | 0.0000000
5 | 5.74080 | 0.0000000 | 0.0000000 | 0.0000000
6 | 5.74080 | 0.0000000 | 0.0000000 | 0.0000000
7 | 5.74080 | 0.0000000 | 0.0000000 | 0.0000000
8 | 5.74080 | 0.0000000 | 0.0000000 | 0.0000000

**Resolver accuracy: 0.0000000 [mm]**

