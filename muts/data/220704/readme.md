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

## filter vertical
 cat data_08.log | head -n 130000 | grep AI04 | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | awk '{if($4<10.755){print $0;}}' | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 
IOC_TEST:m0s002-AI04[19235] 10.3585..10.7517, mean: 10.56677079282558, std: 0.11722817302880705

##  Horizontal
cat data_08.log | head -n 130000 | grep AI | grep -v AI04 |  python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 

IOC_TEST:m0s002-AI01[25792] 8.76428..10.6593, mean: 9.76199968090881, std: 0.6331885970609957
IOC_TEST:m0s002-AI02[25809] 9.56334..11.766, mean: 10.666480993839357, std: 0.7194765746056431
IOC_TEST:m0s002-AI03[24604] 12.8569..14.6239, mean: 13.746221244513086, std: 0.5836709655889983

