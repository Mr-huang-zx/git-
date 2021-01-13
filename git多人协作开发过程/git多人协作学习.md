### Github

    多人协作开发流程
    01.A创建本地仓库
    02.A在github创建远程仓库
    03.A将本地仓库推送到远程仓库
    04.B克隆远程仓库到本地开发
    05.B将本地开发的内容推送到远程仓库
    06.A将远程仓库的代码拉到本地仓库

##### 步骤
    01.git init 创建本地仓库
    02.git add 文件名
    03.git commit -m 提交内容
    04.在github中创建一个仓库
    05.git push 远程仓库地址 分支名称

##### 简单办法
    可以给远程仓库取别名
    git remote add origin  远程仓库地址    (origin是自定义的)

    以后再提交到远程仓库就不需要输入github账号密码
    window10把我们的密码保存在了
    电脑设置-搜索控制面板-右上角点击大图标-凭据管理器-windows凭据

    git push -u origin master

    总结:
        git push 远程仓库地址 分支名称
            简化:
                01.git remote add 别名(可以自定义) 远程仓库地址  (git remote add origin)
                02.git push 别名 分支名称(git push origin master)
            再简化:
                01.git push -u 别名 分支名称(git push -u origin master) -u表示下次可以直接使用git push
                02.直接使用git push

##### 从远程仓库拉去项目
    git clone 远程仓库地址

    B提交代码
    git add git.html

    git add .  将全部上传到暂存区
    git commit -m B第一次提交
    (B没有权限向A创建的仓库提交代码 需要A邀请程序员B称为项目的开发者)

    程序员A 在github中  Settings->Manage-access  邀请项目成员
    然后页面Copy invite link中有个邀请链接 发给B
    B登录github 在浏览器粘贴邀请链接接收邀请

    如果A B是同一台电脑 B需要在window10设置-控制面板-凭据管理器 删除A的账号 使用B账号

    B git push origin master  登录B账号密码 

##### 程序员A将最新版本拉去代码
    git pull 别名 分支名称  (git pull origin master)

    git pull origin master 和 git clone 远程仓库地址区别

    git pull 是在已经有仓库的基础上进行的拉去最新代码
    git clone 是没有本地仓库的基础进行,基本只使用一次
##### 注意
    如果远程仓库代码版本高于本地仓库 本地仓库是不能向远程仓库提交代码。必须先拉去远程仓库到本地再进行提交


##### 解决冲突
    A修改git.html后提交到远程仓库
    B修改git.html后提交报错

    B操作 git pull origin master  拉取最新代码 将冲突的地方(>>>   <<<  >>>) 删除保存后
    git add git.html 
    git commit -m 解决冲突
     再把本地仓库推送到远程就可以了

##### 向其他成语提交代码

    程序员C想贡献自己的一些代码给别人的仓库
        别人的github右上角上的Fork(相当于将程序员A创建的仓库复制一份并且放到程序员C中)
        C git clone 别人远程链接
        对对应文件作出修改后
        git add git.html 
        git commit -m 我是C提交带建议
        git push 别人远程链接 master
        到C自己的远程仓库
        输入账号登录

        然后点击github上方的Pull requests 中的New pull request
        添加修改主题 内容
        然后点击 Create pull request

        原作者中的Pull requests可以查看到C中传来的代码 下面也可以回复
        原作者在Commites和Files changed查看
        点击Conversation中的Merge pull request 合并到仓库

