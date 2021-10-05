## 二、Git命令行操作

### 本地库操作

### 1、本地库初始化

* 命令：git init  

  注释：查看目录的命令有（与linux命令兼容）：

  	* ll                     列出当前目录
  	* ls -lA               带隐藏资源的
  	* ls -l | less       分屏查看

  注意：初始化后 .git 目录中存放的是本地库相关的子目录和文件，不要删除，也不要乱修改

### 2、设置签名

* 形式：
  * 用户名：jack
  * Email 地址：645698@qq.com

* 作用：区分不同开发人员的身份

* 解释：这里设置的签名和登录远程库（代码托管中心）的账户、密码没有任何关系。

* 命令

  * 项目级别/仓库级别：仅在当前本地库范围内有效（优先）
    * git config user.name jack
    * git config user.email 645698@qq.com
    * 信息保存位置：./.git/config
  * 系统用户级别：登录当前操作系统的用户范围
    * git config --global user.name jack
    * git config --global user.email 645698@qq.com
    * 信息保存位置：~/.gitconfig
  * 优先级别
    * 就近原则：项目级别优先于系统用户级别，二者都有时采用项目级别的签名
    * 如果只有系统用户级别的签名，就以系统用户级别的签名为准
    * 二者都没有不允许，会报错，不让提交

  注：* 使用 「cat .git/config 」 命令查看设置内容
  
  ​		* 设置公钥、私钥，在保存签名后，使用命令：ssh-keygen -t rsa -b 2048 -C "你自己的邮箱地址"          或者      ssh-keygen -t rsa -C "nideyouxiang@xxx.com" 
  
  ​		后，有两次确认每次提交/拉去数据时的密码（可以不填，空格回车即可），公钥/私钥一般保存在  C:/uesrs/administrators/          公钥：id_rsa.pub     私钥：id_rsa

### 3、具体操作命令

| 命令                          | 解释                                                         |          |
| ----------------------------- | ------------------------------------------------------------ | -------- |
| git status                    | 查看工作区、暂存区的一个状态；后面可以带参数                 | 状态查看 |
| vim good.txt                  | 文件存在的话，就是查看文件；没有就是创建文件                 |          |
| git add good.txt              | 将工作区新建/修改的文件提交到暂存区                          | 添加操作 |
| git rm --cached good.txt      | 将暂存区的文件删除，工作区的文件不会删除                     |          |
| git commit good.txt           | 将暂存区的文件提交到本地库；需要进入vim编辑器填写提交信息备注 | 提交操作 |
| git commit -m "xxxx" good.txt | 将暂存区的文件提交到本地库；xxx：提交到信息备注              |          |
| git log                       | 查看详细历史版本（多屏显示：空格向下翻页；b 向上翻页；q 退出） |          |
| git log --pretty=oneline      | 以一个好看的形式查看历史版本                                 |          |
| git log --oneline             | 以一个简介的方式查看历史版本（hash值只取了前面7位｜索引值的一部分）只能查看当前版本之前的版本 |          |
| git  reflog                   | 以步数的形式展示历史版本（有利于版本指针的移动）HEAD@{移动到当前版本需要多少步}。所有的都能显示 |          |
| git reset --hard [局部索引值] | 跳转到那一个版本。使用git reflog查看版本对应索引值的一部分   |          |
| git reset --hard HEAD^        | 后退一个版本。只能后退，^:表示后退一步。^^^:表示后退三步     |          |
| git reset --hard HEAD~3       | 后退三步。数字表示后退的步数。只能后退                       |          |
| git help reset                | 查看具体命令reset的文档（本地的文档）                        |          |
| git clean -n                  | 列出未跟踪文件和文件夹                                       |          |
| git clean -f                  | 不提出任何要求就强行删除和清洁未跟踪文件和文件夹             |          |
|                               |                                                              |          |

追加：vim编辑命令

​			set nu : 显示行号

### 4、reset 命令的三个参数对比

* --- soft 参数
  * 仅仅在本地库移动HEAD指针

* --- mixed 参数
  * 在本地库移动HEAD指针
  * 重置暂存区
* --- hard 参数
  * 在本地库移动HEAD指针
  * 重置暂存区
  * 重置工作区

### 

