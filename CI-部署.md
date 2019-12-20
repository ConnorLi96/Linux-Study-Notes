主要分为几个步骤：
- 配置 gitlab-runner，
  - 小坑，gitlab-runner 会默认把 Can run untagged jobs 设置为 False，所以commit没有带指定 tag 的时候是不会触发的。
  - 小坑，gitlab-runner 用 docker 起的时候里面默认是没有 go 的，还是用 shell 把，比较靠谱
- .gitlab-ci.yml


各种项目语言的 ci 配置文件
https://gitlab.com/gitlab-org/gitlab-foss/blob/master/lib/gitlab/ci/templates
