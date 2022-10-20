# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/x_axis_2.log
* Date        : Thu Oct 20 09:08:23 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Reference | -.99801 | 66.14203 | 50.00000 | .14894148

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
1|-4.0|-4.01766|-3.98142|-3.96799|-3.94641|-3.99283|
2|-2.0|-1.99474|-2.05989|-1.94507|-1.92145|-1.99026|
3|0.0|-0.06873|-0.09357|0.02858|0.04528|-0.05652|
4|2.0|1.92202|1.91795|2.0287|2.05191|2.07024|
5|4.0|3.91766|4.01253|4.02679|4.05122|4.07158|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-4.0|-4.13982|-4.01034|-3.99568|-3.97939|-3.96066|
2|-2.0|-2.11161|-1.99189|-1.97968|-1.96095|-1.93814|
3|0.0|-0.07891|0.01108|0.01881|0.0294|0.04691|
4|2.0|1.89962|1.99287|2.00753|2.02219|2.04662|
5|4.0|3.89934|3.99258|4.00398|4.02556|4.04267|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.01766|0.01858|0.03201|0.05359|0.00717|0.01874|
2|0.00526|-0.05989|0.05493|0.07855|0.00974|0.01772|
3|-0.06873|-0.09357|0.02858|0.04528|-0.05652|-0.02899|
4|-0.07798|-0.08205|0.0287|0.05191|0.07024|-0.00184|
5|-0.08234|0.01253|0.02679|0.05122|0.07158|0.01595|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.13982|-0.01034|0.00432|0.02061|0.03934|-0.01718|
2|-0.11161|0.00811|0.02032|0.03905|0.06186|0.00355|
3|-0.07891|0.01108|0.01881|0.0294|0.04691|0.00546|
4|-0.10038|-0.00713|0.00753|0.02219|0.04662|-0.00623|
5|-0.10066|-0.00742|0.00398|0.02556|0.04267|-0.00717|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|0.00078|0.03591|
2|0.01063|0.01417|
3|-0.01177|-0.03445|
4|-0.00403|0.0044|
5|0.00439|0.02313|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.00863 [mm]

**B = Axis reversal error [mm]**

**B = 0.03591 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.02669|0.07102|0.10677|0.28406|0.28406|
2|0.05322|0.0675|0.21287|0.26999|0.26999|
3|0.06193|0.04904|0.2477|0.19616|0.25638|
4|0.07288|0.05625|0.29154|0.22498|0.29154|
5|0.05943|0.05572|0.23773|0.2229|0.25344|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.29154 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.28406 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.29154 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.04773 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.02263 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.03591 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.0224 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.29678 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.29775 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.30314 [mm]** 

