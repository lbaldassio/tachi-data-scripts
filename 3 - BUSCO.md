# 3 - BUSCO

Finding orthologs with BUSCO

```
for i in *file.cdhit; do busco -i $i -o ${i%%.Trinity.fasta.transdecoder.pep.cdhit}.pep.cdhit.busco -l diptera_odb10 --config config.ini -m prot -c 10; done

```
