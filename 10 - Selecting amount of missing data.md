# 10 - Selecting amount of missing data

To select the amount of missing data we used a simple command line to pick the gene names containing the threshold we choose.

```
for i in *; do awk 'NR == (amount of samples x2) {print FILENAME}' $i; done
```

If you have around 60 samples in total and want to use only the genes that contain 75% of the samples or more (60 x 0.75 = 45 samples at least). The command would be:

```

for i in *; do awk 'NR == (90) {print FILENAME}' $i; done

```

With the genes ID available in a list you can select them to align.
