# 8 - Cross information

Cross information between the tabble with the complete genes sequences (full_table_complete) and the genes with best evalues selected previously

```
for i in $(find . -name *_named.txt); do awk '{print $1 ".*" $4 ".*" $2}' $i >> ${i%%_named.txt}_grepfile.txt; done

for i in $(find . -name *_grepfile.txt); do grep -hof $i $(find . -name evalue_hmmer.txt) >> ${i%%_grepfile.txt}_final.txt; done

```