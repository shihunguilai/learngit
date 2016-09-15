#git的使用
[toc]
##1.安装git
`sudo apt install git`

##2.git的设置
```shell
git config --global user.name "your name"
git config --global user.email "your email"
git config --list
```

##3.在本地建立仓库
```shell
mkdir learngit
cd learngit
git init
touch readme.txt #建立测试文件
vim readme.txt #输入测试内容

把文件加入仓库
git add readme.txt

把文件提交到仓库
git commit -m "sth."

修改readme.txt
vim readme.txt

查看仓库当前的状态
git status

查看文件的修改内容
git diff readme.txt

提交修改
git commit -m "sth."

显示提交的历史记录
git log
git log --pretty=oneline #一行显示

```

##4.git版本重置、回退

###版本回退

head表示当前版本
head^表示上一个版本
head^^表示上两个版本
head~100表示当前往上100个版本

用git log查看提交历史，以便会退到某个版本

用git reflog查看命令历史，可以回到未来的哪个版本

重置到某一个版本
git reset --hard commit_id

查看工作区和版本库里最新版的区别：
git diff HEAD -- readme.txt


###管理修改
git管理的是修改，不是文件
git add file  #把工作区文件修改提交到暂存区stage
git commit -m 'commit desc word' #把暂存区修改提交到分支上




###撤销修改
修改了工作区的文件内容，没有添加到暂存区，想直接丢掉修改
git checkout -- filename

修改了工作区的文件内容，并且添加到了 暂存区，想丢掉修改，要2步
git reset head file  #撤掉暂存区修改到工作区
git checkout -- file #撤掉工作去修改


###删除文件
在工作去新建test.txt文件
```shell
touch test.txt
git add .
git commit -m "sth."
```
要删除版本库中的文件 
git rm/add test.txt
git commit -m "remove sth."

删错了，因为版本库还有，可以吧误删的文件到最新版
git checkout -- test.txt

git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”

##5.远程仓库

- 创建ssh key	`ssh-keygen -t rsa -C "your email@xx.com"`
- 把 ~/.ssh/id_rsa.puh 文件的内容 添加到 github 上面的 add ssh key
- 测试是否 添加成功	`ssh -T git@github.com`

- 在github上建立learngit仓库

##6.关联本地仓库

    git remote add  origin  git@github.com:shihunguilai/learngit.git
	git remote set-url origin git@github.com:shihunguilai/learngit.git
    git pull  origin master 
    git push  origin master

	









