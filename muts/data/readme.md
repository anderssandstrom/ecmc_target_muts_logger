cat mech_lowering*.log |  awk '{print $1 " " $2 " " $3 " " $4}' | grep AI01 | awk 'BEGIN{i=0} {if(i==0){print $0}; i=i+1; if(i>10){i=0;} }' | tee down_sample_AI01.log
