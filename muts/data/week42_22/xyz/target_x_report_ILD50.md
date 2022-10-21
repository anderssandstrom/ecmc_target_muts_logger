# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/x_axis_ild50.log
* Date        : Fri Oct 21 13:21:20 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | -.01256 | 167958.45829 | 50.00000 | 397.66311455
Target Position | Reference | -1.00003 | 28.75173 | 50.00000 | .07317916

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
1|-4.0|-4.06474|-3.97681|-3.95845|-4.01578|-4.02373|
2|-2.0|-2.02711|-1.96978|-1.94326|-2.00059|-2.00385|
3|0.0|-0.05068|0.01929|0.04765|-0.03191|-0.02457|
4|2.0|1.96471|2.05162|2.06141|1.96267|1.96756|
5|4.0|4.02437|4.03539|4.04314|3.95643|3.96623|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-4.0|-4.08187|-4.00945|-4.00394|-3.97375|-3.98416|
2|-2.0|-2.0471|-1.99202|-1.9708|-1.95448|-1.97386|
3|0.0|0.02664|-0.00213|0.0454|-0.04844|-0.02498|
4|2.0|2.03978|2.03937|2.0457|1.96042|2.05019|
5|4.0|3.99968|4.00886|3.94317|3.93971|3.95888|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.06474|0.02319|0.04155|-0.01578|-0.02373|-0.0079|
2|-0.02711|0.03022|0.05674|-0.00059|-0.00385|0.01108|
3|-0.05068|0.01929|0.04765|-0.03191|-0.02457|-0.00805|
4|-0.03529|0.05162|0.06141|-0.03733|-0.03244|0.00159|
5|0.02437|0.03539|0.04314|-0.04357|-0.03377|0.00511|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.08187|-0.00945|-0.00394|0.02625|0.01584|-0.01064|
2|-0.0471|0.00798|0.0292|0.04552|0.02614|0.01235|
3|0.02664|-0.00213|0.0454|-0.04844|-0.02498|-0.0007|
4|0.03978|0.03937|0.0457|-0.03958|0.05019|0.02709|
5|-0.00032|0.00886|-0.05683|-0.06029|-0.04112|-0.02994|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|-0.00927|0.00273|
2|0.01171|-0.00126|
3|-0.00437|-0.00734|
4|0.01434|-0.0255|
5|-0.01241|0.03505|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.00073 [mm]

**B = Axis reversal error [mm]**

**B = 0.03505 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.0417|0.04238|0.16679|0.1695|0.17088|
2|0.03267|0.0358|0.13067|0.14321|0.14321|
3|0.04034|0.03789|0.16137|0.15157|0.16381|
4|0.05028|0.03754|0.20113|0.15015|0.20114|
5|0.04067|0.03222|0.16266|0.12888|0.18082|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.20113 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.1695 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.20113 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.01913 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.05703 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.03514 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.02676 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.20113 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.19756 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.20114 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/x_axis_ild50.log |
Reference position source | IOC_TEST:m0s002-Enc01-PosAct |
Reference gear ratio | -1.0000375404 |
Reference offset | 28.7517335499 |
Low Limit source | TARGET_DU:X-LimitMin |
High Limit source | TARGET_DU:X-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | -5.66599 | -5.44934 |
2 | -5.67619 | -5.50442 |
3 | -5.72597 | -5.44893 |
4 | -5.62703 | -5.45158 |
5 | -5.63621 | -5.43077 |
6 | -5.72210 | -5.48790 |
7 | -5.71904 | -5.51340 |
8 | -5.73597 | -5.50972 |
9 | -5.67864 | -5.43771 |
10 | -5.65722 | -5.42445 |
AVG   | -5.68444 | -5.46582 |
STD   | 0.03715 | 0.03265 |
Range | 0.10894 | 0.08895 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 5.29677 | 5.17742 |
2 | 5.29840 | 5.06501 |
3 | 5.22455 | 5.09378 |
4 | 5.22495 | 5.09194 |
5 | 5.19925 | 5.09378 |
6 | 5.20027 | 5.06991 |
7 | 5.19089 | 5.08256 |
8 | 5.20455 | 5.06685 |
9 | 5.19517 | 5.16702 |
10 | 5.22149 | 5.10989 |
AVG   | 5.22563 | 5.10182 |
STD   | 0.03780 | 0.03772 |
Range | 0.10751 | 0.11241 |

## Summary

**Low limit engage range    = 0.10894 [mm]**

**Low limit disengage range = 0.08895 [mm]**

**High limit engage range    = 0.10751 [mm]**

**High limit disengage range = 0.11241 [mm]**

**Total  travel range (engage to engage) = 10.91007 [mm]**


# Resolver Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/muts/data/week42_22/xyz/x_axis_ild50.log |
Resolver position source | TARGET_DU:X-PosAct02 |
Resolver gain | -0.0125639003 |
Resolver offset | 167958.4582901187 |
Target position source | TARGET_DU:X-PosCmd |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Resolver reading over one turn
Measured at 8 positions offset by 45deg resolver shaft angle.
The distrubution values are based on 10 values at each location.

Test | Setpoint [mm] | Resolver AVG[mm] | Diff [mm] | Resolver STD[mm]
--- | --- | --- | --- | --- |
1 | 1.00082 | -0.0640561 | -1.0648735 | 0.1893980
2 | 1.04282 | 16790.8000000 | 16789.7571826 | 50372.5000000
3 | 1.08482 | 16790.8000000 | 16789.7151826 | 50372.5000000
4 | 1.12682 | 16790.8000000 | 16789.6731826 | 50372.4000000
5 | 1.16882 | 16790.7000000 | 16789.5311826 | 50372.5000000
6 | 1.21082 | 16790.7000000 | 16789.4891826 | 50372.5000000
7 | 1.25282 | 16790.9000000 | 16789.6471826 | 50372.4000000
8 | 1.29482 | 16790.8000000 | 16789.5051826 | 50372.4000000

**Resolver accuracy: 16789.8000000 [mm]**

