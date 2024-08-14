# GPT Commit

## prepare-commit-msg

Sometimes, there may be some temporary commits in the code that do not need to
be pushed to upstream (internal development branches or open-source community)
yet. In these cases, the 'commit message' is often written for the author's
temporary reference, and many times the author may write a rather hasty 'commit
message'. In such situations, it might be better to delegate the task of
generating commit messages to AI.

This is a prepare-commit-msg Git hook script. The 'git hook' feature allows Git
to invoke custom scripts when executing certain commands. This script serves as
a 'preparation for commit messages' hook, which automatically generates a
commit message using AI (ChatGPT) after executing `git commit`, ensuring that
the commit message is ready before entering interactive mode. Example of usage:

[![gptcommit](https://asciinema.org/a/AcMRbMhggwfrx3pz4CLmwOLla.svg)](https://asciinema.org/a/AcMRbMhggwfrx3pz4CLmwOLla)

### Usage

```sh
GPTCOMMIT=1 git commit
```
Only when the `GPTCOMMIT` environment variable is actively passed in, will this
script use AI to generate the `commit message`, which means, if you want to be
lazy and use AI to automatically generate `commit message`, the command is
longer, this is as expected 😀.

### Installation

Copy the prepare-commit-msg file to the project's .git/hooks/ directory.

```
pip install -r requirements.txt
```

### OpenAI Configuration

The `OPENAI_API_KEY` needs to be configured in the environment variables

```sh
export OPENAI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

## translate-commit

This is a tool that uses ChatGPT to translate commit messages into English. It
can be placed in `~/.local/bin`, and can be invoked in Vim using the command 
below.

```sh
:'<,'>!translate-commit
```

[![asciicast](https://asciinema.org/a/nIxUJa2yginj8zwnjTqwyli0a.svg)](https://asciinema.org/a/nIxUJa2yginj8zwnjTqwyli0a)
