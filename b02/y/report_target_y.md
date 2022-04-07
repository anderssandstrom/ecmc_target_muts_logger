# ecmc motion system test report

* Data file   : /home/anderssandstrom/source/ecmc_target_muts_logger/b02/y/y.log
* Date        : Thu Apr  7 09:50:57 CEST 2022
* Author      : anderssandstrom


# Gear Ratios
From | To | Ratio [] | Offset [mm] | Data count [] | Residual error [mm²]
--- | --- | --- | --- | --- | --- |
Target Position | Resolver | 0 | .30446 | 90.00000 | .18099428
Target Position | Reference | .99733 | -49.39677 | 90.00000 | .05281945

# ISO 230-2 motion test

## Configuration

Setting | Value
--- | --- |
Data file | sys.stdin
Reference position source | IOC_TEST:ILD_DownSample
Target position source | TARGET_DU:Y-PosCmd
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
1|-20.0|-19.98677|-19.99206|-19.99572|-19.99735|-19.99938|
2|-15.0|-14.96913|-14.97361|-14.97686|-14.98012|-14.98256|
3|-10.0|-9.99503|-10.00114|-10.00602|-10.00846|-10.01131|
4|-5.0|-4.98228|-4.98798|-4.9892|-4.99327|-4.99652|
5|0.0|0.00362|-0.00208|-0.00615|-0.009|-0.00818|
6|5.0|4.98422|4.97609|4.97039|4.96713|4.96347|
7|10.0|10.01529|10.01366|10.00796|10.00715|10.00593|
8|15.0|15.06344|15.06466|15.06019|15.05653|15.05897|
9|20.0|19.98708|19.98423|19.98464|19.98301|19.97976|

### Data backward direction

i = Position index []

j = Cycle index []

tgt_pos(i) = Target position at position i [mm]

ref_pos(i,j) = Reference position at position i and cycle j [mm]

i |tgt_pos(i) [mm]|ref_pos(i,1) [mm]|ref_pos(i,2) [mm]|ref_pos(i,3) [mm]|ref_pos(i,4) [mm]|ref_pos(i,5) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|-20.0|-19.9945|-19.99735|-20.00996|-20.00467|-20.00793|
2|-15.0|-14.98012|-14.98419|-14.9907|-14.99192|-14.99477|
3|-10.0|-10.00724|-10.01457|-10.01986|-10.02555|-10.02555|
4|-5.0|-4.99123|-4.99937|-5.00466|-5.00832|-5.01036|
5|0.0|-0.0033|-0.009|-0.01429|-0.01714|-0.01795|
6|5.0|4.97487|4.9651|4.95859|4.95371|4.95126|
7|10.0|9.99169|9.98803|9.9925|9.98925|9.98843|
8|15.0|15.0435|15.04228|15.04066|15.03699|15.04025|
9|20.0|19.98098|19.97732|19.97488|19.97447|19.97243|


## ISO230-2 calculations:

### Positioning deviation and reversal error

#### Positioning deviation forward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.01323|0.00794|0.00428|0.00265|0.00062|0.00575|
2|0.03087|0.02639|0.02314|0.01988|0.01744|0.02355|
3|0.00497|-0.00114|-0.00602|-0.00846|-0.01131|-0.00439|
4|0.01772|0.01202|0.0108|0.00673|0.00348|0.01015|
5|0.00362|-0.00208|-0.00615|-0.009|-0.00818|-0.00436|
6|-0.01578|-0.02391|-0.02961|-0.03287|-0.03653|-0.02774|
7|0.01529|0.01366|0.00796|0.00715|0.00593|0.01|
8|0.06344|0.06466|0.06019|0.05653|0.05897|0.06076|
9|-0.01292|-0.01577|-0.01536|-0.01699|-0.02024|-0.01625|

#### Positioning deviation backward direction (unidirectional)

x(i,j)   = Position deviation at position i, cycle j (reference position - target position) [mm]

