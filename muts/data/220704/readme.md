# Tests

Test with AVS rotation box.

Same erros as in tdu cabonet (8022 encode signals incorerct)

Anders found wrong phases in input to box. Anders (actemuim changes phases)

Still problems

Then also found wrong phases in motor conentcion box on drive unit. Anders Changed to correct.

Then inverted encoder.

The suddely works.. Starnge.. must be rotation direction issue..Check with eider why phases was changed in both AVS box and motor conenction box.

Encoder noises at 17rpm-20rpm

check with Eider!


## Wrong direction
data_01.log started to late at 15rpm.. ramped up to 20
data_02.log started to late at Xrpm.. ramped up to 20 then to 23.3
data_03.log 23.3rpm
data_04.log rampdown

## Right direction
data_05.log rampup 23.3rpm
data_06.log constant velo 23.3rpm
data_07.log rampdown

## Right direction
data_08.log rampup
data_09.log const velo
data_10.log rampdown

## Z movement
Moved approx 11 mm before touched piedistal
data_11.log rampdown

# Rampup rotation

## filter opto
cat data_08.log | head -n 130000 | grep Opto | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.1 && $4>old-0.1){print $0;} old=$4;}' | awk '{if($4<20.25){print $0;}}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 

IOC_TEST:m0s008-ec0-s8-OptoILD2300_50mm-CH01-PosAct[12583] 18.9891..19.9869, mean: 19.45611324803306, std: 0.2885615581460372
+-0.49mm

## filter vertical AI04
cat data_08.log | head -n 130000 | grep AI04 | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | awk '{if($4<10.755){print $0;}}' | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 
IOC_TEST:m0s002-AI04[19235] 10.3585..10.7517, mean: 10.56677079282558, std: 0.11722817302880705

##  Horizontal AI01..AI03
cat data_08.log | head -n 130000 | grep AI | grep -v AI04 |  python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 

IOC_TEST:m0s002-AI01[25792] 8.76428..10.6593, mean: 9.76199968090881, std: 0.6331885970609957
IOC_TEST:m0s002-AI02[25809] 9.56334..11.766, mean: 10.666480993839357, std: 0.7194765746056431
IOC_TEST:m0s002-AI03[24604] 12.8569..14.6239, mean: 13.746221244513086, std: 0.5836709655889983


# Rampdown

## Opto
cat data_07.log |  grep Opto | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.1 && $4>old-0.1){print $0;} old=$4;}' | awk '{if($4<20.25){print $0;}}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 
IOC_TEST:m0s008-ec0-s8-OptoILD2300_50mm-CH01-PosAct[1240] 18.9951..20.2388, mean: 19.54435370967742, std: 0.3327594920763094, +-0.62

## vertical AI04
cat data_07.log | grep AI04 | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | awk '{if($4<10.755){print $0;}}' | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 
IOC_TEST:m0s002-AI04[1516] 10.3926..10.7543, mean: 10.607186411609499, std: 0.09374807867891954, +-0.18

## Horizontal AI01..AI03
cat data_07.log | grep AI | grep -v AI04 |  python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 
[<caPVArrayLib.caPVArray object at 0x7f09fe75a4a8>, <caPVArrayLib.caPVArray object at 0x7f09fe75aa58>, <caPVArrayLib.caPVArray object at 0x7f09dfcdb320>]
IOC_TEST:m0s002-AI01[1972] 8.78285..10.6497, mean: 9.626850801217039, std: 0.5530981601418496, +-0.93 
IOC_TEST:m0s002-AI02[1997] 9.58114..11.7387, mean: 10.96710332498748, std: 0.7451292957148845, +-1.08
IOC_TEST:m0s002-AI03[1894] 12.8673..14.6122, mean: 13.638638648363253, std: 0.5543754426947586, +-0.87

# Constant velo

## Opto
cat data_06.log |  grep Opto | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.1 && $4>old-0.1){print $0;} old=$4;}' | awk '{if($4<20.0){print $0;}}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 
IOC_TEST:m0s008-ec0-s8-OptoILD2300_50mm-CH01-PosAct[9915] 19.0224..19.9926, mean: 19.455101311144734, std: 0.29385577839393817, +-0.49

## vertical AI04
cat data_07.log | grep AI04 | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | awk '{if($4<10.755){print $0;}}' | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 
IOC_TEST:m0s002-AI04[18251] 10.3874..10.7543, mean: 10.574672154950413, std: 0.111347643861461, +-0.18

## Horizontal AI01..AI03
cat data_06.log | grep AI | grep -v AI04 |  python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py
[<caPVArrayLib.caPVArray object at 0x7f56c40a14a8>, <caPVArrayLib.caPVArray object at 0x7f56c40a1a58>, <caPVArrayLib.caPVArray object at 0x7f56a5622320>]
IOC_TEST:m0s002-AI01[26315] 8.75336..10.6661, mean: 9.742496319209575, std: 0.6550501318013986, +-0.96
IOC_TEST:m0s002-AI02[26352] 9.56618..11.7726, mean: 10.68764042615361, std: 0.7480920569069018, +-1.10
IOC_TEST:m0s002-AI03[25687] 12.8569..14.6309, mean: 13.753568225172266, std: 0.6067467117969889, +-0.89 





