replace space with newline:
```
echo "$string" | tr '\n' ' '
```

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

Select menu:
```
PS3="Enter a number: "

select character in Sheldon Leonard Penny Howard RaJ
do
    echo "Selected character: $character"
    echo "Selected number: $REPLY"
done
```

Check if the output str contains substr
```
#!/bin/bash

STR='GNU/Linux is an operating system'
SUB='Linux'

if grep -q "$SUB" <<< "$STR"; then
  echo "It's there"
fi
```

Select and pass value in function:
```
calculate () {
  read -p "Enter the first number: " n1
  read -p "Enter the second number: " n2
  echo "$n1 $1 $n2 = " $(bc -l <<< "$n1$1$n2")
}

PS3="Select the operation: "

select opt in add subtract multiply divide quit; do

  case $opt in
    add)
      calculate "+";;
    subtract)
      calculate "-";;
    multiply)
      calculate "*";;
    divide)
      calculate "/";;
    quit)
      break;;
    *) 
      echo "Invalid option $REPLY";;
  esac
done

```

Stroing and printing output in array: 
```
arr=($(ls))
my_array_length=${#arr[@]}
echo $my_array_length

select element in "${arr[@]}"
do
   echo "${element}"
done
```
