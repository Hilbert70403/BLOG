# vscode代码上传到github

### 1.安装vscode

安装vscode，网址：https://code.visualstudio.com/download

一直按确定就可以了

### 2.安装git并连接github

然后是下载git，网址：https://git-scm.com/download

#### 2.1安装完成后，在vscode终端命令行操作

这里选择以vscode作为预设的editor，在终端输入git init

```
git init
```

再输入git config --globaluser.name“Hilbert70403”  

```
git config --globaluser.name“Hilbert70403” # 其中“引号里”填的是github的名字
```

再来输入git config --globaluser.email“email@email.com“

```
git config --globaluser.email“email@email.com“ # 其中“引号里”填的是注册github的邮箱
```

之后你可以输入git config --global --list

```
git config --global --list
```

检查自已有没有输错



再来要生成一个ssh key放到github中

继续在终端输入ssh-keygen -t rsa -C“email@email.com“

```
ssh-keygen -t rsa -C“email@email.com“ # 其中“引号里”填的是注册github的邮箱
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

然后再去github建一个仓库,

建完后会看到有个ssh的地址

![image-20221116103522789](C:\Users\Ricar\AppData\Roaming\Typora\typora-user-images\image-20221116103522789.png)

然后在vscode的终端输入git remote add origin [git@github.com](mailto:git@github.com):xxx.git

```
git remote add origin git@github.com:xxx.git  
# git@github.com:xxx.git输入的是你的地址
```

