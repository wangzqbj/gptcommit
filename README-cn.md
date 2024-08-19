# GPT Commit

## 工作流演示

在日常开发工作中，可能会有一些临时的未完全完成的代码，我们期望暂存到本地（以便回溯），而不提交到开发库，这个时候，我们就有可能多次
执行`git commit`, 而这种回溯往往都是即时的，这种情况下，我们一般不会“认真”写commit message, 而是简单几句话略过，但这种“不认真”的commit message可以借助AI来生成，另外，假如我们想要把自己的代码推送到开源社区的话，往往还需要把commit message翻译成英文，这个过程也可以借助AI

下面我们来看一下借助AI前后的操作演示, 从演示中可以看到，AI生成的commit message是比“不认真”的commit message要好的

### 操作演示

#### without AI

[![asciicast](https://asciinema.org/a/g3lJ9xOBm50V3GORK2odb8AhT.svg)](https://asciinema.org/a/g3lJ9xOBm50V3GORK2odb8AhT)


#### with AI

[![asciicast](https://asciinema.org/a/DX554ffxBoD4TH4WGjuagwPwU.svg)](https://asciinema.org/a/DX554ffxBoD4TH4WGjuagwPwU)



## prepare-commit-msg

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

### 使用方法

```sh
GPTCOMMIT=1 git commit
```
只有在主动的传入`GPTCOMMIT`环境变量后，本脚本才会用AI生成`commit message`，也就
是说，若要想偷懒利用AI自助产生`commit message`， 命令是更长的，这是符合预期的😀。

### 安装方法

将 prepare-commit-msg 文件拷贝到工程的 .git/hooks/ 目录下

```
pip install -r requirements.txt
```

### OpenAI 配置

需要在环境变量中配置`OPENAI_API_KEY`，如果你采用聚合代理的方式访问OpenAI, 则需要另外配置`OPENAI_API_BASE`

```sh
export OPENAI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxx"
export OPENAI_API_BASE="https://xxxxxxx"
```

## translate-commit

这是一个利用chatgpt将`commit message`翻译成英文的工具，可以将其放置到`~/.local/bin`， 在vim中可以采用下面的方法调用

```sh
:'<,'>!translate-commit
```

[![asciicast](https://asciinema.org/a/nIxUJa2yginj8zwnjTqwyli0a.svg)](https://asciinema.org/a/nIxUJa2yginj8zwnjTqwyli0a)

