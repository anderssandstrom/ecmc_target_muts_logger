

 1154  cat velo_01.log | tail -n 760 | head -n 465 | tee onlyDownRamp.log
 1158  cat onlyDownRamp.log | python ~/source/ecmccomgui/pyDataManip/deLin.py | python ~/source/ecmccomgui/pyDataManip/plotCaMonitor.py 
