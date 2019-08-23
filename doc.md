### DOC

## Linux 下 docker 安装

[docker](https://www.docker.com/)官方网站

centos 下 docker 的[安装参考](https://docs.docker.com/install/linux/docker-ce/centos/)

## apereo/cas 构建

官方地址 [apereo/cas](https://github.com/apereo/cas)

在官网的[releases](https://github.com/apereo/cas/releases)下载对应版本到本地，解压
进入目录找到 build.gradle 文件
cas 构建时要注释掉 git 这里

```
/*
        Open the project git repository in the current directory.
        Get commit id of HEAD.

    git = org.ajoberstar.grgit.Grgit.open(dir: file('.').canonicalPath)
    def gitHead = git.head()
    currentRevision = gitHead.id
    currentAbbreviatedRevision = gitHead.abbreviatedId
    git.close()
    */
```

设置当前版本为你下载的版本

```
currentRevision = "cas-6.1.0-RC4"
注释用到的仓库
repositories {
        mavenLocal()
        jcenter()
//        maven { url "https://maven.eveoh.nl/content/repositories/releases" }
        maven { url "https://plugins.gradle.org/m2/" }
        maven { url "https://repo.spring.io/plugins-release" }
        maven { url "https://repo.spring.io/libs-milestone" }
    }
```

参考[CAS Overlay Template](https://github.com/apereo/cas-overlay-template) 命令
