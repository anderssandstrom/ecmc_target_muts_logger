# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/x_axis_8A.log
* Date        : Thu Oct 20 13:35:13 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Reference | -.99036 | 73.37527 | 50.00000 | .07961867

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
1|-4.0|-3.99861|-3.98366|-3.98366|-3.95012|-3.95335|
2|-2.0|-2.00655|-1.98836|-1.98109|-1.9419|-1.93341|
3|0.0|-0.02782|-0.00802|-0.01005|0.01986|0.0344|
4|2.0|1.97474|1.99616|2.00181|2.03495|2.04909|
5|4.0|4.00316|4.00397|4.00963|4.03024|4.05165|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-4.0|-4.10205|-4.01598|-3.99861|-3.99254|-3.96143|
2|-2.0|-2.11969|-2.02392|-2.00251|-1.99968|-1.9617|
3|0.0|-0.13005|-0.02904|-0.01489|-0.01126|0.01622|
4|2.0|1.94767|1.97191|1.98848|2.00949|2.02323|
5|4.0|3.94983|3.98054|3.98538|4.01731|4.03024|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.00139|0.01634|0.01634|0.04988|0.04665|0.02612|
2|-0.00655|0.01164|0.01891|0.0581|0.06659|0.02974|
3|-0.02782|-0.00802|-0.01005|0.01986|0.0344|0.00167|
4|-0.02526|-0.00384|0.00181|0.03495|0.04909|0.01135|
5|0.00316|0.00397|0.00963|0.03024|0.05165|0.01973|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.10205|-0.01598|0.00139|0.00746|0.03857|-0.01412|
2|-0.11969|-0.02392|-0.00251|0.00032|0.0383|-0.0215|
3|-0.13005|-0.02904|-0.01489|-0.01126|0.01622|-0.0338|
4|-0.05233|-0.02809|-0.01152|0.00949|0.02323|-0.01185|
5|-0.05017|-0.01946|-0.01462|0.01731|0.03024|-0.00734|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|0.006|0.04025|
2|0.00412|0.05124|
3|-0.01607|0.03548|
4|-0.00025|0.02319|
5|0.00619|0.02707|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.03544 [mm]

**B = Axis reversal error [mm]**

**B = 0.05124 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.02115|0.05296|0.08458|0.21182|0.21182|
2|0.03132|0.05929|0.12529|0.23715|0.23715|
3|0.02502|0.05625|0.10007|0.22499|0.22499|
4|0.03018|0.02995|0.12072|0.11981|0.14346|
5|0.02094|0.03184|0.08377|0.12734|0.13263|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.12529 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.23715 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.23715 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.02806 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.02646 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.02806 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.02226 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.14139 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.24337 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.24337 [mm]** 

