# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/b02/z/z.log
* Date        : Wed Apr 13 14:00:34 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | 0 | .08387 | 50.00000 | .00000769
Target Position | Reference | -.99886 | 28.68214 | 50.00000 | .00673788

# ISO 230-2 motion test

## Configuration

Setting | Value
--- | --- |
Data file | sys.stdin
Reference position source | IOC_TEST:ILD_DownSample
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
1|-15.0|-15.0001|-15.0005|-15.00091|-15.0005|-15.00132|
2|-10.0|-10.01225|-10.01185|-10.01225|-10.01225|-10.00859|
3|-5.0|-4.97795|-4.97877|-4.97877|-4.97836|-4.97877|
4|0.0|0.00296|0.00255|0.00255|0.00215|0.00215|
5|5.0|4.99325|4.99284|4.99243|4.99121|4.99121|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-15.0|-15.00132|-15.00173|-15.00213|-15.00213|-15.00254|
2|-10.0|-10.01388|-10.01348|-10.01348|-10.01429|-10.01388|
3|-5.0|-4.97999|-4.97958|-4.97999|-4.9804|-4.97999|
4|0.0|0.00174|0.00133|0.00133|0.00092|0.00011|
5|5.0|4.99162|4.99121|4.9908|4.98999|4.98958|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.0001|-0.0005|-0.00091|-0.0005|-0.00132|-0.00067|
2|-0.01225|-0.01185|-0.01225|-0.01225|-0.00859|-0.01144|
3|0.02205|0.02123|0.02123|0.02164|0.02123|0.02148|
4|0.00296|0.00255|0.00255|0.00215|0.00215|0.00247|
5|-0.00675|-0.00716|-0.00757|-0.00879|-0.00879|-0.00781|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-0.00132|-0.00173|-0.00213|-0.00213|-0.00254|-0.00197|
2|-0.01388|-0.01348|-0.01348|-0.01429|-0.01388|-0.0138|
3|0.02001|0.02042|0.02001|0.0196|0.02001|0.02001|
4|0.00174|0.00133|0.00133|0.00092|0.00011|0.00109|
5|-0.00838|-0.00879|-0.0092|-0.01001|-0.01042|-0.00936|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|-0.00132|0.0013|
2|-0.01262|0.00236|
3|0.02074|0.00147|
4|0.00178|0.00139|
5|-0.00859|0.00155|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.00161 [mm]

**B = Axis reversal error [mm]**

**B = 0.00236 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.00046|0.00046|0.00186|0.00186|0.00316|
2|0.0016|0.00034|0.00642|0.00136|0.00642|
3|0.00036|0.00029|0.00146|0.00115|0.00277|
4|0.00034|0.00062|0.00136|0.00247|0.0033|
5|0.00094|0.00085|0.00375|0.00338|0.00512|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.00642 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.00338 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.00642 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.03292 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.03381 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.03292 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.03336 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.03685 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.03507 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.03685 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/b02/z/z.log |
Reference position source | IOC_TEST:ILD_DownSample |
Reference gear ratio | -0.9988645126 |
Reference offset | 28.6821436727 |
Low Limit source | TARGET_DU:Z-LimitMin |
High Limit source | TARGET_DU:Z-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 28.68214 | -15.15903 |
2 | -15.35832 | -15.15903 |
3 | -15.35995 | -15.16270 |
4 | 28.68214 | -15.16066 |
5 | 28.68214 | 27.68328 |
6 | -15.34609 | 27.68328 |
7 | -15.34609 | -15.16882 |
8 | -15.35751 | -15.16107 |
9 | 28.68214 | -15.16026 |
10 | 28.68214 | -15.15944 |
AVG   | 6.66428 | -6.59245 |
STD   | 22.01787 | 17.13786 |
Range | 44.04209 | 42.85209 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 7.48045 | 7.37326 |
2 | 7.47759 | 7.37286 |
3 | 7.47800 | 7.37571 |
4 | 7.47800 | 7.37489 |
5 | 7.47841 | 7.37530 |
6 | 7.47841 | 7.37815 |
7 | 7.47841 | 7.37449 |
8 | 7.47882 | 7.37815 |
9 | 7.47922 | 7.37815 |
10 | 7.47922 | 7.37775 |
AVG   | 7.47865 | 7.37587 |
STD   | 0.00078 | 0.00196 |
Range | 0.00285 | 0.00530 |

## Summary

**Low limit engage range    = 44.04209 [mm]**

**Low limit disengage range = 42.85209 [mm]**

**High limit engage range    = 0.00285 [mm]**

**High limit disengage range = 0.00530 [mm]**

**Total  travel range (engage to engage) = 0.81437 [mm]**


# Resolver Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/b02/z/z.log |
Resolver position source | TARGET_DU:ec0-s12-EL7201-PosAct |
Resolver gain | -0.0000000109 |
Resolver offset | 0.0838703030 |
Target position source | TARGET_DU:Z-PosCmd |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Resolver reading over one turn
Measured at 8 positions offset by 45deg resolver shaft angle.
The distrubution values are based on 10 values at each location.

Test | Setpoint [mm] | Resolver AVG[mm] | Diff [mm] | Resolver STD[mm]
--- | --- | --- | --- | --- |
1 | 0.99997 | 0.9960250 | -0.0039481 | 0.0000030
2 | 1.00141 | 0.9974210 | -0.0039921 | 0.0000022
3 | 1.00285 | 0.9988310 | -0.0040221 | 0.0000019
4 | 1.00429 | 1.0002600 | -0.0040331 | 0.0000014
5 | 1.00573 | 1.0016800 | -0.0040531 | 0.0000009
6 | 1.00717 | 1.0031100 | -0.0040631 | 0.0000007
7 | 1.00861 | 1.0045400 | -0.0040731 | 0.0000006
8 | 1.01005 | 1.0059800 | -0.0040731 | 0.0000003

**Resolver accuracy: 0.0040731 [mm]**

