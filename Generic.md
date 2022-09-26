Wait for userinput: 
```
read -p 'Enter 1 or 2' vara
echo $vara
```
Wait for specific length of user input:
```

```

Search and Replace a pattern in the file: 
Search "BLOCKED RESOURCE LIST:" in file and replace with "BEGIN"
```
cat abc.txt | sed 's/BLOCKED RESOURCE LIST:/BEGIN/g' | sed 's/ACTIVITY LIST:/END/g' 
```
Print the data between 2 markers/patterns 
```
cat abc.output | sed 's/BLOCKED RESOURCE LIST:/BEGIN/g' | sed 's/ACTIVITY LIST:/END/g' | awk '/BEGIN/,/END/'
```
