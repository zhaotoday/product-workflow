## 一、发布环境

### 测试环境
name: test  
url: http://{app}.test.liruan.cn/

### 预生产环境
name: beta  
url: http://{app}.beta.liruan.cn/

### 生产环境
name: prod  
url: http://www.{app}.cn/ 或 http://{app}.prod.liruan.cn/

## 二、分支

### master
可发布到 beta 和 prod，在 beta 上走查无误方可发布到 prod。

### develop
稳定版本，新特性的起点。

### feature/*
新特性开发。

### release/*
发布到 test，提测、BUG 修复。

### hotfix/*
线上 BUG 修复。

## 三、流程

### 新特性开发
1. 接到一个新产品特性 a；
2. 从 develop 分出新分支 feature/a；
3. 在 feature/a 开发特性 a；
4. 完成开发，结束特性 a，代码合并到 develop；

### 提测
1. 从 develop（此时 develop 可能包含多个特性：feature/a、feature/b ...）分出新分支 release/ab；
2. 在 release/ab 上修复 QA 测试的 BUG；
3. 完成测试，结束 release/ab，代码合并到 develop 和 master；

### 修复线上 BUG
1. 从 master 分出新分支 hotfix/somebugs；
2. 修复 BUG；
3. 完成 BUG 修复，结束 hotfix/somebugs，代码合并到 develop 和 master；

## 四、注意事项
1. 用于发布的分支有 master、release/*，所以只能在这两个分支上构建代码，减少合并时的冲突。  
2. 命令参考：http://www.qianduan.org/post-447.html 。
