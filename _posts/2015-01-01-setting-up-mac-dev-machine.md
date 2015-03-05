---
layout: post
title: Setting up your Mac Dev Machine
categories:
- blog
---

> Work in progress (WIP)

sync dotfiles with dropbox

bash script to symoblic link all your files

http://support.apple.com/kb/PH14243
https://gist.github.com/zenorocha/7159780
http://mattstauffer.co/blog/setting-up-a-new-os-x-development-machine-part-2-global-package-managers
http://robots.thoughtbot.com/brewfile-a-gemfile-but-for-homebrew


##Setting up Xcode
install command line tools
http://stackoverflow.com/questions/9329243/xcode-4-4-and-later-install-command-line-tools

##Setting up Iterm2
***
not needed
http://zanshin.net/2013/09/03/how-to-use-homebrew-zsh-instead-of-max-os-x-default/
http://johndjameson.com/blog/updating-your-shell-with-homebrew/

/etc/shells
```
# List of acceptable shells for chpass(1).
# Ftpd will not allow users to connect who are not using
# one of these shells.

/bin/bash
/bin/csh
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
/usr/local/bin/fish
/usr/local/bin/zsh
```
***

1. install oh-my-zsh https://github.com/robbyrussell/oh-my-zsh
`curl -L http://install.ohmyz.sh | sh`
2. Pick color theme
Download zip from http://iterm2colorschemes.com/. Navigate to `schemes` download whichever iterm color you like
I use `Monokai Soda.itermcolors`
3. popup iterm2 window
4. Add Go2Shell. Open a terminal in folder in finder.
`open -a Go2Shell --args config` set to iterm2
5. Install sublime text package terminal (not working)
6. Enable new tab is in same directory instead of home
7. Enable tab close buttons
8. skip by word. https://coderwall.com/p/h6yfda/use-and-to-jump-forwards-backwards-words-in-iterm-2-on-os-x

powerline
https://github.com/powerline/powerline/issues/552

```
error: can't combine user with prefix, exec_prefix/home, or install_(plat)base
```

###Setup SourceTree
great git visualizer.

More comprehensive than gitx
Get the command line tool `stree` and do `stree .` which works on a local git repository to see a visual git history.

##Setting up Sublime Text 3

mac add `subl` command line
`ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/`

http://stackoverflow.com/questions/25152711/subl-command-not-working-command-not-found

press esc to exit when it asks you to pay. No need to click it.


Sublime Text 3 Plugins

https://packagecontrol.io/installation

##Plugins
"AlignTab",
"ApplySyntax",
"ColorPicker",
"CSS Extended Completions",
"CSS3_Syntax",
"DashDoc",
"Emmet",
"GitGutter",
"GitStatus",
"LaTeXTools",
"LineEndings",
"Markdown Preview",
"MarkdownEditing",
"More Layouts",
"NASM x86 Assembly",
"Package Control",
"Predawn",
"Pretty JSON",
"SideBarEnhancements",
"Sublimerge Pro",
"Table Editor",
"Terminal",
"TrailingSpaces"


Sublime Text > Preferences > Setting - User
~~~
{
    "detect_slow_plugins": false,
    "enable_table_editor": true,
    "findreplace_small": true,
    "font_size": 14,
    "ignored_packages":
    [
        "Vintage",
        "Markdown",
        "LaTeXTools",
        "Markdown Preview"
    ],
    "sidebar_xsmall": true,
    "tab_size": 2,
    "table_editor_syntax": "MultiMarkdown",
    "tabs_small": true,
    "theme": "predawn.sublime-theme",
    // "theme": "Flatland Dark.sublime-theme",
    "translate_tabs_to_spaces": true
}
~~~~

