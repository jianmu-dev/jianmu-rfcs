# 概述

为简化使用，删除当前流程DSL和管道DSL中的`ref`、`name`和`description`

# 问题描述

当前流程DSL和管道DSL都存在如下段落:
```
workflow:
  name: 建木官网CDN CI/CD
  ref: jianmu_official_site_cdn_cicd
  description: 建木官网CDN CI/CD
```
或
```
pipeline:
  name: 建木官网CDN CI/CD
  ref: jianmu_official_site_cdn_cicd
  description: 建木官网CDN CI/CD
```
并无实际用途，过于冗长

# 约束条件

无

# 解决方案

删除`ref`语句，内部使用项目ID作为流程定义的ref

删除`name`和`description`语句，改完新建项目时由用户在界面上填写

批量导入项目时如何处理`name`和`description`？

可以在导入的API上提供`name`和`description`的值或者使用DSL文件的文件名作为`name`的值

# 待讨论问题

无

# 已解决问题

无

# 后果

一旦实施，无法兼容之前版本已创建的项目，需要重新创建项目
