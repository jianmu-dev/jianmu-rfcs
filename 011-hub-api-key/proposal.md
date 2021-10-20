# 概述

为系统提供拉取私有节点定义的API-Key

# 问题描述

当用户希望在Pipeline/Workflow定义中使用自己在[官方节点库](https://hub.jianmu.dev)创建的私有节点时，需要提供Hub用户的Api-key进行认证鉴权

# 约束条件

同时需要考虑未来提供私有Registry时，是否需要改动当前方案

# 解决方案

* 方案一： 在当前Pipeline/Workflow定义中添加hub的顶层语法定义相关配置如下：

```
hub:
  url: https://hub.jianmu.dev/hub/
  ak: ((hub.ak))
  sk: ((hub.sk))
```

* 方案二： 在Pipeline/Workflow定义的每个节点部分添加hub相关语法定义：

```
pipeline:
  name: CI_Flow
  ref: ci_flow
  description: jianmu-workflow-core CI Flow
  GitClone:
    type: 172.20.1.23:5000/git_clone:0.4
    param:
      commit_branch: ${branch_name}
      remote_url: https://gitee.com/jianmu-dev/jianmu-workflow-core.git
    hub:
      url: http://172.20.52.15:5000/
      ak: ((hub.ak))
      sk: ((hub.sk))
```

# 待讨论问题

使用方案一对当前语法侵入性低，但是未来支持私有Registry时存在局限性

使用方案二时如果存在多个同源私有节点时，语法较为啰嗦

# 已解决问题

API-Key的值可以使用明文或引用密钥存储中的值

# 后果

无