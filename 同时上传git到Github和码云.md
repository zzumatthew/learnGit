# Git同时上传到Github和码云

> ❝
>
> `悟空`
> 种树比较好的时间是十年前，其次是现在。
> 自主开发了Java学习平台、PMP刷题小程序。目前主修`Java`、`多线程`、`SpringBoot`、`SpringCloud`、`k8s`。
> 本公众号不限于分享技术，也会分享工具的使用、人生感悟、读书总结。
>
> ❞

**「`前情提要`」**

我们都知道`github`和`码云`汇集了很多软件工程师/架构师在上面分享知识、交流代码，所以称作*知名男性交友网站*也不为过。

> ❝
>
> **「为什么要上传到两个仓库？」**
>
> 1.既然要交友，那当然得扩大点影响力，所以如果上传到了两个地方，那被浏览的几率肯定也会高一点。
>
> 2.github有很多时候打不开，难过😔，导致别人想访问也访问不了。
>
> 3.github自动生成的静态网站打开速度偶尔也很慢。不信您试试：点击下方的`阅读原文`。
>
> 4.gitee毕竟是国内的最厉害的远程代码管理平台，不论是访问速度还是影响力都不错，很多同学都会在gitee上搜开源项目。
>
> 5.git本来就支持上传到多个仓库，那我就来顺便学习一波git的远程仓库的命令。
>
> ❞

## **一、创建两个远程仓库**

在码云和github上创建两个一样的仓库.

![github仓库](http://cdn.jayh.club/blog/20200810/vOKm3Hf1JDTz.png?imageslim)

也可以通过导入的方式，如码云的仓库可以从github导入。

![码云的仓库从github导入](http://cdn.jayh.club/blog/20200810/VftfGuKytK3B.png?imageslim)码云的仓库从github导入

## **二、clone仓库**

先从github或gitee上clone仓库到本地

```
git clone git@github.com:Jackson0714/PassJava-Learning.git复制代码
```

## **三、移除现有仓库**

```
git remote rm origin复制代码
```

## **四、关联码云和github仓库**

### 4.1 关联GitHub的远程库

- ounter(line

```
git remote add github git@github.com:Jackson0714/PassJava-Learning.git复制代码
```

注意，远程库的名称叫github，不叫origin了。

### 4.2 关联码云的远程库

- ounter(line

```
git remote add gitee git@gitee.com:jayh2018/PassJava-Learning.git复制代码
```

### 4.3 查看关联的仓库

注意，远程库的名称叫gitee，不叫origin。

现在，我们用`git remote -v`查看远程库信息，可以看到两个远程库：

```
$ git remote -v复制代码gitee   git@gitee.com:jayh2018/PassJava-Learning.git (fetch)复制代码gitee   git@gitee.com:jayh2018/PassJava-Learning.git (push)复制代码github  git@github.com:Jackson0714/PassJava-Learning.git (fetch)复制代码github  git@github.com:Jackson0714/PassJava-Learning.git (push)复制代码
```

![mark](http://cdn.jayh.club/blog/20200810/dBGa37OJTgGr.png?imageslim)mark

## **五、推送到两个远程仓库**

### 5.1 用git命令推送

如果要推送到GitHub，使用命令： `git push github master` 如果要推送到码云，使用命令： `git push gitee master` 这样一来，本地库就可以同时与多个远程库互相同步。

### 5.2 用可视化工具推送

也可以用git可视化工具`TortoiseGit`上传

![用TortoiseGit工具选择所有仓库](http://cdn.jayh.club/blog/20200810/OQ3pmaepSOAu.png?imageslim)用TortoiseGit工具选择所有仓库

## **六、遇到的问题**

### 1.如果提示以下信息

```
The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.复制代码RSA key fingerprint is SHA256:xxx.复制代码Are you sure you want to continue connecting (yes/no/[fingerprint])?复制代码
```

直接输入yes

![mark](http://cdn.jayh.club/blog/20200810/wdB2VH7WxkO4.png?imageslim)mark

### 2.如果提示这个信息

```
To gitee.com:jayh2018/PassJava-Learning.git复制代码 ! [rejected]        master -> master (fetch first)复制代码error: failed to push some refs to 'git@gitee.com:jayh2018/PassJava-Learning.git'复制代码hint: Updates were rejected because the remote contains work that you do复制代码hint: not have locally. This is usually caused by another repository pushing复制代码hint: to the same ref. You may want to first integrate the remote changes复制代码hint: (e.g., 'git pull ...') before pushing again.复制代码hint: See the 'Note about fast-forwards' in 'git push --help' for details.复制代码
```

如果你本地的代码比gitee仓库里面的代码新，或者你就是想用本地代码覆盖gitee的代码，则可以强制推送

```
git push gitee master -f复制代码
```

![强制推送到远程分支](http://cdn.jayh.club/blog/20200810/ctzlMgeGvdSi.png?imageslim)

强制推送到远程分支