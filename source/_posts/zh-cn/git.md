---
title: git
excerpt: git
categories: 
- FE
---


# 安装
## 安装ssh
安装：apt-get install openssh-server openssh-client
重启服务： /etc/init.d/ssh restart

## 安装git
apt-get install git-core

## 生成ssh密钥
- 输入命令： ssh-keygen -C 'goumang2010@live.com' -t rsa
（'goumang2010@live.com' 是我的github邮箱）
-C为提供注释 -t rsa表示生成的类型为rsa
一路回车即可

## 在github上配置密钥
- 获取密钥文件，把该文件拷贝至ftp目录： cp ~/.ssh/id_rsa.pub /home/ftp/data
- 使用编辑器打开该文件，打开Github，点击自己图标=>Settings，在左侧点击 SSH Keys，然后点击Add SSH key，title随便起，在Key处把id_rsa.pub文件的'''全部内容'''复制进去，然后点击Add Key，输入自己的Github密码后保存。
- 在Ubuntu中键入ssh -v git@github.com进行测试  出现Exit status 1表示成功，测试后，github上该key的绿灯也会亮起来

# 命令


## 克隆拉取
* 将项目克隆至本地：
```
git clone git@github.com:goumang2010/NetClipBoard.git
```
  （goumang2010为用户名，NetClipBoard为项目名称）
* 拉取commit并与本地同步（首先需进入git仓库所在目录：cd /home/ftp/data/NetClipBoard/） ：
```
git pull
```

## 添加提交
* 添加所有文件及修改：
```
git add -A
```
* 提交
```
git commit -m "your message"
```

## 远程推送
参照：[https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)
* 设置远程目录：
```
 
git remote add origin git@github.com:xxx.git
```
* 推送至远程目录
```
git push origin master
```
* 修改远程目录
```
git remote set-url origin [https://github.com/USERNAME/OTHERREPOSITORY.git](https://github.com/USERNAME/OTHERREPOSITORY.git)
```
参考：[https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)

## pull request
- fork原项目
- 新建分支并切换至该分支<br />
```
git branch newbranchname
```

```
git checkout newbranchname
```
- 推送分支到远程 
```
git push --set-upstream origin newbranchname
```
- 在github界面上发起pull request
参考:[http://blog.csdn.net/zhangdaiscott/article/details/17438153](http://blog.csdn.net/zhangdaiscott/article/details/17438153)