# vscode代码上传到github

### 1.安装vscode

安装vscode，网址：https://code.visualstudio.com/download

一直按确定就可以了

### 2.安装git并连接github

然后是下载git，网址：https://git-scm.com/download

#### 2.1安装完成后，在vscode终端命令行操作

这里选择以vscode作为预设的editor，在终端输入git config --globaluser.name“Hilbert70403”  

```
git config --globaluser.name“Hilbert70403” # 其中“引号里”填的是github的名字
```

再来输入git config --globaluser.email“email@email.com“

```
git config --globaluser.email“ricardo70403@gmail.com“ # 其中“引号里”填的是注册github的邮箱
```

之后你可以输入git config --global --list

```
git config --global --list
```

检查自已有没有输错



再来要生成一个ssh key放到github中

继续在终端输入ssh-keygen -t rsa -C“email@email.com“

```
ssh-keygen -t rsa -C“ricardo70403@gmail.com“ # 其中“引号里”填的是注册github的邮箱
```

一路回车，在出现选择时输入Y，

```
Enter passphrase (empty for no passphrase):
Enter same passphrase again: 
# 上述提示是输入 安全码，此安全码的意思是每次上传文件到github上都需要输入的密码，为了方便此处可以直接回车不输入密码。
```

再一路回车直到生成密钥。会在/Users/***/路径下生成一个.ssh文件夹，密钥就存储在其中。

一路回车，在出现选择时输入Y，再一路回车直到生成密钥。会在/Users/***/路径下生成一个.ssh文件夹，密钥就存储在其中。

可以在提示的那个/Users/xx/路径中用记事本打开id_rsa.pub

并把那段内容复制到github的setting的SSH and GPG keys，选择New SSH key

![image-20221116103346519](C:\Users\Ricar\AppData\Roaming\Typora\typora-user-images\image-20221116103346519.png)

把那段文字复制并保存

之后可以在vscode的终端输入**ssh -T** [git@github.com](mailto:git@github.com)

```
ssh -T git@github.com
```

之后会有个提示你输入yes，就可以连接成功了

上述操作表示GitHub和VSCODE建立连接

#### 2.2 本地建立同名仓库并上传到远程仓库

首先在Vscode打开本地工程文件夹项目，点击终端->新建终端

在vscode终端输入

```
git init # 初始化项目

git status # 查看状态
git branch # 查看分支

git add readme.md # 添加文件
git add . # 添加所有文件

git commit -m "这里填的内容为每次上传文件的备注信息"
```



去github建一个仓库,建完后会看到有个ssh的地址

![image-20221116103522789](C:\Users\Ricar\AppData\Roaming\Typora\typora-user-images\image-20221116103522789.png)

推送到远程仓库，在vscode终端输入

```
git remote add origin git@github.com:xxx.git  # git@github.com:xxx.git输入的是你的地址
```

push到远程仓库

```
git push -u origin master
```

上传完成

#### 2.3 上传新文件&上传修改文件

点击changes中 + 符号将test.md添加到 Staged Changes中

此操作类似于

```
git add readme.md # 添加文件
```

![image-20221116154559550](C:\Users\Ricar\AppData\Roaming\Typora\typora-user-images\image-20221116154559550.png)

在Message（Ctrl+Enter to commit on 'master'）框内添加备注信息 

此操作类似于 

```
git commit -m "这里填的内容为每次上传文件的备注信息"
```

点击Commit提交或者点击commit & push

![image-20221116154959659](C:\Users\Ricar\AppData\Roaming\Typora\typora-user-images\image-20221116154959659.png)



### Linux下建立Git和GitHub的连接

#### 1、安装git

Ubuntu 安装 Git： 

```
apt-get install git 
```

配置Git用户信息

```
 git config --global user.name "Hilbert70403"
 git config --global user.email "ricardo70403@gmail.com"
```

↑ 把用户名和邮箱换成你自己的，键入命令后屏幕没有输出，则表示设置成功了

#### 2、开启SSH服务

Ubuntu 安装 SSH： 

```
apt-get install ssh 
```

查看 SSH 服务状态： 

```
ps -e | grep sshd 
```

![image-20221116193712677](C:\Users\Ricar\AppData\Roaming\Typora\typora-user-images\image-20221116193712677.png)

sshd 表示 ssh-server 已启动

#### 3、生成SSH KEY

生成 SSH KEY： 

```
ssh-keygen -t rsa -C "ricardo70403@gmail.com" 
```

生成 ssh key 过程中，会让你填写 passphrase，连按三次回车跳过即可。

以下ls命令查看 ssh key 是否存在

```
ls -al /root/.ssh
```

打开 id_rsa.pub 文件，将内容复制到剪贴板： 

```
vim id_rsa.pub 
```

#### 4、添加SSH KEY 

这一步骤与Windows下的vscode中

并把那段内容复制到github的setting的SSH and GPG keys，选择New SSH key

相同

5、克隆远程仓库到本地仓库

```
git clone git@github.com:Hilbert70403/yoloair_run.git
```

命令查看仓库远程本地的连接状态

```
git remote -v
```

```
git status # 查看状态

git add file.txt # 添加文件到暂存区
git rm file.txt # 删除文件到暂存区

git commit -m "备注信息" # 提交本次修改

git push origin master # 推送到远程仓库

```

