


## docker

```sudo docker system prune ``` 
``` sudo docker ps -a ``` 列出现有的镜像
```sudo docker container rm 21c614a20171``` 删除 docker 容器
```sudo docker exec -it nifi bash ``` 进入 docker 安装的文件当中


在 toolkit 下生成配置文件
```
bin/tls-toolkit.sh standalone -n 'ip-172-31-21-15.ap-east-1.compute.internal' -C 'CN=Admin, O=CovenantLAB, OU=Nifi, C=CN' -o certs
``` 

docker run nifi 初始化配置

```
sudo docker run --ulimit nofile=100000:100000 --name nifi   -v /home/ubuntu/nifi-toolkit-1.8.0/certs/ip-172-31-21-15.ap-east-1.compute.internal:/opt/certs   -p 7890:7890   -e AUTH=tls   -e KEYSTORE_PATH=/opt/certs/keystore.jks   -e KEYSTORE_TYPE=JKS   -e KEYSTORE_PASSWORD=R7ZcOThXoMhxL/HeJcuuf02JxDGEjXr344mVG6oWixk   -e TRUSTSTORE_PATH=/opt/certs/truststore.jks   -e TRUSTSTORE_PASSWORD=WBwNVGxns/+sZ5AtcxC6XffERQOnABjvJiwIneu6JIQ   -e TRUSTSTORE_TYPE=JKS   -e INITIAL_ADMIN_IDENTITY='CN=Admin, O=CovenantLAB, OU=Nifi, C=CN' -e NIFI_WEB_HTTPS_PORT=7890 -e 'NIFI_WEB_PROXY_HOST=ip-172-31-21-15.ap-east-1.compute.internal:7890'  -d   apache/nifi:latest
```

docker run nifi-registry 初始化配置

```
sudo docker run --ulimit nofile=100000:100000 --name nifi-registry   -v /home/ubuntu/nifi-toolkit-1.8.0/certs/ip-172-31-21-15.ap-east-1.compute.internal:/opt/certs  -p 18443:18443  -e AUTH=tls   -e KEYSTORE_PATH=/opt/certs/keystore.jks   -e KEYSTORE_TYPE=JKS   -e KEYSTORE_PASSWORD=R7ZcOThXoMhxL/HeJcuuf02JxDGEjXr344mVG6oWixk   -e TRUSTSTORE_PATH=/opt/certs/truststore.jks   -e TRUSTSTORE_PASSWORD=WBwNVGxns/+sZ5AtcxC6XffERQOnABjvJiwIneu6JIQ  -e TRUSTSTORE_TYPE=JKS   -e INITIAL_ADMIN_IDENTITY='CN=AdminUser, OU=nifi'   -e NIFI_WEB_HTTPS_PORT=18443   -e 'NIFI_WEB_PROXY_HOST=ip-172-31-21-15.ap-east-1.compute.internal:18443'   -d  apache/nifi-registry:latest  
  ```
  
  
