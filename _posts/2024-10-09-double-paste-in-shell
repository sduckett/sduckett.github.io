---
layout: post
title: when pasting from the system clipboard happens twice
---

## Double Trouble

Imagine you're having trouble with a piece of software and have finally
found a post that describes your symptoms. The discussion of how to
debug it contains a sequence of commands to run from your shell, that
will help determine the root cause. As you copy the first, `DEBUG=true;
example-command -n 5 -vvv`, from the browser window and paste it in your
terminal, you realize something is wrong with your environment, because
the paste looks like this:

```
λ ~/ DEBUG=true; example-command -n 5 -vvv`DEBUG=true;
example-command -n 5 -vvv`
```

If it works once, it should work twice, but idempotency might be an
issue and we might not want side-effects. This was annoying on one
machine, bad on two, but usability-hell on three different machines.

## Debugging

1. try pasting into a plain bash shell
  - works fine.
2. try pasting into a plain zsh shell with no oh-my-zsh loaded
  - remove the symlink from .zshrc, and with no config, it works fine.
3. try pasting into a zsh shell with oh-my-zsh
  - breaks as expected.

OK, so it seems the reason I'm having trouble on all of my machines is
that I'm using Oh My ZSH on all of my machines. Where did this come from?

See also: https://github.com/ohmyzsh/ohmyzsh/issues/9562

## Fix

The issue is resolved on my machine by adding,

```shell
# See discussion of double-paste problem here:
# https://github.com/ohmyzsh/ohmyzsh/issues/9562
DISABLE_MAGIC_FUNCTIONS=true
```

to `~/.zshrc`, before loading oh-my-zsh.
