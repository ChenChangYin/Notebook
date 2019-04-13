# linux考试复习

### scp的使用

scp -3 通过我将1中的文件拷贝到2中



### man手册

man -f reboot 找reboot

man -k 含有reboot的都找出



### whereis

查文件的路径



### which

查可执行文件

如 which ls

但 which cd 不可 因为cd是内置文件

### locate

查找 文件 根据索引查找

updatedb 重新建立索引

### grep

grep -w "文件"

### find

find 路径 -name 文件明 -atime +1



## 创建文件

### ls 

ls -al

文件类型权限 

ls -ali

ln 硬链接

ln -s 软链接

### cd

cd - 返回上次工作目录



### cp

cp -a[r,p]

cp -u 更新



### rm 

rm -i 交互模式

rm -rf



### mkdir

mkdir -p 自动创建不存在的路径

### touch

创建一个文件

### vim



### apt

apt-get --purge remove a 将软件a的所有东西删除

apt-get update 更新

apt-get install a 

apt-get upgrade 更新全部软件

## 三剑客

### grep

grep -w b 查找b的单词

grep -v b 查找不包含b的

### awk

```
awk -F 'BEGIN{print "Hello"} {printf("%s-%s\n" $1, $3)} END{printf("%s\n", "BYE")}' b
```

### sed



### free

查看内存

### ifconfg

查看本机ip

### df -h

查看磁盘

### du

看当前目录下文件大小

### 数据处理

### cut

cut -d : -f 1 a 以d作为分隔符 取文件a中的第一块

### sort

sort -

### tr

echo changyin | tr 'a-z' 'A-Z'

### xargs

### split

### kill 

信号

### pstree

### top

### read -s a



