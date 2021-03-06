---
description: Compose CLI reference
keywords: fig, composition, compose, docker, orchestration, cli, reference
title: Command-line completion
---

Compose comes with [command completion](http://en.wikipedia.org/wiki/Command-line_completion)
for the bash and zsh shell.

## Installing Command Completion

### Bash

Make sure bash completion is installed.

*  On a current Linux OS (in a non-minimal installation), bash completion should be
available.

*  On a Mac, install with `brew install bash-completion`.

Place the completion script in `/etc/bash_completion.d/`
(or `/usr/local/etc/bash_completion.d/` on a Mac):

```shell
sudo curl -L https://raw.githubusercontent.com/docker/compose/{{site.compose_version}}/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose
```

On a Mac, add the following to your `~/.bash_profile`:

```shell
if [ -f $(brew --prefix)/etc/bash_completion ]; then
. $(brew --prefix)/etc/bash_completion
fi
```

You can source your `~/.bash_profile` or launch a new terminal to utilize
completion.

If you're using MacPorts instead of brew you'll need to slightly modify your steps to the
following:

Run `sudo port install bash-completion` to install bash completion.
Add the following lines to `~/.bash_profile`:

```shell
if [ -f /opt/local/etc/profile.d/bash_completion.sh ]; then
    . /opt/local/etc/profile.d/bash_completion.sh
fi
```

You can source your `~/.bash_profile` or launch a new terminal to utilize
completion.

### Zsh

Place the completion script in your `/path/to/zsh/completion`, using e.g. `~/.zsh/completion/`:

```shell
$ mkdir -p ~/.zsh/completion
$ curl -L https://raw.githubusercontent.com/docker/compose/{{site.compose_version}}/contrib/completion/zsh/_docker-compose > ~/.zsh/completion/_docker-compose
```

Include the directory in your `$fpath`, e.g. by adding in `~/.zshrc`:

```shell
fpath=(~/.zsh/completion $fpath)
```

Make sure `compinit` is loaded or do it by adding in `~/.zshrc`:

```shell
autoload -Uz compinit && compinit -i
```

Then reload your shell:

```shell
exec $SHELL -l
```

## Available completions

Depending on what you typed on the command line so far, it will complete:

 - available docker-compose commands
 - options that are available for a particular command
 - service names that make sense in a given context (e.g. services with running or stopped instances or services based on images vs. services based on Dockerfiles). For `docker-compose scale`, completed service names will automatically have "=" appended.
 - arguments for selected options, e.g. `docker-compose kill -s` will complete some signals like SIGHUP and SIGUSR1.

Enjoy working with Compose faster and with less typos!

## Compose documentation

- [User guide](index.md)
- [Installing Compose](install.md)
- [Get started with Django](django.md)
- [Get started with Rails](rails.md)
- [Get started with WordPress](wordpress.md)
- [Command line reference](./reference/index.md)
- [Compose file reference](compose-file.md)
