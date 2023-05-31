# 9 - Assemble a file with command line

Assemble a script file to select all sequences matching the genes selected previously 
```

for i in $(find . -name *_final.txt); do awk '{print "grep -h -A1 " $1 ".*" $2, "*.oneline.fasta.pep.cdhit" " >> "$3".fas"}' $i >> assemble_fastas.sh; done
```

The next command move all fastas files to a particular directory named "fastas"

```
sh assemble_fastas.sh && mkdir fastas && mv *.fas fastas
```
