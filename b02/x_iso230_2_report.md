# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/b02/x.log
* Date        : Wed Apr  6 14:38:27 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | 0 | -1.35645 | 90.00000 | .00004770
Target Position | Reference | -1.00357 | 50.31931 | 90.00000 | .09780742

# ISO 230-2 motion test

## Configuration

Setting | Value
--- | --- |
Data file | sys.stdin
Reference position source | IOC_TEST:ILD_DownSample
Target position source | TARGET_DU:X-PosCmd
Test number source | IOC_TEST:TestNumber
Position count | 9 (i=1..9)
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
1|-20.0|-20.01852|-20.01934|-20.02138|-20.02015|-20.02261|
2|-15.0|-14.96742|-14.96783|-14.97315|-14.97602|-14.97725|
3|-10.0|-9.92656|-9.92861|-9.92902|-9.93229|-9.93229|
4|-5.0|-4.97087|-4.97251|-4.97292|-4.97333|-4.97333|
5|0.0|-0.00944|-0.01518|-0.01886|-0.025|-0.02664|
6|5.0|4.99129|4.98719|4.98474|4.98474|4.98187|
7|10.0|10.00144|9.99939|9.99775|9.99243|9.99038|
8|15.0|15.00667|15.00586|15.00463|15.00626|15.00667|
9|20.0|20.04016|20.04057|20.03853|20.04016|20.04057|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-20.0|-20.04923|-20.0525|-20.05127|-20.05004|-20.05086|
2|-15.0|-14.9969|-14.99895|-14.99977|-15.00018|-15.00141|
3|-10.0|-9.95195|-9.95113|-9.95481|-9.95809|-9.95686|
4|-5.0|-4.98684|-4.98684|-4.98929|-4.98929|-4.99052|
5|0.0|-0.04712|-0.0508|-0.05367|-0.05489|-0.05653|
6|5.0|4.97245|4.96836|4.96672|4.96631|4.96508|
7|10.0|9.97318|9.97073|9.96459|9.96418|9.96172|
8|15.0|14.98129|14.98129|14.98006|14.98006|14.97924|
9|20.0|20.01519|20.01601|20.01682|20.01764|20.01805|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.01852|-0.01934|-0.02138|-0.02015|-0.02261|-0.01133|
2|0.03258|0.03217|0.02685|0.02398|0.02275|0.01537|
3|0.07344|0.07139|0.07098|0.06771|0.06771|0.03903|
4|0.02913|0.02749|0.02708|0.02667|0.02667|0.01523|
5|-0.00944|-0.01518|-0.01886|-0.025|-0.02664|-0.01057|
6|-0.00871|-0.01281|-0.01526|-0.01526|-0.01813|-0.0078|
7|0.00144|-0.00061|-0.00225|-0.00757|-0.00962|-0.00207|
8|0.00667|0.00586|0.00463|0.00626|0.00667|0.00334|
9|0.04016|0.04057|0.03853|0.04016|0.04057|0.02222|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.04923|-0.0525|-0.05127|-0.05004|-0.05086|-0.02821|
2|0.0031|0.00105|0.00023|-0.00018|-0.00141|0.00031|
3|0.04805|0.04887|0.04519|0.04191|0.04314|0.02524|
4|0.01316|0.01316|0.01071|0.01071|0.00948|0.00636|
5|-0.04712|-0.0508|-0.05367|-0.05489|-0.05653|-0.02922|
6|-0.02755|-0.03164|-0.03328|-0.03369|-0.03492|-0.0179|
7|-0.02682|-0.02927|-0.03541|-0.03582|-0.03828|-0.0184|
8|-0.01871|-0.01871|-0.01994|-0.01994|-0.02076|-0.0109|
9|0.01519|0.01601|0.01682|0.01764|0.01805|0.0093|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|-0.01977|0.01688|
2|0.00784|0.01506|
3|0.03213|0.01379|
4|0.01079|0.00887|
5|-0.0199|0.01865|
6|-0.01285|0.0101|
7|-0.01023|0.01633|
8|-0.00378|0.01424|
9|0.01576|0.01292|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.01409 [mm]

