
#### 什么是 CI/CD
第一次自己搞 CI 的项目，踩了很多坑也学到很多，简单记录一下。CI(Continuges Integration)持续集成和部署，每当有代码提交的时候，会自动化运行测试和代码的编译等。首先明确以下几个概念：

##### Pipline 
一次 Pipeline 其实相当于一次构建任务，里面可以包含多个流程，如安装依赖、运行测试、编译、部署测试服务器、部署生产服务器等流程。 任何提交或者 Merge Request 的合并都可以触发 Pipeline。

##### Stages
Stages 表示构建阶段，说白了就是上面提到的流程。 我们可以在一次 Pipeline 中定义多个 Stages，这些 Stages 会有以下特点：

所有 Stages 会按照顺序运行，即当一个 Stage 完成后，下一个 Stage 才会开始
只有当所有 Stages 完成后，该构建任务 (Pipeline) 才会成功
如果任何一个 Stage 失败，那么后面的 Stages 不会执行，该构建任务 (Pipeline) 失败
因此，Stages 和 Pipeline 的关系就是一个 pipline 对应多个 stages 的，具体则在 gitlab-ci.yml 当中配置。

##### Jobs
Jobs 表示构建工作，表示某个 Stage 里面执行的工作。 我们可以在 Stages 里面定义多个 Jobs，这些 Jobs 会有以下特点：

相同 Stage 中的 Jobs 会并行执行
相同 Stage 中的 Jobs 都执行成功时，该 Stage 才会成功
如果任何一个 Job 失败，那么该 Stage 失败，即该构建任务 (Pipeline) 失败


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
https://docs.docker.com/compose/compose-file/compose-file-v2/#ipv4_address-ipv6_address 

##### 配置 gitlab-runner config file


#### golang 的单元测试
golang 被墙的，编译的时候需要加一个配置：
```go env -w GOPROXY=https://goproxy.cn,direct```

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
