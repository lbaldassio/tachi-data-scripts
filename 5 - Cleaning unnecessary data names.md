# 5 - Cleaning unnecessary data names

Create a file with the following code:

```
{
        if ($1 ~ /TRINITY_/) {
                print $1
        } else { 
                print $0
        }
}
```

Use the code with the awk command and change the name as needed

```
for i in named_*; do awk -f trim_pep.txt $i >> trim_$i; done
for i in named_*; do awk -f trim_trinity.txt $i >> trim_$i; done
```
