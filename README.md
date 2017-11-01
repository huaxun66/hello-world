1.注册账户以及创建仓库

     要想使用github第一步当然是注册github账号了。之后就可以创建仓库了（免费用户只能建公共仓库），Create a New Repository，填好名称后Create，之后会出现一些仓库的配置信息，这也是一个git的简单教程。

2.安装Git客户端

     github是服务端，要想在自己电脑上使用git我们还需要一个git客户端, 如何安装不同操作系统的 Git 客户端，参见：http://help.github.com/win-set-up-git/.
	 
	 Git客户端装好了，点击Git Bash进入git命令行，为了把本地的仓库传到github，还需要配置ssh key。

3.配置Git

    （1） 首先在本地创建ssh key；
	
    $ ssh-keygen -t rsa -C "huaxun1988@126.com"
	
    之后会要求确认路径（选默认就可）和输入密码，我们这使用默认的一路回车就行。成功的话会在C:/User/你的windows用户名/下生成.ssh文件夹，进去，打开id_rsa.pub，复制里面的key。
	回到github，进入Account Settings，左边选择SSH Keys，Add SSH Key,title随便填，粘贴key。
	
	注意: .ssh 文件夹下同时有 id_rsa 和 id_rsa.pub 文件（注意在开启后缀名的情况下），id_rsa 是置于本地机器的密钥，用于匹配置于服务器端的密钥文件 id_rsa.pub，这样才能建立 SSH 连接。

   （2）为了验证是否成功，在git bash下输入：
   
    $ ssh -T git@github.com 
	
    如果是第一次的会提示是否continue，输入yes就会看到：You’ve successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。
	
	（3）接下来我们要做的就是把本地仓库传到github上去，在此之前还需要设置username和email，因为github每次commit都会记录他们。
	
     $ git config --global user.name "Hua Xun" 
     $ git config --global user.email "huaxun1988@126.com"

4.下载

    cd到你的本地项目根目录下，执行git命令
	
	git clone https://github.com/huaxun66/hello-world
    
	 
5.提交、上传

   （1）建立git仓库 
   
    cd到你的本地项目根目录下，执行git命令（从github用git命令clone下来的项目已经包含了git仓库）
	
    git init
	
	查看修改文件
	
	git status

   （2）将项目的所有文件添加到仓库中
   
    git add .
	
    如果想添加某个特定的文件，只需把.换成特定的文件名即可

   （3）将add的文件commit到仓库
   
    git commit -m "注释语句"

   （4）去github上创建自己的Repository

   （5）将本地的仓库关联到github上
   
    git remote add origin https://github.com/huaxun66/hello-world

   （6）上传github之前，要先pull一下，执行如下命令：
   
    git pull origin master

   （7）也就是最后一步，上传代码到github远程仓库
   
    git push -u origin master
	
    执行完后，如果没有异常，等待执行完就上传成功了，中间可能会让你输入Username和Password，你只要输入github的账号和密码就行了
	
	
更多请参考：http://rogerdudler.github.io/git-guide/index.zh.html