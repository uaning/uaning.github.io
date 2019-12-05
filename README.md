# uaning.github.io

``` 
git init
git add -A
git commit -m "first commit"
git remote add origin https://github.com/uaning/uaning.github.io.git
git push -u origin master
``` 

## git 常用命令

### init
``` 
git init #初始化
``` 
### status
``` 
git status #获取状态
``` 
### add
``` 
git add file # .或*代表全部添加
git rm --cached <added_file_to_undo> # 在commit之前撤销git add操作
git reset head # 好像比上面git rm --cached更方便
```
### commit
```
git commit -m "message" #此处注意乱码
```
### remote
```
git remote add origin git@github.com:JSLite/test.git #添加源
```
### push
```
git push -u origin master # push同事设置默认跟踪分支  
git push origin master  
git push -f origin master # 强制推送文件，缩写 -f（全写--force）
```

#!/bin/bash
# 部署到 github pages 脚本
# 错误时终止脚本
set -e

# 删除打包文件夹
rm -rf public

# 打包。even 是主题
hugo -t even # if using a theme, replace with `hugo -t <YOURTHEME>`

# 进入打包文件夹
cd public

# Add changes to git.

git init
git add -A

# Commit changes.
msg="building site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# 推送到githu  
# nusr.github.io 只能使用 master分支
git push -f git@github.com:nusr/nusr.github.io.git master

# 回到原文件夹
cd ..
