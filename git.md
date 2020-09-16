# git

- 分布式版本控制系统

- git把内容按元数据方式

1. 存储配置本地用户名称以及地址

```
  $ git config --global user.name "..."
  $ git config --global user.email "..."
```

1. 查看配置信息

   ```
     $ git config --list
   ```

[git工作流程]: https://www.runoob.com/wp-content/uploads/2015/02/git-process.png

- git工作区：显示的工作目录
- git暂存区：stage或index
- git版本库：.git目录

1. 初始化（当前目录生成.git目录）

   ```
     $ git init
   ```

2. 在newrepo目录下生成.git目录

   ```
     $ git init newrepo
   ```

3. 提交文件

   ```
     $ git add .
     $ git commit -m "注释"
   ```

4. 克隆github仓库至本地

   ```
     $ git clone url
     git clone git@github.com:fsliurujie/test.git  --SSH协议、、速度较快
     $ git clone git://github.com/fsliurujie/test.git           --GIT协议
     $ git clone https://github.com/fsliurujie/test.git          --HTTPS协议
   ```

5. git基本操作

   [操作流程]: https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg

| 命令             | 说明                                 |
| :--------------- | :----------------------------------- |
| git add          | 添加文件到仓库                       |
| git status       | 查看状态、显示变更                   |
| git diff         | 比较文件                             |
| git commit       | 提交暂存区到本地仓库                 |
| git reset        | 回退版本                             |
| git rm           | 删除工作区文件                       |
| git mv           | 移动或重命名工作区文件               |
| git log         | 查看历史提交记录                     |
| git blame <file> | 以列表形式产看指定文件的历史修改记录 |
| git remote       | 远程仓库操作                         |
| git fetch        | 从远程获取代码库                     |
| git pull         | 下载远程代码并合并                   |
| git push         | 上传远程代码并合并                   |



- 分支管理

  | 命令                          | 说明               |
  | ----------------------------- | ------------------ |
  | git branch (branchname)       | 创建分支           |
  | git checkout (branchname)     | 切换分支           |
  | git merge                     | 合并分支           |
  | echo "# Garbage" >> README.md | 创建文件并添加信息 |
  | git branch -d (branchname)    | 删除分支           |
  |                               |                    |
  |                               |                    |

  


### git远程仓库(github)

[github流程]: https://www.runoob.com/wp-content/uploads/2015/03/Git-push-command.jpeg

#### 添加远程库

1. 生成SSH Key

   ```
     $ ssh-keygen -t rsa -C "邮箱"
   ```

2. 在.ssh文件夹下找到id_rsa.pub（公钥），复制里面的key

3. 在github上添加SSH Key

```
   $ mkdir runoob-git-test                        创建测试目录
   $ cd runoob-git-test/                            进入测试目录
   $ echo "# 菜鸟教程 Git 测试" >> README.md       创建README.md 文件并写入内容
   $ ls                                           查看目录下的文件
   README
   $ git init                                     初始化
   $ git add README.md                            添加文件
   $ git commit -m "添加 README.md 文件"             提交并备注信息
   [master (root-commit) 0205aab]                 添加 README.md 文件
    1 file changed, 1 insertion(+)
    create mode 100644 README.md                    提交到 Github
   $ git remote add origin    git@github.com:tianqixin/runoob-git-test.git
   $ git push -u origin master
```

#### git文件操作

```
  $ git mkdir 文件夹名 //创建文件夹
  $ git cd 文件夹名/   //进入文件夹
  $ git rm 文件名.格式 //删除文件
  $ git rm -r 文件夹名 //删除文件夹
```



#### git恢复删除文件

通过git status可查看文件是否已经添加至暂存区（红色为未添加）

1. 删除本地文件，但未添加至暂存区

   ```
     $ git checkout -- 文件名.格式
   ```

2. 删除本地文件，并且已添加至暂存区

   ```
     $ git reset HEAD 文件名.格式
     $ git checkout -- 文件名.格式
   ```

3. 从暂存区把删除操作提交到了本地git库（已经输入commit命令）则进行版本回滚

   ```
     $ git log //查看版本信息
     $ git reset --hard *.//选择ID前几位字符串
   ```

4. 删除操作已经推送至github

