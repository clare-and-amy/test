# git

```shell
git diff 
git diff master origin/master --name-only
```

git revert xx
git revert HEAD // 回滚最新一次的提交记录
git revert HEAD^ // 回滚前一次的提交记录

 revert命令与reset命令不同，是生成一次新的commit冲抵原来的commit， reset直接删除某些commit的内容，而revert则是生成一次新的commit来回滚某些commit的内容。

```shell
git reset --hard HEAD^
git reset --hard HEAD~10
git reset --hard HEAD~10^
```

git reset --hard HEAD^ 回退到上一个版本，HEAD^表示当前版本的父版本，HEAD~10表示当前版本的第10个父版本，HEAD~1