x_avg(i) = Mean unidirectional positioning deviation at a position [mm]

i |x(i,1) [mm]|x(i,2) [mm]|x(i,3) [mm]|x(i,4) [mm]|x(i,5) [mm]|x_avg(i) [mm]|
--- |--- |--- |--- |--- |--- |--- |
1|0.0055|0.00265|-0.00996|-0.00467|-0.00793|-0.00288|
2|0.01988|0.01581|0.0093|0.00808|0.00523|0.01166|
3|-0.00724|-0.01457|-0.01986|-0.02555|-0.02555|-0.01855|
4|0.00877|0.00063|-0.00466|-0.00832|-0.01036|-0.00279|
5|-0.0033|-0.009|-0.01429|-0.01714|-0.01795|-0.01233|
6|-0.02513|-0.0349|-0.04141|-0.04629|-0.04874|-0.0393|
7|-0.00831|-0.01197|-0.0075|-0.01075|-0.01157|-0.01002|
8|0.0435|0.04228|0.04066|0.03699|0.04025|0.04074|
9|-0.01902|-0.02268|-0.02512|-0.02553|-0.02757|-0.02399|

#### Positioning deviation bi-directional

x_avg(i) = Mean bi-directional positioning deviation at a position [mm]

B(i)     = Reversal error at a position [mm]

i |x_avg(i) [mm]|B(i) [mm]|
--- |--- |--- |
1|0.00143|0.00863|
2|0.0176|0.01188|
3|-0.01147|0.01416|
4|0.00368|0.01294|
5|-0.00835|0.00798|
6|-0.03352|0.01156|
7|-1e-05|0.02002|
8|0.05075|0.02002|
9|-0.02012|0.00773|

B_avg = Axis avg. reversal error [mm]

B_avg = 0.01277 [mm]

**B = Axis reversal error [mm]**

**B = 0.02002 [mm]**

### Repeatability

S_fwd(i) = Forward estimator for unidirectional axis positiong repeatability at a position [mm]

S_bwd(i) = Backward estimator for unidirectional axis positiong repeatability at a position [mm]

R_fwd(i) = Forward unidirectional positioning repeatability at a position [mm]

R_bwd(i) = Backward unidirectional positioning repeatability at a position [mm]

R(i) = Bi-directional position repeatability at a position [mm]

i |S_fwd(i) [mm]|S_bwd(i) [mm]|R_fwd(i) [mm]|R_bwd(i) [mm]|R(i) [mm]|
--- |--- |--- |--- |--- |--- |
1|0.00497|0.0067|0.01989|0.02681|0.03198|
2|0.00531|0.00601|0.02122|0.02404|0.03451|
3|0.00643|0.0078|0.02571|0.03121|0.04262|
4|0.00542|0.00769|0.02167|0.03077|0.03916|
5|0.0052|0.00615|0.0208|0.02459|0.03067|
6|0.00814|0.00952|0.03254|0.03807|0.04687|
7|0.00419|0.002|0.01676|0.00801|0.0324|
8|0.00331|0.00247|0.01325|0.00986|0.03158|
9|0.00267|0.00327|0.0107|0.01309|0.01963|

R_fwd = Forward unidirectional positioning repeatability of an axis (max(R_fwd(i))) [mm]

R_fwd = 0.03254 [mm]

R_bwd = Backward unidirectional positioning repeatability of an axis (max(R_bwd(i))) [mm]

R_bwd = 0.03807 [mm]

**R = Bi-directional positioning repeatability of an axis (max(R_fwd,R_bwd)) [mm]**

**R = 0.03807 [mm]**

### Positioning Error

E_fwd = Forward unidirectional system positioning error of an axis [mm]

E_fwd = 0.0885 [mm]

E_bwd = Backward unidirectional system positioning error of an axis [mm]

E_bwd = 0.08003 [mm]

**E = Bi-directional system positioning error of an axis [mm]**