Sublime Text > Preferences > Key Binding - User
~~~
[
    { "keys": ["command+/"], "command": "toggle_comment", "args": { "block": false } },
    { "keys": ["command+shift+/"], "command": "toggle_comment", "args": { "block": true } },
    { "keys": ["alt+g"], "command": "markdown_preview", "args": {"target": "browser", "parser":"GFM"} },
    { "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} },
    { "keys": ["command+shift+["], "command": "open_mac_terminal" },
    { "keys": ["command+shift+m"], "command": "delete_trailing_spaces" },
    { "keys": ["command+shift+r"], "command": "goto_symbol_in_project" },
    {
    "command": "goto_definition",
    "keys": ["option+command+up"]
    },
]
~~~

##Setting up Homebrew

###Install command line applications

~~~
brew tap homebrew/boneyard

Add this line to `.zshrc`, `export HOMEBREW_CASK_OPTS="--appdir=/Applications"`

brew bundle
~~~

apple-gcc42     cairo           gdk-pixbuf      icu4c           mongodb         pixman          ruby-build
asciidoc        ctags           gettext         jpeg            nasm            pkg-config      sqlite
atk             docbook         git         libcaca         node            postgresql      the_silver_searcher
autoconf        fish            glib            libffi          openssl         python          toilet
bash-completion fontconfig      glibmm          libpng          ossp-uuid            python3         tree
bdw-gc          freetype        gobject-introspection   libsigc++       pango           rbenv           xz
brew-cask       gdbm            harfbuzz        libtiff         pcre            readline        zsh

mongo
git
zsh
python3
ruby-build
the_silver_searcher
rbenv
tree
node

###Install other applications

https://github.com/caskroom/homebrew-cask

`brew cask list`
`brew cask cleanup`

where cask install applications are stored `/opt/homebrew-cask/Caskroom`

Add this line to `.zshrc`, `export HOMEBREW_CASK_OPTS="--appdir=/Applications"`
this will make cask create the symbolic links in the `/Applications` instead of the default `~/Applications`

restart terminal for changes to .zshrc to take effect

https://github.com/caskroom/homebrew-cask/blob/master/USAGE.md


~~~
Warning: brew-cask-0.52.0 already installed
==> Downloading http://download.lightheadsw.com/download.php?software=caffeine
######################################################################## 100.0%
==> It seems there is already an App at '/Applications/Caffeine.app'; not linkin
🍺  caffeine staged at '/opt/homebrew-cask/Caskroom/caffeine/1.1.1' (13 files, 416K)
Warning: A Cask for flux is already installed. Add the "--force" option to force re-install.
==> Downloading https://github.com/downloads/fikovnik/ShiftIt/ShiftIt-develop-1.
######################################################################## 100.0%
==> It seems there is already an App at '/Applications/ShiftIt.app'; not linking.
🍺  shiftit staged at '/opt/homebrew-cask/Caskroom/shiftit/1.6' (119 files, 1.9M)
==> Downloading http://marked2app.com/download/Marked.zip
~~~

By making the symbolic link location the same as where mac applications are installed. cask knows not to install it if it's already installed.

run this magic line
`brew update && brew upgrade brew-cask && brew cleanup && brew cask cleanup`

##Setting up dotfiles

Git
http://gitimmersion.com/

~~~
[user]
    name = Jimicy
    email = jimmy_wang1995@hotmail.com
[core]
    excludesfile = /Users/Jimmy/.gitignore_global
    editor = subl -n -w
    autocrlf = false
    safecrlf = true
[difftool "sourcetree"]
    cmd = opendiff \"$LOCAL\" \"$REMOTE\"
    path =
[mergetool "sourcetree"]
    cmd = /Applications/SourceTree.app/Contents/Resources/opendiff-w.sh \"$LOCAL\" \"$REMOTE\" -ancestor \"$BASE\" -merge \"$MERGED\"
    trustExitCode = true
[color]
    ui = true

[alias]
  co = checkout
  ci = commit
  st = status
  br = branch
  hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
  type = cat-file -t
  dump = cat-file -p
[help]
    autocorrect = 1
[credential]
    helper = osxkeychain
[push]
    default = simple
~~~

https://help.github.com/articles/caching-your-github-password-in-git/

zshrc
```

```

##Mac shortcuts
Screenshot cmd+shift+4
Screenshot application with shadow cmd+shift+4+space

Text manipulation
CMD + arrow [go to left/right end of line]
option + arrow [go by word separated by delimiter]