title: Git同时推送到多个远程库

date: 2015-08-09 15:16:30

tags: Git

------

在有些情况下，我们希望将项目同时关联到多个远程库，并一次性推送到多个远程库。这里我们以同时推送到Github和Gitcafe为例，操作系统为OS X。
<br>

### 1. 创建本地git仓库

------
创建项目文件夹，并将其初始化为git仓库。

``` bash
mkdir ~/github/testGit
cd ~/github/testGit
git init
```
<!--more--><br>

### 2. 创建远程仓库

------

*  在Github创建远程仓库。
   
    ![](http://imgx.sinacloud.net/jerryshao/w_500,h_333/QQ20150812-1%402x.png)
   
   
*  在GitCafe创建远程仓库。
   
     ![](http://imgx.sinacloud.net/jerryshao/w_500,h_333/QQ20150812-2%402x.png)

<br>

### 3. 将本地仓库关联至远程仓库

------
-  关联至Github
  
   ![](http://imgx.sinacloud.net/jerryshao/w_500,h_333/QQ20150812-4%402x.png)
  
   ``` bash
   git remote add github 'git@github.com:jerry-shao/testGit.git'
   ```
  
-  关联至GitCafe
  
   ![](http://imgx.sinacloud.net/jerryshao/w_500,h_333/QQ20150812-3%402x.png)
  
   ``` bash
   git remote add gitcafe 'git@gitcafe.com:jerryshao/testGit.git'
   ```
  
-  配置仓库关联属性
  
   ``` bash
   cd ~/github/testGit/.git
   vi config
   ```
  
   打开config文件后，我们可以看到下图中含有我们之前操作的两条remote记录。
  
   ![](http://sinacloud.net/jerryshao/QQ20150812-5%402x.png)

- 将两条remote记录合并
  
   ![](http://sinacloud.net/jerryshao/QQ20150812-6%402x.png)
  
- 保存并退出，可连续输入两个大写Z。即shift+zz。
<br>

### 4. 推送至两个远程库

------

- 新建一个README.MD文件

  ``` bash
  vim README.MD
  ```

  输入*#testGit*， 保存并退出。

- commit并push到远程库

  ``` bash
  git add .
  git commit -m "readme"
  git push tworepo master
  ```

  ![](http://sinacloud.net/jerryshao/QQ20150812-7%402x.png)

  两个远程仓库均推送成功。

