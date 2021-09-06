# Git基本用法

#   一. Git诞生背景

## 版本控制

版本控制（Version Control）是一种记录文件内容变化，以便将来查阅特定版本修订情况的系统, 可在软件开发的过程中，确保由不同人编辑的同一程序文件都得到同步。

## 分布式版本控制系统 VS 集中化版本控制系统

- 集中化版本控制（Svn）

  集中管理服务器，所有人直接连接该服务器，拉取最新代码，提交自己更新。所有数据保存在集中管理服务器。

- 分布式版本控制（Git）

  代码仓库完整克隆。每个人的仓库都是服务器，多人之间交换数据，达到统一版本控制。

## Git开发历史

- 集中化版本控制（Svn）

  集中管理服务器，所有人直接连接该服务器，拉取最新代码，提交自己更新。所有数据保存在集中管理服务器。

- 分布式版本控制（Git）

  代码仓库完整克隆。每个人的仓库都是服务器，多人之间交换数据，达到统一版本控制。

## Git重要概念

### 仓库

本地仓库：个人仓库，文档修改等操作

​                          |

​                        clone

​                          |

个人远端仓库：个人仓的远端保存，只有自己有权限

​                          |

​                        fork

​                          |

统一远端仓库：所有开发人员只有读取权限，管理员有所有权限

### 分支

Git的分支功能支持同时进行多个功能的开发和版本管理。在数据库进行最初的提交后, Git会创建一个名为master的分支。因此之后的提交，在切换分支之前都会添加到master分支里。

- 分支之间相互隔离，互不影响。
- 切换到指定分支，只会展示当前分支的文件，不属于该分支文件不可见。
- 可通过合并将分支内容进行归一化处理。

#   二. Git安装及初信息配置

## 1. 安装客户端

1. 通过Git官网，选择电脑适配版本Git，安装git客户端（<http://www.git-scm.com/download/win>）。

## 2. 个人信息配置

1. 注册gitee账号 （https://gitee.com/）。

2. 空白位置鼠标右键，打开Git Bash Here。

3. 打开的黑色背景窗口，输入 **cd ~/.ssh**，进入密钥存储目录。

4. 继续输入 **ssh-keygen -o** 遇到需要需要输入密码时，直接回车，直到出现 $符号。

   ###### ![Git 1](git-basics images\Git 1.PNG)

5. 继续输入  **cat ~/.ssh/id_rsa.pub**。

6. 拷贝**ssh-rsa** 开始到 个人邮箱结尾的文字。

   ###### ![Git 2](git-basics images\Git 2.PNG)

7. 登录Git管理后台，**个人头像->设置->SSH秘钥->添加秘钥**，拷贝至输入框，保存。

   ###### <img src="git-basics images\Git 3.PNG" alt="Git 3" style="zoom: 50%;" />

## 3. 初始化仓库

- Fork远端仓库到个人远端仓库

选择一个远端仓库，点击左上角fork按钮。

###### <img src="git-basics images\Git 4.PNG" alt="Git 4" style="zoom: 67%;" />

- 克隆到个人本地仓库

进入个人远端仓库，左上角有**克隆/下载**按钮，点击下三角，选择用SSH克隆（默认选中），点击复制按钮

在需要保存仓库文件的目录下，鼠标右键单击，打开Git Bash Here，输入 git clone 拷贝内容。

###### <img src="git-basics images\Git 5.PNG" alt="Git 5" style="zoom:80%;" />

###### ![Git 6](git-basics images\Git 6.PNG)

## 4. 个人本地仓库配置

- 配置远端仓库

进入仓库目录，打开git bash客户端。

进入统一远端仓库，点击**克隆/下载**按钮下三角->复制图标，复制统一仓库地址。

###### <img src="git-basics images\Git 5.PNG" alt="Git 5" style="zoom:80%;" />

Git bash 客户端输入 **git remote add upstream** 统一仓库地址。

输入 **git remote -v**, 查看远端仓库配置信息。

###### ![Git 7](git-basics images\Git 7.PNG)

# 三. 提交文件

1. 在个人本地仓库存储文件夹下新增一个待提交文件。
2. 将待提交文件纳入个人本地仓库版本管理内。

​      目录下打开git bash 客户端，输入**git add** 文件名。

3. 将该文件提交至个人本地仓库。

​      目录下打开git bash 客户端，输入**git commit**，会提示输入版本说明信息  ，输入i开始进行版本信息说明，输入后按esc并输入**:wq**确认提交。

4. 个人本地仓库信息推送至个人远端仓库。

  目录下打开git bash 客户端，输入**git push origin master**。

5. 在服务器上创建merge request。

  个人远端仓库，选择合并请求页签，点击新建，源分支选择个人远程仓库  ，目标分支选择同一远端仓库。

#   四. Git工具 —— TortoiseGit

- 下载安装TortoiseGit  [https://tortoisegit.org/download](https://tortoisegit.org/download/)[/](https://tortoisegit.org/download/)

- 克隆个人远端仓库 空白处鼠标右键，选择**Git Clone**。

  ###### ![Git 8](git-basics images\Git 8.PNG)

- **URL**: 输入个人远端仓库复制的地址，Directory输入。

  想要保存仓库文件的目录，点击**OK**。

  ###### <img src="git-basics images\Git 9.PNG" alt="Git 9" style="zoom:80%;" />

- 进入保存仓库文件的目录，该目录下添加文件。

- 选中该文件并鼠标右键，加入本地管理。

- 仓库目录下空白处鼠标右键单击，选择**Git commit->master**。

  ###### <img src="git-basics images\Git 10.PNG" alt="Git 10" style="zoom:80%;" />

  ###### <img src="git-basics images\Git 11.PNG" alt="Git 11" style="zoom:80%;" />

  ###### <img src="git-basics images\Git 12.PNG" alt="Git 12" style="zoom:80%;" />

- 仓库目录下空白处，鼠标右键单击，选择**TortoiseGit->push**，选择远端分支 。

  ###### <img src="git-basics images\Git 13.PNG" alt="Git 13" style="zoom:80%;" />

  注：此部分图源网络，详见 https://www.softwaretestinghelp.com/tortoisegit-tutorial/。

# 五. 冲突解决

- 提交前必须拉取远端分支，拉取远端分支失败则存在冲突，需要按照以下方式解决。

  1. 将本地修改进行stash，进入仓库目录，git bash内输入**git stash**。
  2. 再次拉取远端分支 **git pull origin master**。
  3. 将本地存储的内容从stash pop出来，  git bash内输入**git stash pop**。
  4. 使用工具或命令行，寻找解决conflict文件。
  5. 工具比对conflict文件，解决冲突位置并保存。
  6. 正常提交，并将stash内容删除 **git stash clear** 。

#  六. Git 常用命令

| 命令名称                           | 作用                         |
| ---------------------------------- | ---------------------------- |
| git init                           | 初始化本地库                 |
| git status                         | 查看本地库状态               |
| git add 文件名                     | 添加文件到暂存区             |
| git reflog                         | 查看历史记录                 |
| git reset –hard 版本号             | 版本穿梭                     |
| git branch 分支名                  | 创建分支                     |
| git branch -v                      | 查看分支                     |
| git checkout 分支名                | 切换分支                     |
| git merge 分支名                   | 把指定的分支合并到当前分支上 |
| git clone 远程地址                 | 克隆远程仓库到本地           |
| git pull 远程库地址别名 远程分支名 | 拉取远程库内容               |
| ...                                | ...                          |

