显示name的方法：

```bash
git config user.name
git config --list
```

或者查看`~/.gitconfig`文件。

改名字：

```bash
git config --global user.name "Furzoom"
# or
vi ~/.gitconfig
```

如果不加`--global`就是修改当前仓库的下的配置。

```bash
git config user.name "Furzoom"
```

或者直接修改当前仓库的`.git/config`文件。

修改email，与上面是同样的操作，只不过需要将name换行email即可。

作者：[马 岩](http://furzoom.com/)（[Furzoom](http://furzoom.com/)） （http://www.cnblogs.com/furzoom/）
版权声明：本文的版权归作者与博客园共同所有。转载时请在明显地方注明本文的详细链接，未经作者同意请不要删除此段声明，感谢您为保护知识产权做出的贡献。