# 6 - One line sequences

Transforming the transdecoder output amino acids sequences in one line

```
for file in trim_named_*.Trinity.fasta.transdecoder.pep.cdhit; do awk '/^>/ {printf("\n%s\n",$0);next; } { printf("%s",$0);}  END {printf("\n");}' < $file > ${file%%.Trinity.fasta.transdecoder.pep.cdhit}.oneline.fasta.pep.cdhit; done

```