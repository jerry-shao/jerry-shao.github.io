title: 初次使用Hexo遇到的一些问题

date: 2015-07-29 15:40:46

category: Hexo

------

今天把Blog从Wordpress迁移到了Hexo，初次使用静态Blog，遇到了一些问题，整理如下。( 部分问题可能仅存在于OS X系统 )

### 安装Hexo报错

安装流程是按照Node.js官方指导，下载安装包一步一步安装，Node.js和npm同时由Node.js提供的包安装。

此时执行

``` bash
node -v
npm -v
```

版本号正常显示

问题：安装Hexo，执行以下命令时报错。

``` bash
npm install hexo-cli -g
```

<!--more-->

因错误信息中注明no permission to access，以为是权限问题。

然后执行命令

``` bash
sudo npm install hexo-cli -g
```

错误依然抛出。

*后来在[StackOverflow](http://stackoverflow.com/questions/15633029/npm-no-longer-working)找到解决办法：*

原因出在OS X版npm安装包上，需要下载npm源代码重新Make并安装。

1. 通过执行以下命令下载npm源代码重Make并安装
   
   ``` bash
   git clone http://github.com/isaacs/npm.git
   cd npm
   sudo make install
   ```
   
2. 安装Hexo
   
   ``` bash
   sudo npm install hexo-cli -g
   ```
   
   此时hexo已经正确安装。

------

### 更改主题后本地显示正常，部署后无法加载CSS

使用默认主题landscape时，本地和部署后都可以正常显示。然而更换主题后，本地测试正常，部署后排版错乱，显然没有正确加载所需的CSS样式。

问题出在Hexo站点根目录的_config.yml文件上。

*解决方法：*

- 最初测试时，为了不影响站点使用，我将站点绑定至二级域名pages.jerryshao.com，并将_config.yml文件中url属性设置为pages.jerryshao.com，此时本地和远端均正常显示。
- 在将根域名解析过去以后，_config.yml中url属性没有及时更改，且该属性不会影响本地测试。将url改为新的网站地址，CSS样式加载正常，问题解决。
- 在几个平台回答了遇到同样问题的网友，大概都是因为忘记修改_config.yml文件中url属性所致。

