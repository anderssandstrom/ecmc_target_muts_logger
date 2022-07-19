# Z dismount


## ALL
Copy plotTargetMuts.py to ecmccomgui/pyDataManip first

cat data_11.log | tail -n 260000 | head -n 200000 | python ~/sources/ecmccomgui/pyDataManip/plotTargetMuts.py


## opto
cat data_11.log | tail -n 260000 | head -n 200000 | grep Opto |  python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
IOC_TEST:m0s008-ec0-s8-OptoILD2300_50mm-CH01-PosAct[42856] 10.3581..20.7592, mean: 14.189132210192271, std: 3.383572142446601
Lowering of 10.4011mm

## AI04
Out of range in bottom so useless

## AI01..AI03
cat data_11.log | tail -n 260000 | head -n 200000 | grep AI |  grep -v AI04 |  python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py






