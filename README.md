# git-fixup

Fighting the copy-paste element of your rebase workflow.

`git fixup <ref>` is simply an alias for `git commit --fixup <ref>`. That's
just a convenience feature that can be also be used to trigger tab completion.

The magic is in plain `git fixup` without any arguments.  It finds which
lines/files you have changed, uses git blame/log to find the most recent commits
that touched those lines/files, and displays a list for you to pick from. This
is a convenient alternative to manually searching through the commit log and
copy-pasting the commit hash.

<img src="https://cloud.githubusercontent.com/assets/484559/6431298/344ded94-c023-11e4-8b82-314387ceeee3.png" alt="git fixup" width="500px" />

## Install

On OS X you can install this script with **homebrew**

    brew install git-fixup

There is a package up on AUR for any arch linux users out there that can be
installed using **yaourt** or a similar tool

    yaourt git-fixup

For most other systems (as long as they include `install` and `make`) you can
install by cloning this repo and running make

    git clone https://github.com/keis/git-fixup.git
    cd git-fixup
    make install
    make install-zsh

Or if you don't want to deal with any of that you can simply download the
scripts in anyway you like and make sure to put the program and completion
script into your `$PATH` and `$fpath` respectively.

## Usage

For this tool to make any sense you should enable the `rebase.autosquash`
setting in the git config.


```bash
# Select the changes that should be part of the fixup.
$ git add -p

# Output a list of commits that the staged changes are likely a fixup of.
$ git fixup

# Create a fixup!-<commit> of the given ref. If you have installed the zsh script
# you can cycle through the list of fixup candidates with tab completion.
$ git fixup <ref>

# Commit rebased into the selected commit as a fixup.
$ git rebase -i ...
```

### Squashing

`git-fixup` also supports squashing commits when you pass the `-s` or
`--squash` command-line flag.  This is equivalent to using `git commit
--squash <ref>`.

    $ git fixup --squash <ref>

Squashing gives you the opportunity to edit the commit message before
the commits are squashed together.

## Tab completion

The suggestions for the tab completion is the suggested fixup bases as
generated by running the tool without any arguments.

To be able to tab complete the command itself add a line like this to your zsh
configuration::

    zstyle ':completion:*:*:git:*' user-commands fixup:'Create a fixup commit'


## Changelog

See [CHANGELOG.md](CHANGELOG.md)

## Authors

- Rickard Dybeck ([alde](https://github.com/alde))
- Cristiano Giuffrida ([cgiuffr](https://github.com/cgiuffr))
- David Keijser ([keis](https://github.com/keis))
- Tiago Ribeiro ([fixe](https://github.com/fixe))
- Joe Shaw ([joeshaw](https://github.com/joeshaw))