**E = 0.0885 [mm]**

**M = Mean bi-directional system positioning error of an axis [mm]**

**M = 0.08426 [mm]**

### Accuracy

A_fwd = Forward unidirectional accuracy of an axis [mm]

A_fwd = 0.1114 [mm]

A_bwd = Backward unidirectional accuracy of an axis [mm]

A_bwd = 0.104 [mm]

**A = Bi-directional accuracy of an axis [mm]**

**A = 0.12572 [mm]** 

# Limit Switch Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/b02/y/y.log |
Reference position source | IOC_TEST:ILD_DownSample |
Reference gear ratio | 0.9973342107 |
Reference offset | -49.3967719749 |
Low Limit source | TARGET_DU:Y-LimitMin |
High Limit source | TARGET_DU:Y-LimitMax |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Low Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | -20.83436 | -20.58940 |
2 | -20.82012 | -20.60120 |
3 | -20.80832 | -20.61463 |
4 | -20.79571 | -20.63416 |
5 | -20.81687 | -20.61260 |
6 | -20.80303 | -20.62969 |
7 | -20.82094 | -20.60120 |
8 | -20.80873 | -20.61056 |
9 | -20.79652 | -20.63050 |
10 | -20.81646 | -20.60934 |
AVG   | -20.81210 | -20.61330 |
STD   | 0.01140 | 0.01374 |
Range | 0.03866 | 0.04476 |

## High Limit

Test | Engage [mm] | Disengage [mm] |
--- | --- | --- |
1 | 21.01128 | 20.74313 |
2 | 20.98971 | 20.75493 |
3 | 21.01576 | 20.73214 |
4 | 21.00152 | 20.74842 |
5 | 21.02430 | 20.72441 |
6 | 21.07964 | 20.75655 |
7 | 21.01454 | 20.73255 |
8 | 20.99867 | 20.74882 |
9 | 21.02471 | 20.72644 |
10 | 21.08127 | 20.75737 |
AVG   | 21.02410 | 20.74250 |
STD   | 0.03003 | 0.01200 |
Range | 0.09156 | 0.03296 |

## Summary

**Low limit engage range    = 0.03866 [mm]**

**Low limit disengage range = 0.04476 [mm]**

**High limit engage range    = 0.09156 [mm]**

**High limit disengage range = 0.03296 [mm]**

**Total  travel range (engage to engage) = 41.83620 [mm]**


# Resolver Performance

## Configuration

Setting | Value |
--- | --- |
Data file | /home/anderssandstrom/source/ecmc_target_muts_logger/b02/y/y.log |
Resolver position source | TARGET_DU:ec0-s11-EL7201-PosAct |
Resolver gain | 0.0000003246 |
Resolver offset | 0.3044650423 |
Target position source | TARGET_DU:Y-PosCmd |
Test number source | IOC_TEST:TestNumber |
Unit | mm |

## Resolver reading over one turn
Measured at 8 positions offset by 45deg resolver shaft angle.
The distrubution values are based on 10 values at each location.

Test | Setpoint [mm] | Resolver AVG[mm] | Diff [mm] | Resolver STD[mm]
--- | --- | --- | --- | --- |
1 | 1.00086 | 0.9852210 | -0.0156363 | 0.0000014
2 | 1.04286 | 0.9867050 | -0.0561523 | 0.0000048
3 | 1.08486 | 1.1373900 | 0.0525327 | 0.0000599
4 | 1.12686 | 1.1541300 | 0.0272727 | 0.0000040
5 | 1.16886 | 1.1554800 | -0.0133773 | 0.0000074
6 | 1.21086 | 1.1569900 | -0.0538673 | 0.0000051
7 | 1.25286 | 1.2803700 | 0.0275127 | 0.0001282
8 | 1.29486 | 1.3240500 | 0.0291927 | 0.0000105

**Resolver accuracy: 0.0561523 [mm]**

