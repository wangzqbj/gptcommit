# GPT Commit

有些时候，代码中可能会有一些临时提交，并不需要（或者时机未到)推送到上游（内部开发
分支，开源社区），这种时候，`commit message`往往是写给代码作者临时看的，很多情况下
代码作者本人会比较敷衍的写一点`commit message`，这种时候，不如将commit message委托给
AI生成

这是一个prepare-commit-msg的git hook脚本， 'git hook'特性可以使git在执行某些命
令时，调用一些自定义的脚本，本脚本是一个“提前准备commit message"的hook, 可以在
执行`git commit`后利用 AI(chatgpt)自动准备 `commit message`，使得在进入交互模式
之前，便准备好`commit message`，操作示例如
下：

[![gptcommit](https://asciinema.org/a/AcMRbMhggwfrx3pz4CLmwOLla.svg)](https://asciinema.org/a/AcMRbMhggwfrx3pz4CLmwOLla)

## 使用方法

```sh
GPTCOMMIT=1 git commit
```
只有在主动的传入`GPTCOMMIT`环境变量后，本脚本才会用AI生成`commit message`，也就
是说，若要想偷懒利用AI自助产生`commit message`， 命令是更长的，这是符合预期的😀。

## 安装方法

将 prepare-commit-msg 文件拷贝到工程的 .git/hooks/ 目录下
