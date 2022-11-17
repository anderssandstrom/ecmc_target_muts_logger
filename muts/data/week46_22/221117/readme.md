# 221117

## Started at 3rpm

## 10rpm
took spectras
peaks moving?! but 5Hz constant

## 12rpm
There could eb some log of at 122 rpm that is name 10rpm

## Started log of Torque, Temp and Velo

## 14 rpm
"120Hz" peaks moving to higher freq
probably not same peak as seen this band before at higher rpm:s

## 18 rpm
Tourque osc. alitlle more

## 20rpm
Tourque osc seems to go down above 19rpm
"Burring" Sound is there

## 23.33
 looks fine
 kristoffer needed to go while i was at lunch so stopped

## 23.33 after lunch phasing
started in pahsing mode instead.
everything just worked +-0.8mm!! Success!


cat vib_1khz_phasing_3.log | python ~/source/ecmccomgui/pyDataManip/plotCaMonitorFFT.py 
cat torqueAndVelo_*.log | grep Tor | python ~/source/ecmccomgui/pyDataManip/plotCaMonitor.py 
