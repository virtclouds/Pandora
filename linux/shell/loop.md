### for 循环语句
普通循环
```
for i in 0 1 2  
do  
     echo "Welcome $i times"  
done  
```

带有步长的循环
```
for i in {0..10..2}  
do  
     echo "Welcome $i times"  
done  
 ```

C语言风格循环
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

### while循环语句
只要特定条件为真，”while” 语句就会执行
```
#!/bin/bash
myvar=1
while [ $myvar -le 10 ]
do
        echo $myvar
        myvar=$(( $myvar + 1 ))
done
```

### util语句
“Until” 语句提供了与 “while” 语句相反的功能：只要特定条件为假，它们就重复。下面是一个与前面的 “while” 循环具有同等功能的 “until” 循环。
```
#!/bin/bash
myvar=1
until [ $myvar -gt 10 ]
do
        echo $myvar
       myvar=$(( $myvar + 1 ))
done
```