**B = Axis reversal error [mm]**

**B = 0.01865 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.01027|0.02526|0.04107|0.10106|0.10106|
2|0.01448|0.0017|0.05792|0.00678|0.05792|
3|0.03499|0.02278|0.13998|0.0911|0.13998|
4|0.01366|0.00592|0.05464|0.02368|0.05464|
5|0.01181|0.0264|0.04724|0.1056|0.1056|
6|0.00781|0.01626|0.03125|0.06505|0.06505|
7|0.00504|0.01716|0.02017|0.06862|0.06862|
8|0.00311|0.00979|0.01244|0.03915|0.04003|
9|0.01989|0.0084|0.07958|0.03361|0.07958|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.13998 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.1056 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.13998 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.05036 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.05446 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.05036 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.05203 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.1432 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.15282 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.19104 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/b02/x.log |
Reference position source | IOC_TEST:ILD_DownSample |
Reference gear ratio | -1.0035779146 |
Reference offset | 50.3193131396 |
Low Limit source | TARGET_DU:X-LimitMin |
High Limit source | TARGET_DU:X-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | -20.99590 | -20.79158 |
2 | -20.99426 | -20.66014 |
3 | -20.98648 | -20.69413 |
4 | -20.99590 | -20.64827 |
5 | -20.99139 | -20.67857 |
6 | -20.99672 | -20.79240 |
7 | -20.99344 | -20.67283 |
8 | -20.98607 | -20.69781 |
9 | -20.99344 | -20.65523 |
10 | -20.99057 | -20.68839 |
AVG   | -20.99240 | -20.69790 |
STD   | 0.00358 | 0.04952 |
Range | 0.01065 | 0.14413 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 21.03269 | 20.85212 |
2 | 20.99789 | 20.88529 |
3 | 21.02123 | 20.86154 |
4 | 21.00649 | 20.87710 |
5 | 20.98929 | 20.88815 |
6 | 21.01345 | 20.86686 |
7 | 20.99666 | 20.88283 |
8 | 21.02123 | 20.85499 |
9 | 21.00772 | 20.87137 |
10 | 21.08429 | 20.79357 |
AVG   | 21.01710 | 20.86340 |
STD   | 0.02562 | 0.02610 |
Range | 0.09499 | 0.09459 |

## Summary

**Low limit engage range    = 0.01065 [mm]**

**Low limit disengage range = 0.14413 [mm]**

**High limit engage range    = 0.09499 [mm]**

**High limit disengage range = 0.09459 [mm]**

**Total  travel range (engage to engage) = 42.00950 [mm]**


# Resolver Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/b02/x.log |
Resolver position source | TARGET_DU:ec0-s10-EL7201-PosAct |
Resolver gain | 0.0000003245 |
Resolver offset | -1.3564538425 |
Target position source | TARGET_DU:X-PosCmd |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Resolver reading over one turn
Measured at 8 positions offset by 45deg resolver shaft angle.
The distrubution values are based on 10 values at each location.

Test | Setpoint [mm] | Resolver AVG[mm] | Diff [mm] | Resolver STD[mm]
--- | --- | --- | --- | --- |
1 | 1.00084 | 1.0003100 | -0.0005273 | 0.0000082
2 | 1.04284 | 1.0425000 | -0.0003373 | 0.0000055
3 | 1.08484 | 1.0845100 | -0.0003273 | 0.0000088
4 | 1.12684 | 1.1269200 | 0.0000827 | 0.0000042
5 | 1.16884 | 1.1687300 | -0.0001073 | 0.0000072
6 | 1.21084 | 1.2108800 | 0.0000427 | 0.0000038
7 | 1.25284 | 1.2523600 | -0.0004773 | 0.0000030
8 | 1.29484 | 1.2944900 | -0.0003473 | 0.0000044

**Resolver accuracy: 0.0005273 [mm]**

