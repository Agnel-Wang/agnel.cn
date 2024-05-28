---
title: Git
linktitle: Git
type: book
weight: 10
---

## 管理多个git账号

用于同时有gitlab和github的情况

①生成rsa key并添加到github和gitlab的设置中
②配置 `~/.ssh/config`
```bash
# 以github举例
Host github
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_github
    User git
```

③检测是否配置成功
```bash
ssh -T git@github.com
```
## 仓库迁移

已迁移的仓库更改远程url
```bash
git remote set-url origin new_url
```

### 1. gitlab --> gitlab

①旧仓库

```mermaid
graph LR
A[设置]
B[通用]
C[高级]
D[导出项目]

A --> B --> C --> D
```

②新仓库

```mermaid
graph LR
A[新建项目]
B[导入项目]
C[Gitlab导出]

A --> B --> C
```


### 2. github --> gitlab

①gitlab创建一同名空仓库(无README)
②在任意目录克隆旧仓库
```bash
git clone --mirror old_url
cd repo
git remote set-url --push origin new_url
git push --mirror origin
```