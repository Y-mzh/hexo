---
title: Hexo+GithubPage搭建个人博客（Windows）
keywords: Hexo,Git,GitHub,搭建个人博客
categories:
- Git
---
### 准备工作
1.	##### 安装node.Js
	去 NodeJs 官网下载相应版本，进行安装即可。可以通过node -v的命令来测试NodeJS是否安装成功。
    
2.	##### 安装Git 
	去 Git 官网下载相应版本，进行安装即可。 可以通过git –version的命令来测试git是否安装成功。
3.	##### 注册Github账号 
	去 Github 官网进行注册。 注册完之后记得添加 SSH Key。 
	这个 SSH Key是一个认证，让github识别绑定这台机器，允许这台机器提交。执行如下命令：
    ```
    cd ~/. ssh
    ```
    ~这个符号，表示在用户目录下，如果提示：No such file or directory 说明是第一次使用		 	 	 git。 
    生产新的SSH Key配置，在Git Bash执行代码：
    ```
    ssh-keygen -t rsa -C "此处写邮箱地址"
    ```
    成功后会生成两个文件id_rsa 以及id_rsa.pub。然后添加在github上
    
4.	##### 搭建博客
	1.**安装Hexo:**
		在本地新建一个Hexo文件夹，文件右键，选择Git Bash。
        输入指令安装hexo：
        ```
        npm install -g hexo 
        ```
        等安装完毕，通过输入hexo的命令来测试Hexo是否安装成功,成功如下图展示:
        ![](../../img/githexo.jpg '安装Hexo')
	2.**初始化Hexo：**
		```
        hexo init hexo 
        ```
        初始化成功会显示Start blogging with Hexo! 
        这时在你刚才创建的Hexo里面会多出一个hexo文件 。
        进入到hexo目录，右键，选择Git Bash，输入下面指令安装依赖：
        ```
        npm install
        ```
       部署形成文件：
       ```
       hexo generate
       ```
       运行hexo服务
       ```
       hexo server
       ```
       打开浏览器，输入http://localhost:4000/便可看到默认的博客。
       
	3.**配置githubPage**
		登录Github，点击”New repository”，新建一个版本库。 
		输入仓库名：你的Github名称.github.io。然后点击Create repository。 
        **注意：这边的创建名字，一定要用的github的用户名，不然显示不出来，因为githubPage只能你的用户名。**
        
	4.**启用GitHub Page**
		进入项目，点击Settings，如下图：
        ![](../../img/git-setting.jpg '设置')
        进入设置界面，下拉找到Choose a theme，如下图：
        ![](../../img/chooseTheme.jpg '设置')
        选择一个随意模版，点击”Select theme”,发布github默认生成的一个静态站点。
        试着打开自己在github的静态网址，https://y-mzh.github.io/。
        
	5.**将本地hexo项目托管到Github**
		打开修改hexo目录下配置文件_config.yml。 
        ![](../../img/config.jpg '设置')
        编辑最后面的deploy属性，加入代码：
        ```
        type: git
  		repository: git@github.com:Y-mzh/Y-mzh.github.io.git
  		branch: master 
        ```
        type使用是git。 
		repository属性改成你的刚才创建仓库git地址。 
		分支branch填写master。
	6.**网站的配置文件，这里列举部分关键配置：**
		```
        # Site
        title:  Blog //网站的标题
        subtitle: life is struggle //副标题
        description: life is struggle //描述
        author: examble #作者信息
        avatar: /images/avatar.png //头像，图片位置在相应主题目录下的images
        language: zh-Hans //中文简体
        email: 
        timezone:
        # Extensions
        theme: next //配置主题，这里使用next主题
        stylus:
        compress: true //自适应布局
        # Deployment
        deploy:
          type: git
          repository: git@github.com:Y-mzh/Y-mzh.github.io.git
          branch: master 
        ```
	7.**安装hexo-deployer-git插件**
		```
        npm install hexo-deployer-git --save
        ```
	8.**上传本地的主题到github上**
		```
        hexo clean
        hexo generator //简写 hexo g
        hexo deploy //简写 hexo d
        ```
        最后看下，部署到github上的效果！
        访问：https://y-mzh.github.io/