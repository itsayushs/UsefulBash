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

SSH to multiple nodes and append output with sed 
```
export WORKER_PREFIX=adi731
export DIR_NAME=/tmp/worker-monitoring
export NUM_WORKERS=4

rm -rf ${DIR_NAME}
mkdir ${DIR_NAME}

seq ${NUM_WORKERS} | xargs -I {} -P 150 bash -c "ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no ${WORKER_PREFIX}-{} 'df -h / --output\=pcent | tail -1' | sed 's/^/${WORKER_PREFIX}{}/' >> ${DIR_NAME}/disk_usage.output"
sort -r -t ' ' -k 2 ${DIR_NAME}/disk_usage.output | awk -F ' ' '$2 > 4 {print $1","$2}' > ${DIR_NAME}/disk_usage.csv

```
