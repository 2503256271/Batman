远程仓库

- github

- 码云



## git和github的关系

git是一个版本管理工具，github提供了一个`网络版本`的代码库，它可以允许你在远程建立git库，这样你就不用担心本地电脑坏掉啦。

假设你已经先在**github上申请帐号**（它会向你的邮箱发验证码，提醒：你的邮箱可能会把它当作一个垃圾邮件）。接下来，我们看看我们目前的处境：

- 有一个可以建立远程库的github帐号

- 有一个本地使用的版本管理工具git。

下面我们就来介绍一下如何把它们关联起来。

## github基本操作

### 把别人的代码下载下来

1. 找到你兴趣的代码，复制地址。

   ![1574051491491](asset/1574051491491.png)

2. 运行命令：`git clone 地址`

### 建立自己的远程代码仓库

前提你必须先要注册。

<img src="asset/1568953444783.png" alt="1568953444783" style="zoom:50%;" />

- 公开 / 私人 
- 关于license: https://www.cnblogs.com/Wayou/p/how_to_choose_a_license.html

### 删除仓库

删除不需要的仓库。

![image-20200114210220468](asset/image-20200114210220468.png)

## 同步



### https协议代码同步

![1574051491491](asset/1574051491491.png)

1. 登陆github，创建仓库

2. 在电脑的某个文件夹下，通过git clone到本地。

   - git clone命令会自动创建一个文件夹，文件夹名就是项目名
   - git clone命令只需要在第一次时使用

3. 本地正常编辑（修改代码，新建文件等等），提交到本地仓库。

   1. git add .
   2. git commit

4. 推送到远程github

   git push  （如果是第一次push,会要求你输入github的帐号和密码）

<img src="asset/1574074090801.png" alt="1574074090801" style="zoom:50%;" />



### ssh协议代码同步

<img src="asset/image-20200114204955965.png" alt="image-20200114204955965" style="zoom: 67%;" />

ssh是一种网络协议，用于计算机之间的加密登录。如果一个用户从本地计算机，使用SSH协议登录另一台远程计算机，我们就可以认为，这种登陆是安全的，即使中途被截获，密码也不会泄露。



<img src="asset/image-20200114204120048.png" alt="image-20200114204120048" style="zoom: 50%;" />

配置步骤：

1. 使用git bash在本地生成钥匙：

- 私钥
- 公钥 

2. 把公钥给github



步骤

1. git bash下执行： `ssh-keygen -t rsa` 。一路默认回车即可。 

它会生成钥匙，默认会保存在c:/users/当前用户/.ssh/id_rsa.pub，

2. 找到id_rsa.pub并打开复制内容。
3. 在github上设置，找到SSH配置项，新建keys，把id_rsa.pub中的内容复制。
4. 正常进行后续代码仓库clone，commit，push。





### 多端同步

<img src="./asset/1562578831352.png" alt="1562578831352" style="zoom:50%;" />

基本操作流程：

1. 在github（或者是公司自己的代码库）上建立仓库

2. 在A电脑上：使用https/ssh协议，通过git clone到本地。

   - clone命令会创建一个文件夹
   - clone命令只需要在第一次时使用

3. 在A电脑上：正常本地编辑（修改代码，新建文件等等），提交到本地仓库。

   1. git add .
   2. git commit

4. 在A电脑上：把本地仓库同步到远程github

   git push

5. 在B电脑上：git clone 到本地

6. 拉取：git pull 

   git pull  是从远程拉取最新的代码。（可能在你在本地修改代码时，有另外的同事也在修改代码，所以在提交之间一定要先拉取最新的代码）

> 上班第一件事： git pull
>
> 下班最后一件事：git push

### 多人合作

一个公开代码仓库中的代码

![image-20200114205504261](asset/image-20200114205504261.png)

## github博客

建立格式名为: `用户名.github.io`的仓库。这个特殊之处就是在于这个名字。



## 把本地仓库推到远程github

如果你先在本地建立了git库，想关联到远程github。

前提：本地有一个仓库，想推到远程。

你应该这样做：

1. 去github上建立一个与**本地代码库同名的空代码库**。

   ![1574418661362](asset/1574418661362.png)

2. 使用如下命令：

   进入到本地仓库，先把所有的代码都提交到本地仓库。再运行下面的两句命令：

   ```
   git remote add origin https://github.com/fanyoufu/bigevent90.git
   git push -u origin master
   ```

   

把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支`master`推送到远程。

由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

如果上面两句代码成功。则后续就不再需要这两句，直接操作就可以：

- 提交到远程：`git push`
- 从远程下拉：`git pull`


