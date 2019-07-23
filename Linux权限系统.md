权限系统解决 permission denied 的问题


## 问题排查过程

```ll``` 退回系统根目录查看不同账号的权限，rwx 之后可能跟随两个权限的说明

```cat /etc/passwd``` 查看用户，直接给用户权限搞不定，就给文件夹加权限

```chmod -R 777 /home/work/nifi``` 给所有用户对这个文件夹的 777 读写权限

```ps au | grep nifi``` 查看当前进程
