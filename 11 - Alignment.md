# 11 - Alignment


Alignment with MAFFT

```
for i in *.fas; do mafft --maxiterate 1000 --globalpair $i > ${i%%.fas}_aln.fas; done

```

Trim alignments with Trimal

```
for file in *_aln.fasta; do trimal -in $file -out ${file%%.fasta}_trim.fasta -htmlout ${file%%.fasta}_trim.html -automated1; done

```

Refining alignment with a python script named parseGapsInFasta.py 

- clean signifficant initial and final gaps 
- Add "X" in the remaining initial and final gaps

```
for i in *.fasta; do python3.9 parseGapsInFasta.py -e -f $i -m X -t 0.25 > ${i%%_aln_trim.fasta}_x_trim_final.fasta; done

```
