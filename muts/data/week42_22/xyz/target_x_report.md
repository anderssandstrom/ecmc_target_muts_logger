# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/x_axis.log
* Date        : Wed Oct 19 15:15:56 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | -.00946 | 126356.01813 | 50.00000 | 398.57990585
Target Position | Reference | -.99415 | 22.62545 | 50.00000 | .12450909

# ISO 230-2 motion test

## Configuration

Setting | Value
--- | --- |
Data file | sys.stdin
Reference position source | IOC_TEST:m0s002-Enc01-PosAct
Target position source | TARGET_DU:X-PosCmd
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
1|-4.0|-4.00937|-3.97732|-4.02681|-3.9323|-3.93352|
2|-2.0|-2.00562|-1.97195|-2.01495|-1.93099|-1.93301|
3|0.0|0.0107|0.03058|-0.04771|0.06627|0.06911|
4|2.0|1.91426|2.00958|1.94427|2.06109|2.05744|
5|4.0|3.97885|4.02347|3.96871|4.07944|4.06403|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-4.0|-4.07467|-4.02437|-3.99395|-4.05277|-3.94771|
2|-2.0|-2.06362|-2.01819|-1.99305|-2.04253|-1.96262|
3|0.0|-0.11788|0.00462|0.00624|-0.0323|-0.00512|
4|2.0|1.91142|1.98565|1.9175|1.95401|2.03878|
5|4.0|3.95938|3.99669|3.95857|4.05429|4.0474|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.00937|0.02268|-0.02681|0.0677|0.06648|0.02414|
2|-0.00562|0.02805|-0.01495|0.06901|0.06699|0.0287|
3|0.0107|0.03058|-0.04771|0.06627|0.06911|0.02579|
4|-0.08574|0.00958|-0.05573|0.06109|0.05744|-0.00267|
5|-0.02115|0.02347|-0.03129|0.07944|0.06403|0.0229|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.07467|-0.02437|0.00605|-0.05277|0.05229|-0.0187|
2|-0.06362|-0.01819|0.00695|-0.04253|0.03738|-0.016|
3|-0.11788|0.00462|0.00624|-0.0323|-0.00512|-0.02889|
4|-0.08858|-0.01435|-0.0825|-0.04599|0.03878|-0.03853|
5|-0.04062|-0.00331|-0.04143|0.05429|0.0474|0.00327|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|0.00272|0.04283|
2|0.00635|0.0447|
3|-0.00155|0.05468|
4|-0.0206|0.03586|
5|0.01308|0.01963|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.03954 [mm]

**B = Axis reversal error [mm]**

**B = 0.05468 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.04304|0.04994|0.17217|0.19977|0.22881|
2|0.03929|0.03985|0.15716|0.15941|0.20298|
3|0.04787|0.05209|0.1915|0.20835|0.2546|
4|0.06623|0.05257|0.26491|0.21029|0.27346|
5|0.04941|0.04615|0.19765|0.18459|0.21075|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.26491 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.21029 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.26491 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.03137 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.04179 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.03137 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.03368 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.26491 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.23923 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.27346 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/x_axis.log |
Reference position source | IOC_TEST:m0s002-Enc01-PosAct |
Reference gear ratio | -0.9941583041 |
Reference offset | 22.6254553711 |
Low Limit source | TARGET_DU:X-LimitMin |
High Limit source | TARGET_DU:X-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | -5.43754 | -5.25136 |
2 | -5.54949 | -5.34709 |
3 | -5.54828 | -5.36859 |
4 | -5.41077 | -5.24447 |
5 | -5.41239 | -5.24771 |
6 | -5.41767 | -5.25299 |
7 | -5.42700 | -5.25258 |
8 | -5.41929 | -5.24447 |
9 | -5.39901 | -5.22419 |
10 | -5.55842 | -5.31991 |
AVG   | -5.45798 | -5.27534 |
STD   | 0.06237 | 0.04765 |
Range | 0.15941 | 0.14440 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 5.34131 | 5.21476 |
2 | 5.36362 | 5.21638 |
3 | 5.37985 | 5.32874 |
4 | 5.45651 | 5.30521 |
5 | 5.43907 | 5.32184 |
6 | 5.44353 | 5.32387 |
7 | 5.44596 | 5.32387 |
8 | 5.37822 | 5.25248 |
9 | 5.35754 | 5.24113 |
10 | 5.36038 | 5.26181 |
AVG   | 5.39660 | 5.27901 |
STD   | 0.04199 | 0.04416 |
Range | 0.11520 | 0.11398 |

## Summary

**Low limit engage range    = 0.15941 [mm]**

**Low limit disengage range = 0.14440 [mm]**

**High limit engage range    = 0.11520 [mm]**

**High limit disengage range = 0.11398 [mm]**

**Total  travel range (engage to engage) = 10.85458 [mm]**


# Resolver Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/x_axis.log |
Resolver position source | TARGET_DU:X-PosAct02 |
Resolver gain | -0.0094672943 |
Resolver offset | 126356.0181324943 |
Target position source | TARGET_DU:X-PosCmd |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Resolver reading over one turn
Measured at 8 positions offset by 45deg resolver shaft angle.
The distrubution values are based on 10 values at each location.

Test | Setpoint [mm] | Resolver AVG[mm] | Diff [mm] | Resolver STD[mm]
--- | --- | --- | --- | --- |
1 | 1.00077 | -0.0839260 | -1.0846969 | 0.1423280
2 | 1.04277 | 12631.8000000 | 12630.7572291 | 37895.5000000
3 | 1.08477 | 12631.8000000 | 12630.7152291 | 37895.4000000
4 | 1.12677 | 12631.8000000 | 12630.6732291 | 37895.4000000
5 | 1.16877 | 12631.8000000 | 12630.6312291 | 37895.4000000
6 | 1.21077 | 12631.8000000 | 12630.5892291 | 37895.4000000
7 | 1.25277 | 12631.8000000 | 12630.5472291 | 37895.4000000
8 | 1.29477 | 12631.8000000 | 12630.5052291 | 37895.4000000

**Resolver accuracy: 12630.8000000 [mm]**

