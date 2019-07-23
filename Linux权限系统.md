权限系统解决 permission denied 的问题


## 问题排查过程

```ll``` 退回系统根目录查看不同账号的权限，rwx 之后可能跟随两个权限的说明

```cat /etc/passwd``` 查看用户，直接给用户权限搞不定，就给文件夹加权限

```chmod -R 777 /home/work/nifi``` 给所有用户对这个文件夹的 777 读写权限

```ps aux | grep nifi``` 查看当前进程

```find . -iname "*-*"`` 查找

```find . -iname "*-*" -type f ! -iname "*.py"```查找文件并排除 .py 文件 

```find . -iname "*-*" -type f ! -iname "*.py" -maxdepth 1 | xargs rm``` maxdepth 暂时不知道是啥

```ll -hlrt``` 查看当前目录的文件并按照时间排序


