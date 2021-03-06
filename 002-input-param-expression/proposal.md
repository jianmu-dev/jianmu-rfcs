提案实现进度,见[Issue I48AX6](https://gitee.com/jianmu-dev/jianmu-ci-server/issues/I48AX6)

# 概述

* 输入参数（含，全局参数）支持表达式关联

# 问题描述

* dsl中节点定义输入参数只能关联单个变量（如，密钥、全局参数、事件参数、任务输出参数），不支持多个变量拼接的表达式

* 全局参数不支持关联变量（如，密钥、事件参数），只支持常量

# 约束条件

* 需要重构参数关联模型

# 解决方案

修改jianmu-el表达式语法,增加反引号语法表示字符串模版替换

只支持数字、布尔和null到字符串类型的隐式转换,其他类型不匹配时会报错

如下:
```
${a} + ${b} + `${c}+${d}` == aaabbbccc+ddd 

`${c}+${d}` == ccc+ddd
```


* dsl示例：
```
param:
  git_username: ((xxx.xxx))
  branch: $(xxx.xxx)
  path: `$(xxx.xxx)/$(xxx.xxx)/`

qiniu_upload:
  type: jianmu_runner_qiniu:0.1.2
  param:
    qiniu_upload_prefix: `${xxx.xxx}/${xxx.xxx}/`
```

# 待讨论问题

* 参数值的合法性校验无法前置，只能在运行时校验，当前无法拿到错误提示，通过归集流程实例日志，展示错误提示 

# 已解决问题

无

# 后果

* 此变更对现有参数领域模型数据有侵入性，需要数据迁移或重新创建所有项目