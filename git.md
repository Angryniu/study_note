## Git的基础命令

- git init                

  描述:初始化git          

  用途:工作区没有.git文件 就使用一次创建.git文件 才能进行后续操作

- git add [fileName]

  描述:将指定文件从工作区添加到缓存区，进行文件追踪

  用途:凡是没有进行过add操作 或者添加过之后 又修改的文件 都可以使用add进行添加

- git commit -m '描述信息'

  描述:将所有缓存区文件提交到本地库

  用途:每提交一次为一个版本。只有提交到本地库才能上传到远程仓库

- git status

  描述:查看工作区的文件状态

  用途:查看工作区的文件状态

- git reflog(使用 git log更详细)

  描述:查看历史记录

  用途:可以查看历史版本 当前的版本 以及提交的信息

- git reset --hard [version]

  描述:版本穿梭

  用途:穿梭到指定版本，文件内容也会还原

- git remote -v

  描述:查看远程连接仓库是否存在  不要-v 就显示名字不显示url

- git remote add [自定义名字] [url]

  描述: 配置远程仓库

- git remote rm name

  描述: 删除远程仓库

- git remote rename old_name new_name

  描述: 修改仓库名

- git push (-f) [仓库名字] 分支[master]

  描述: 推送到仓库   -f 强制推送

- git rm [fileName]  

  描述: 从暂存区和工作区删除此文件

- git rm -cached [fileName]
  
  描述: 仅删除缓存区

- git clone [url]

  描述: 克隆整个仓库

- git pull 主机名  分支名
 
  描述: 下拉仓库项目

## 分支

- git branch 分支名
  
  描述:创建分支

- git branch -v
  
  描述:查看分支

- git checkout 分支名

  描述:切换分支

- git merge 分支名

  描述:把指定的分支合并到当前分支上


## git系统

- git config -l
- git config --system --list
- git config -global --list
- git config --global user.name '名字'
- git config --global user.email '邮箱'
- ssh-keygen it rsa -C '邮箱'     生成ssh公钥
- ssh -T git@gitee.com   检查远程仓库是否畅通

## 文本指令

  vim  [fileName]    创建/修改文件信息

  ​      i   切换到插入模式    

  ​     esc  退出插入模式

  ​     :wq 保存并退出

  cat [fileName]   读取文件信息 

  