### 第一步 找到文件夹
.ssh 是用来存放 ssh 密钥的文件地址，. 意思是隐藏文件，
```.ssh/``` 

### 第二步 移动密钥到 .ssh
下载私钥文件之后：
```mv Downloads/files_testnet-work.txt .ssh/```移动文件到 .ssh 文件夹之下

#### 查看文件
```ls -lrth```ls 带参数的高级用法，详见 [每天一个linux命令(1)：ls命令](https://www.cnblogs.com/peida/archive/2012/10/23/2734829.html)

### 第三步 权限设置
```chmod 600 files_testnet-work.txt ``` 设置 600 权限
```mv files_testnet-work.txt testnet-work``` 移动到 testnet-work 文件夹，等于直接创建

### 第四步 访问
```ssh work@hdp00.gridb.io -i testnet-work ``` 
```-i``` 指定 ssh 公钥文件


### 第五步 config 设置
```touch config``` 创建

```chmod 600 config```权限

```vim config```暂时不知道

### 第六部 端口设置以便浏览器访问
```ssh -NfL 9000:localhost:8080 work@hdp00.gridb.io -i ~/.ssh/testnet-work ```


### SCP 本地到远程复制

```scp -i JP-TOKEN.txt /Users/lichenxi/Trello_csv.py ubuntu@3.112.61.135:/home/ubuntu/nifi/nifi-test```

### 查看端口的情况
```curl -Lsvvv http://3.112.61.135:7890/nifi/```

### Refs
使用SSH连接Linux服务器 https://www.jianshu.com/p/59c4fc2684be
