### Before 
第一次自己搞 CI 的项目，踩了很多坑也学到很多，简单记录一下。

### 正文
#### 什么是 CI/CD

#### 配置 gitlab-runner
- docker 起
- 配置 gitlab-runner 
  - 小坑，gitlab-runner 会默认把 Can run untagged jobs 设置为 False，所以commit没有带指定 tag 的时候是不会触发的。
  - 小坑，gitlab-runner 用 docker 起的时候里面默认是没有 go 的，还是用 shell 把，比较靠谱，然后因为没有 go 所以又换回了 docker，日常被坑，apt-get 不能拉到最新的，手动安装还不如直接拉取 image。
- .gitlab-ci.yml

各种项目语言的 ci 配置文件
https://gitlab.com/gitlab-org/gitlab-foss/blob/master/lib/gitlab/ci/templates

#### 配置 docker-compose file
##### tag 部署
##### 配置静态 IP 
 

##### 配置 gitlab-runner config file


#### golang 的单元测试

##### 配置 config-test 
- go 的坑，再拉取极光推送依赖包的时候有问题，因为 golang.org 被墙了，需要加上```go env -w GOPROXY=https://goproxy.cn,direct```


- ```nc -vz localhost 15432``` 查看本地端口是否在运行
- docker 起的 runner 需要配置一个静态地址 host 来访问，docker-compose.yml 需要设置成 version2，然后去掉 unexpected ipv6 就可以把服务跑起来了
https://docs.docker.com/compose/compose-file/compose-file-v2/#networks

- docker network ls 在 docker 里面配置的网络是可以列出来的。。我太无知了。。我对 CI 简直一无所知

- CI 里面的单测还需要依赖数据库里面的表，在数据库跑起来以后要跑一下建表的脚本。


### Conclusion
总结一下为什么这么多坑的原因，
- 缺乏对于 CI 的认知
- 对于主项目不够了解，陌生的语言+陌生的数据库
- 没有自动化一些重复性的工作（部署，拉 docker image 等）
