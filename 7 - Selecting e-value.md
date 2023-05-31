# 7 - Selecting e-value

Using the hmmer output file from BUSCO to select the best e-values 
We used e-values = 0 or e-values < e^-100

```
for i in *.out; do awk '(NR == 4 && ($7 ~ "[0-9].[0-9]e-[0-9]{3}")) || (NR == 4 && ($7 ~ "[0-9]e-[0-9]{3}")) || (NR == 4 && ($7 == 0)) {print "908",$1,$4,$7}' $i >> evalue_hmmer.txt; done

```

This is the only command we did for each sample. We did not have the time to automate