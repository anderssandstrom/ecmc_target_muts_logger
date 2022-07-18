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


## filter opto
cat data_08.log | head -n 130000 | grep Opto | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.1 && $4>old-0.1){print $0;} old=$4;}' | awk '{if($4<20.25){print $0;}}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 

## filter vertical
 cat data_08.log | head -n 130000 | grep AI04 | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | awk '{if($4<10.755){print $0;}}' | awk 'BEGIN{f=1;}{if(f){f=0;old=$4;} if($4<old+0.015 && $4>old-0.015){print $0;} old=$4;}' | python ~/sources/ecmccomgui/pyDataManip/plotCaMonitor.py 

