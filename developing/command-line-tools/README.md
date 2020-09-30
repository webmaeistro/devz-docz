# [Tools and Practice](../README.md) / Command Line Tools

## Overview

This is a list of recommended tools used at Martin's experience to enhance productivity and
developer happiness.

You may also be interested in these other pages from the Martin's experience Standard Devz Processes:

- [docker](https://gitlab.com/webmaeistro/Engineering-Playbook/tree/master/developing/docker)
- [direnv](https://gitlab.com/webmaeistro/Engineering-Playbook/tree/master/developing/direnv)

## Terminal Emulators

- [iTerm2](https://iterm2.com/)

### Resources

#### iTerm2

##### Configuration

- [itermocil](https://gitlab.com/TomAnthony/itermocil) - Create pre-defined
  window/pane layouts and run commands in iTerm

## Shells

- bash
- zsh
- [fish](https://fishshell.com/)

### Resources

#### zsh

##### Frameworks

- [Oh My Zsh](https://ohmyz.sh/)
- [Prezto](https://gitlab.com/sorin-ionescu/prezto)

#### fish

##### Frameworks

- [Oh My Fish](https://gitlab.com/oh-my-fish/oh-my-fish)

##### Configuration

- [chruby-fish](https://gitlab.com/JeanMertz/chruby-fish) - Thin wrapper around
  `chruby` to make it work with the Fish shell

## File compression and archiving

- [unar](https://unarchiver.c3.cx/commandline) Universal unarchiver
- [zstd](https://facebook.gitlab.io/zstd/) Ridonkulously fast (de)compression algorithm

## git tools

- [tig](https://gitlab.com/jonas/tig) ncurses interface for git
- [gitlab-cli](https://gitlab.com/cli/cli) A `git` helper for gitlab specific operations from the command-line

## Colorizers

- [grc](https://korpus.juls.savba.sk/~garabik/software/grc.html) Generic colorizer.
  For example: `alias ping='\grc --stdout --stderr --colour=on ping'`
- [diff-so-fancy](https://gitlab.com/so-fancy/diff-so-fancy) Prettier colored diffs in git.
- [diffr](https://gitlab.com/mookid/diffr) Another colordiff alternative.
  For example: `git diff | diffr`

## Navigation

- [tmux](https://gitlab.com/tmux/tmux) Terminal multiplexer with client-server architecture.
  Can easily recover lost shell sessions with [tpm](https://gitlab.com/tmux-plugins/tpm), [tmux-resurrect](https://gitlab.com/tmux-plugins/tmux-resurrect) and (optionally) [tmux-continuum](https://gitlab.com/tmux-plugins/tmux-continuum)
- [ranger](https://ranger.gitlab.io/) An ncurses file manager with vim-like bindings
- [exa](https://the.exa.website/) An `ls` replacement with git integrations.
  For example: `alias ll='exa --long --header --git --links --group-directories-first --color-scale --time-style=long-iso'`

## Database access

- [pgcli](https://www.pgcli.com/) - CLI for Postgres with auto-completion and
  syntax highlighting.

## Data Manipulation

### JSON

- [jq](https://stedolan.gitlab.io/jq/)

## Document format conversion

- [dos2unix](https://waterlan.home.xs4all.nl/dos2unix.html) Efficient conversion of line terminators between DOS <-> Unix format
- [pandoc](https://pandoc.org/) Swiss-Army Knife of rich text document format conversion

## Plain text search tools

- [ripgrep](https://gitlab.com/BurntSushi/ripgrep) Stronger, faster, better grep.

## macOS system administration

- [mas](https://gitlab.com/mas-cli/mas) Control the Mac App Store from the command line

## Remote host administration

- [keychain](https://www.funtoo.org/Keychain) User-friendly front-end to `ssh-agent`
- [mosh](https://mosh.org/) Mobile-friendly `ssh` replacement that performs better on unreliable network connections.

## HTTP clients

- [httpie](https://httpie.org/)

## Terminal recording/sharing

- [asciinema](https://asciinema.org/) - record and share Terminal sessions as
  text that you can copy and paste.

## Learning/Debugging/Looking Things Up

- [howdoi](https://gitlab.com/gleitz/howdoi) - instant coding answers via the command line
- [tldr](https://tldr.sh/) - simplifies `man` with practical examples

## \*nix tools

- cal - quick monthly calendar view for the command line
