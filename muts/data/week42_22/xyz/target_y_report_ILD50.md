# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/y_axis_ild50.log
* Date        : Fri Oct 21 14:02:02 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | .02599 | -8900.23190 | 50.00000 | 390.48472794
Target Position | Reference | .99714 | -24.98038 | 50.00000 | .01511638

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
1|-4.0|-3.97853|-3.99664|-4.0064|-4.01332|-4.01678|
2|-2.0|-1.96979|-1.98382|-1.99501|-2.00233|-2.00844|
3|0.0|0.02391|0.00723|-0.00091|-0.0064|-0.00945|
4|2.0|2.03245|2.02025|2.01008|2.00296|1.99828|
5|4.0|4.03266|4.01252|3.9995|3.99259|3.9873|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-4.0|-3.96775|-3.99684|-4.01271|-4.02044|-4.02674|
2|-2.0|-1.96694|-1.98891|-2.00335|-2.01413|-2.02206|
3|0.0|0.02086|-0.00192|-0.0123|-0.01738|-0.02186|
4|2.0|2.02676|2.00479|1.99238|1.98506|1.97997|
5|4.0|4.01191|3.99279|3.98181|3.9753|3.9698|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.02147|0.00336|-0.0064|-0.01332|-0.01678|-0.00233|
2|0.03021|0.01618|0.00499|-0.00233|-0.00844|0.00812|
3|0.02391|0.00723|-0.00091|-0.0064|-0.00945|0.00288|
4|0.03245|0.02025|0.01008|0.00296|-0.00172|0.0128|
5|0.03266|0.01252|-0.0005|-0.00741|-0.0127|0.00491|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.03225|0.00316|-0.01271|-0.02044|-0.02674|-0.0049|
2|0.03306|0.01109|-0.00335|-0.01413|-0.02206|0.00092|
3|0.02086|-0.00192|-0.0123|-0.01738|-0.02186|-0.00652|
4|0.02676|0.00479|-0.00762|-0.01494|-0.02003|-0.00221|
5|0.01191|-0.00721|-0.01819|-0.0247|-0.0302|-0.01368|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|-0.00362|0.00256|
2|0.00452|0.0072|
3|-0.00182|0.0094|
4|0.0053|0.01501|
5|-0.00438|0.01859|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.01055 [mm]

**B = Axis reversal error [mm]**

**B = 0.01859 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.01537|0.02358|0.06147|0.09433|0.09433|
2|0.01538|0.02185|0.06152|0.0874|0.0874|
3|0.01336|0.01701|0.05343|0.06804|0.07013|
4|0.01376|0.01869|0.05502|0.07475|0.0799|
5|0.01816|0.01667|0.07264|0.06668|0.08825|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.07264 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.09433 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.09433 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.01514 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.0146 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.01514 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.00968 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.07431 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.09668 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.09668 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/y_axis_ild50.log |
Reference position source | IOC_TEST:m0s002-Enc01-PosAct |
Reference gear ratio | 0.9971450350 |
Reference offset | -24.9803875145 |
Low Limit source | TARGET_DU:Y-LimitMin |
High Limit source | TARGET_DU:Y-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | -4.97121 | -4.88090 |
2 | -4.97345 | -4.88374 |
3 | -4.97426 | -4.90347 |
4 | -4.99257 | -4.88578 |
5 | -4.99257 | -4.90734 |
6 | -4.99298 | -4.89412 |
7 | -4.99216 | -4.89595 |
8 | -4.99216 | -4.89615 |
9 | -4.99237 | -4.89554 |
10 | -4.99216 | -4.89717 |
AVG   | -4.98659 | -4.89402 |
STD   | 0.00894 | 0.00796 |
Range | 0.02177 | 0.02644 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 5.31500 | 5.11260 |
2 | 5.31724 | 5.10711 |
3 | 5.31826 | 5.10304 |
4 | 5.30117 | 5.11911 |
5 | 5.30219 | 5.11647 |
6 | 5.30422 | 5.11443 |
7 | 5.30402 | 5.11199 |
8 | 5.30687 | 5.10874 |
9 | 5.30911 | 5.10589 |
10 | 5.31155 | 5.10325 |
AVG   | 5.30896 | 5.11026 |
STD   | 0.00597 | 0.00525 |
Range | 0.01709 | 0.01607 |

## Summary

**Low limit engage range    = 0.02177 [mm]**

**Low limit disengage range = 0.02644 [mm]**

**High limit engage range    = 0.01709 [mm]**

**High limit disengage range = 0.01607 [mm]**

**Total  travel range (engage to engage) = 10.29555 [mm]**


# Resolver Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/y_axis_ild50.log |
Resolver position source | TARGET_DU:Y-PosAct02 |
Resolver gain | 0.0259980111 |
Resolver offset | -8900.2319080164 |
Target position source | TARGET_DU:Y-PosCmd |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Resolver reading over one turn
Measured at 8 positions offset by 45deg resolver shaft angle.
The distrubution values are based on 10 values at each location.

Test | Setpoint [mm] | Resolver AVG[mm] | Diff [mm] | Resolver STD[mm]
--- | --- | --- | --- | --- |
1 | 1.00076 | 0.2001910 | -0.8005666 | 0.4349130
2 | 1.04276 | -879.5000000 | -880.5427576 | 2638.9000000
3 | 1.08476 | -879.4300000 | -880.5147576 | 2638.9200000
4 | 1.12676 | -879.5670000 | -880.6937576 | 2638.8600000
5 | 1.16876 | -879.5570000 | -880.7257576 | 2638.8600000
6 | 1.21076 | -879.4240000 | -880.6347576 | 2638.9000000
7 | 1.25276 | -879.2630000 | -880.5157576 | 2638.9400000
8 | 1.29476 | -879.2610000 | -880.5557576 | 2638.9300000

**Resolver accuracy: 880.7260000 [mm]**

