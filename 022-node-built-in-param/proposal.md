提案实现进度见[Issue](https://gitee.com/jianmu-dev/jianmu-ci-server/issues/I4O4MJ)

# 概述

* 节点任务执行完成后提供一些基本的内置输出参数

# 问题描述

* 当前节点任务执行完成后，下游节点只能获取节点定义中定义过的输出参数。缺乏节点任务执行过程中的自身的一些元数据。

* 当上游节点失败后，下游节点无法获取上游节点的失败状态。

# 约束条件

节点定义校验时，不允许设置`inner`开头的输出参数

# 解决方案

为节点添加以`inner`开头的内置输出参数

如下:
```
# 节点任务执行状态
xxx.inner.execution_status

```

* 引用示例：
```
yaml_lint:
    targets:
        - condition
    image: sdesbure/yamllint
    script: 
      - 'yamllint -d "{extends: relaxed, rules: {new-line-at-end-of-file: disable, new-lines: disable}}" *.yml'
condition:
    sources:
        - yaml_lint
    type: condition
    expression: ${yaml_lint.inner.execution_status} == "EXECUTION_SUCCEEDED"
    cases:
        true: feishu_notice_post1
        false: feishu_notice_post2
```

# 待讨论问题

* 其他需要添加的内置输出参数

# 已解决问题

无

# 后果

无