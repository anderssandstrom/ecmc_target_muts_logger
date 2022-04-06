# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/b02/x/x.log
* Date        : Wed Apr  6 14:51:47 CEST 2022
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
1|-0.01852|-0.01934|-0.02138|-0.02015|-0.02261|-0.0204|
2|0.03258|0.03217|0.02685|0.02398|0.02275|0.02767|
3|0.07344|0.07139|0.07098|0.06771|0.06771|0.07025|
4|0.02913|0.02749|0.02708|0.02667|0.02667|0.02741|
5|-0.00944|-0.01518|-0.01886|-0.025|-0.02664|-0.01903|
6|-0.00871|-0.01281|-0.01526|-0.01526|-0.01813|-0.01404|
7|0.00144|-0.00061|-0.00225|-0.00757|-0.00962|-0.00372|
8|0.00667|0.00586|0.00463|0.00626|0.00667|0.00602|
9|0.04016|0.04057|0.03853|0.04016|0.04057|0.04|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.04923|-0.0525|-0.05127|-0.05004|-0.05086|-0.05078|
2|0.0031|0.00105|0.00023|-0.00018|-0.00141|0.00056|
3|0.04805|0.04887|0.04519|0.04191|0.04314|0.04543|
4|0.01316|0.01316|0.01071|0.01071|0.00948|0.01144|
5|-0.04712|-0.0508|-0.05367|-0.05489|-0.05653|-0.0526|
6|-0.02755|-0.03164|-0.03328|-0.03369|-0.03492|-0.03222|
7|-0.02682|-0.02927|-0.03541|-0.03582|-0.03828|-0.03312|
8|-0.01871|-0.01871|-0.01994|-0.01994|-0.02076|-0.01961|
9|0.01519|0.01601|0.01682|0.01764|0.01805|0.01674|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|-0.03559|0.03038|
2|0.01411|0.02711|
3|0.05784|0.02481|
4|0.01943|0.01597|
5|-0.03581|0.03358|
6|-0.02313|0.01818|
7|-0.01842|0.0294|
8|-0.0068|0.02563|
9|0.02837|0.02326|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.02537 [mm]

**B = Axis reversal error [mm]**

**B = 0.03358 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.00163|0.00124|0.00651|0.00497|0.03612|
2|0.00455|0.00167|0.0182|0.00669|0.03955|
3|0.0025|0.00302|0.00999|0.01207|0.03584|
4|0.00102|0.00165|0.00408|0.00659|0.0213|
5|0.00708|0.00371|0.02831|0.01486|0.05516|
6|0.00352|0.00286|0.01409|0.01144|0.03095|
7|0.00469|0.00484|0.01877|0.01937|0.04847|
8|0.00085|0.00089|0.0034|0.00355|0.02911|
9|0.00085|0.00117|0.0034|0.00469|0.0273|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.02831 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.01937 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.02831 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.09065 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.09803 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.09065 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.09365 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.10842 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.1115 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.13527 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/b02/x/x.log |
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
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/b02/x/x.log |
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

