# 4 - Selection of Orthologs

Before running the command line, it is necessary to rename every full_table file with the first 3 letters or numbers of the respective sample

> Step 1

This command will select every Complete gene in BUSCO within the full_table file and assemble a new table with them.

```
for i in $(find . -name *_full*); do grep Complete $i >> ${i%%.tsv}_complete.txt; done
```


> Step 2

Add the first 3 letters or numbers of the samples in each line of the complete genes

```
for i in $(find . -name *_complete.txt); do awk '{print substr(FILENAME,0,3),$0}' $i >> ${i%%.txt}_named.txt; done
```


> Step 3

Add the samples names in the transdecoder files(.pep):

Create file name_in_pep.sh with this code:
```
BEGIN {FS="\>"}
{
	if ($2 ~ /TRINITY_/) {
		print ">" substr(FILENAME,1,3) "_" $2
	} else { 
		print $0
	}
}
```

Create file name_in_trinity.sh with this code:
```
BEGIN {FS="\>"}
{
	if ($3 ~ GENE.c/) {
		print ">" substr(FILENAME,1,3) "_" $2
	} else { 
		print $0
	}
}
```

Run the command line:

```
for i in *.pep.cdhit; do awk -f name_in_pep.sh $i >> named_$i; done

for i in *.Trinity.fasta ; do awk -f name_in_trinity.sh $i >> named_$i; done

```
