Print 2nd col: 
```
awk '{print $2}'
```

Print 2nd line/row:
```
awk 'FNR == 2 {print}'
```

Print 3Col and 5Row:
```
awk 'FNR == 5 {print $3}'
```

Skip 1st line:
```
awk 'NR!=1' booklist.txt
or
awk '(NR>1)' booklist.txt
or
awk '{if (NR!=1) {print}}' booklist.txt
```
