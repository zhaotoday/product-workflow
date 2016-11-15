# 结合网龙共享平台总结的产品发布流程及 git flow 工作流

## 发布环境：

### 测试环境
名称：test
域名：{app}.test.liruan.cn）

### 预生产环境
名称：beta
域名：{app}.bate.liruan.cn）

### 生产环境
名称：prod
域名：www.{app}.cn 或 {app}.prod.liruan.cn

注：{app} 为业务英文名称。

## 分支

### master
发布到预生产和生产，在预生产上走查无误方可发布到正式

### develop
发布到测试环境，用于 QA 测试，BUG 修复

### feature/*
新特性开发

### release/*
提测，BUG 修复

### hotfix/*
生产 BUG 修复

## 流程：

### 一、新特性开发
1. 接到一个新产品特性 a；
2. 从 develop 分出新分支 feature/a；
3. 在 feature/a 开发特性 a；
4. 完成开发，结束特性 a，代码合并到 develop；

### 二、提测
1. 从 develop（此时 develop 可能包含多个特性：feature/a、feature/b ...）分出新分支 release/ab；
2. 在 release 上修复 QA 测试的 BUG；
3. 完成测试，结束 release/ab，代码合并到 develop 和 master；

### 三、修复线上 BUG
1. 从 master 分出新分支 hotfix/somebugs；
2. 修复 BUG；
3. 完成 BUG 修复，结束 hotfix/somebugs，代码合并到 develop 和 master；  

