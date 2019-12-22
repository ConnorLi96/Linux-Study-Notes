主要分为几个步骤：
- scp code
- 配置 runner
- docker


- 配置 gitlab-runner 
  - 小坑，gitlab-runner 会默认把 Can run untagged jobs 设置为 False，所以commit没有带指定 tag 的时候是不会触发的。
  - 小坑，gitlab-runner 用 docker 起的时候里面默认是没有 go 的，还是用 shell 把，比较靠谱，然后因为没有 go 所以又换回了 docker，日常被坑，apt-get 不能拉到最新的，手动安装还不如直接拉取 image。
- .gitlab-ci.yml


各种项目语言的 ci 配置文件
https://gitlab.com/gitlab-org/gitlab-foss/blob/master/lib/gitlab/ci/templates
