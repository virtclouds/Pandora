### for 循环

```
for i in {0..10..2}  
do  
     echo "Welcome $i times"  
done  
 ```
 ```
 for((i=0;i<10;i=i+2))
 do  
      echo "Welcome $i times"  
done  
```

对目录的循环

```
#!/bin/bash
for x in /var/log/*
do
        #echo "$x is a file living in /var/log"
        echo $(basename $x) is a file living in /var/log
done
```
