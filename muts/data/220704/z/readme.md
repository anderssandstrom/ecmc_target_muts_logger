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
IOC_TEST:m0s002-AI02[45176] 9.8383..10.0769, mean: 9.877008837657163, std: 0.04980746719259242
IOC_TEST:m0s002-AI03[43211] 14.5397..14.762, mean: 14.722282731248988, std: 0.03414438893013366
IOC_TEST:m0s002-AI01[44368] 9.42219..9.49019, mean: 9.454987185809593, std: 0.007979215037009449

change 
AI01 0.23859999999999992
AI02 0.2223000000000006
AI03 0.06799999999999962
