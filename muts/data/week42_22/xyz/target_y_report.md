# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/y_axis.log
* Date        : Wed Oct 19 15:52:39 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | -.02175 | 93448635.32289 | 50.00000 | 391.07904748
Target Position | Reference | 1.00040 | -49.60006 | 50.00000 | .07296442

# ISO 230-2 motion test

## Configuration

Setting | Value
--- | --- |
Data file | sys.stdin
Reference position source | IOC_TEST:m0s002-Enc01-PosAct
Target position source | TARGET_DU:Y-PosCmd
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
1|-4.0|-3.96408|-3.9751|-3.98285|-4.00285|-4.01469|
2|-2.0|-1.93795|-1.95755|-1.96816|-1.98367|-2.00163|
3|0.0|0.0747|0.07511|0.0694|0.06042|0.05184|
4|2.0|2.04083|2.02287|2.00817|1.99756|1.98777|
5|4.0|4.03307|4.02409|4.01389|4.01226|4.00287|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-4.0|-3.94653|-3.98653|-4.0102|-4.02408|-4.04041|
2|-2.0|-2.03061|-2.05959|-2.05428|-2.05387|-2.06204|
3|0.0|-0.02285|-0.03591|-0.0404|-0.04652|-0.05101|
4|2.0|2.00287|1.97307|1.95552|1.9494|1.94613|
5|4.0|4.00409|3.99471|3.99022|3.98409|3.97838|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.03592|0.0249|0.01715|-0.00285|-0.01469|0.01208|
2|0.06205|0.04245|0.03184|0.01633|-0.00163|0.03021|
3|0.0747|0.07511|0.0694|0.06042|0.05184|0.06629|
4|0.04083|0.02287|0.00817|-0.00244|-0.01223|0.01144|
5|0.03307|0.02409|0.01389|0.01226|0.00287|0.01724|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.05347|0.01347|-0.0102|-0.02408|-0.04041|-0.00155|
2|-0.03061|-0.05959|-0.05428|-0.05387|-0.06204|-0.05208|
3|-0.02285|-0.03591|-0.0404|-0.04652|-0.05101|-0.03934|
4|0.00287|-0.02693|-0.04448|-0.0506|-0.05387|-0.0346|
5|0.00409|-0.00529|-0.00978|-0.01591|-0.02162|-0.0097|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|0.00527|0.01363|
2|-0.01093|0.08229|
3|0.01348|0.10563|
4|-0.01158|0.04604|
5|0.00377|0.02694|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.05491 [mm]

**B = Axis reversal error [mm]**

**B = 0.10563 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.0206|0.03656|0.08242|0.14622|0.14622|
2|0.02435|0.0125|0.09741|0.04998|0.15598|
3|0.01002|0.01087|0.04007|0.04348|0.14741|
4|0.02096|0.02339|0.08386|0.09354|0.13474|
5|0.01162|0.00988|0.04649|0.03951|0.06994|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.09741 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.14622 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.14622 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.05485 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.05053 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.05485 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.02506 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.11682 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.15294 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.1677 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/y_axis.log |
Reference position source | IOC_TEST:m0s002-Enc01-PosAct |
Reference gear ratio | 1.0004014232 |
Reference offset | -49.6000624665 |
Low Limit source | TARGET_DU:Y-LimitMin |
High Limit source | TARGET_DU:Y-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | -4.98775 | -49.60006 |
2 | -4.99592 | -49.60006 |
3 | -4.99755 | -49.60006 |
4 | -4.99837 | -49.60006 |
5 | -4.99673 | -49.60006 |
6 | -5.01918 | -49.60006 |
7 | -5.01551 | -49.60006 |
8 | -5.01428 | -49.60006 |
9 | -5.01224 | -49.60006 |
10 | -5.01061 | -49.60006 |
AVG   | -5.00481 | -49.60010 |
STD   | 0.01014 | nan |
Range | 0.03143 | 0.00000 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 5.31308 | 5.13226 |
2 | 5.31389 | 5.12859 |
3 | 5.31553 | 5.12491 |
4 | 5.31757 | 5.12246 |
5 | 5.31757 | 5.12206 |
6 | 5.31879 | 5.11757 |
7 | 5.31879 | 5.11716 |
8 | 5.31838 | 5.11552 |
9 | 5.31920 | 5.11267 |
10 | 5.31838 | 5.11063 |
AVG   | 5.31712 | 5.12038 |
STD   | 0.00207 | 0.00658 |
Range | 0.00612 | 0.02163 |

## Summary

**Low limit engage range    = 0.03143 [mm]**

**Low limit disengage range = 0.00000 [mm]**

**High limit engage range    = 0.00612 [mm]**

**High limit disengage range = 0.02163 [mm]**

**Total  travel range (engage to engage) = 10.32193 [mm]**


# Resolver Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/y_axis.log |
Resolver position source | TARGET_DU:Y-PosAct02 |
Resolver gain | -0.0217584204 |
Resolver offset | 93448635.3228929490 |
Target position source | TARGET_DU:Y-PosCmd |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Resolver reading over one turn
Measured at 8 positions offset by 45deg resolver shaft angle.
The distrubution values are based on 10 values at each location.

Test | Setpoint [mm] | Resolver AVG[mm] | Diff [mm] | Resolver STD[mm]
--- | --- | --- | --- | --- |
1 | 1.00076 | 0.0998869 | -0.9008707 | 0.4072950
2 | 1.04276 | 9344850.0000000 | 28034600.0000000 | 0.0000000
3 | 1.08476 | 9344850.0000000 | 28034600.0000000 | 0.0000000
4 | 1.12676 | 9344850.0000000 | 28034600.0000000 | 0.0000000
5 | 1.16876 | 9344850.0000000 | 28034600.0000000 | 0.0000000
6 | 1.21076 | 9344860.0000000 | 28034600.0000000 | 0.0000000
7 | 1.25276 | 9344850.0000000 | 28034600.0000000 | 0.0000000
8 | 1.29476 | 9344860.0000000 | 28034600.0000000 | 0.0000000

**Resolver accuracy: 0.0000000 [mm]**

