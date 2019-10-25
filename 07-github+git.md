## git

上传代码的工具

-   下载
-   安装 双击 一路 下一步
-   鼠标右键时 git bash here 说明安装成功

-   第一次安装 git 需要配置用户邮箱 和 用户名 (只需一次)

        -   右键 点击 git bash here 黑窗口打开(命令行)

        -   设置用户名
            git config --global user.name "John Doe"

        -   设置邮箱
            git config --global user.email "johndoe@example.com"

## GithHub

-   社区 全球程序员交友交流
-   仓库 仓库可以用来存放我们写的代码/项目,管理自己的代码
-   使用仓库功能,来管理我们的学习笔记
-   star 点赞

-   一个仓库通常对应电脑里的一个文件夹,这个文件夹里边的所有内容都会存在这个仓库里..注意

### 第一件事

-   新建仓库 点击右上角 + 号
-   上传代码 到这个仓库

#### 如何上传

-   进入你要上传的 那个文件夹 的内部 右键 点击 git bash here
-   git init 初始化这个文件(本地仓库)) 成功的标志 有一个 .git 的隐藏文件 (仓库只需初始化一次)
-   git add . (把这个仓库里的文件 添加到 暂存区)
-   git commit -m'提交描述' (把刚才新添加到暂存区的文件 提交到 本地仓库)

-   把本地仓库 同步更新到 远程 github 仓库
-   第一次 需要 将本地仓库 和 远程仓库 建立 联系 (本地仓库只能和一个远程仓库 建立联系)

    -   git remote add origin https://github.com/metro2703/z-note.git
    -   (git remote add origin 仓库地址)

-   git push origin master (同步代码 )

#### 第二次上传

工作区===>暂存区====>提交到本地仓库===>同步到远程仓库

-   git add .
-   git commit -m'提交信息'
-   git push origin master

#### 注意 不要再 github 远程仓库里边 修改任意一个文件
