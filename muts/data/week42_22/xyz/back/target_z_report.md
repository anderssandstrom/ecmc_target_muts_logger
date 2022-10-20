# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/z_axis.log
* Date        : Thu Oct 20 15:04:31 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | -.00184 | 5.74079 | 50.00000 | 344.84114970
Target Position | Reference | -.98446 | 30.81044 | 50.00000 | .68934562

# ISO 230-2 motion test

## Configuration

Setting | Value
--- | --- |
Data file | sys.stdin
Reference position source | IOC_TEST:m0s002-Enc01-PosAct
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
1|-1.5|-1.22479|-1.50435|-1.50595|-1.63288|-1.72968|
2|0.5|0.59915|0.59795|0.46098|0.42162|0.31678|
3|2.5|2.52351|2.63959|2.46326|2.4492|2.35842|
4|4.5|4.46593|4.67239|4.51293|4.42015|4.38841|
5|6.5|6.44291|6.62928|6.57666|6.42202|6.36739|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-1.5|-1.4445|-1.26134|-1.51439|-1.51599|-1.63729|
2|0.5|0.52565|0.73571|0.52163|0.46138|0.39471|
3|2.5|2.49097|2.75325|2.55483|2.42269|2.40301|
4|4.5|4.46513|4.68604|4.58483|4.42497|4.3844|
5|6.5|6.44612|6.61522|6.57987|6.42523|6.36699|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.27521|-0.00435|-0.00595|-0.13288|-0.22968|-0.01953|
2|0.09915|0.09795|-0.03902|-0.07838|-0.18322|-0.02071|
3|0.02351|0.13959|-0.03674|-0.0508|-0.14158|-0.01321|
4|-0.03407|0.17239|0.01293|-0.07985|-0.11159|-0.00804|
5|-0.05709|0.12928|0.07666|-0.07798|-0.13261|-0.01235|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.0555|0.23866|-0.01439|-0.01599|-0.13729|0.0253|
2|0.02565|0.23571|0.02163|-0.03862|-0.10529|0.02782|
3|-0.00903|0.25325|0.05483|-0.07731|-0.09699|0.02495|
4|-0.03487|0.18604|0.08483|-0.07503|-0.1156|0.00907|
5|-0.05388|0.11522|0.07987|-0.07477|-0.13301|-0.01331|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|0.00288|-0.04483|
2|0.00356|-0.04852|
3|0.00587|-0.03816|
4|0.00052|-0.01711|
5|-0.01283|0.00096|

B_avg = Axis avg. reversal error [mm]

B_avg = -0.02953 [mm]

**B = Axis reversal error [mm]**

**B = 0.04852 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.18993|0.13798|0.75973|0.55191|0.75973|
2|0.12095|0.12786|0.4838|0.51146|0.54615|
3|0.10385|0.14098|0.4154|0.56391|0.56391|
4|0.1113|0.1241|0.4452|0.49641|0.49641|
5|0.1104|0.10601|0.44159|0.42404|0.44159|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.75973 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.56391 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.75973 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.01267 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.04113 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.04113 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.0187 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.75973 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.56391 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.75973 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/z_axis.log |
Reference position source | IOC_TEST:m0s002-Enc01-PosAct |
Reference gear ratio | -0.9844616851 |
Reference offset | 30.8104444231 |
Low Limit source | TARGET_DU:Z-LimitMin |
High Limit source | TARGET_DU:Z-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | -2.15222 | 30.81044 |
2 | -2.14298 | 30.81044 |
3 | -2.14339 | 30.81044 |
4 | -2.13696 | 30.81044 |
5 | -2.12853 | 30.81044 |
6 | -2.12089 | 30.81044 |
7 | -2.11286 | 30.81044 |
8 | -2.10563 | 30.81044 |
9 | -2.09720 | 30.81044 |
10 | -2.09157 | 30.81044 |
AVG   | -2.12322 | 30.81040 |
STD   | 0.01989 | 0.00000 |
Range | 0.06065 | 0.00000 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 6.62526 | 30.81044 |
2 | 6.63329 | 30.81044 |
3 | 6.62847 | 30.81044 |
4 | 6.62486 | 30.81044 |
5 | 6.62325 | 30.81044 |
6 | 6.62245 | 30.81044 |
7 | 6.61723 | 30.81044 |
8 | 6.61522 | 30.81044 |
9 | 6.60919 | 30.81044 |
10 | 6.60678 | 30.81044 |
AVG   | 6.62060 | 30.81040 |
STD   | 0.00797 | 0.00000 |
Range | 0.02651 | 0.00000 |

## Summary

**Low limit engage range    = 0.06065 [mm]**

**Low limit disengage range = 0.00000 [mm]**

**High limit engage range    = 0.02651 [mm]**

**High limit disengage range = 0.00000 [mm]**

**Total  travel range (engage to engage) = 8.74382 [mm]**


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

