title: neovim python YouCompleteMe 安裝紀錄
date: 2015-07-07 09:52:31
tags:
---

注意！不要用內建 python 安裝任何東西

我是全新安裝Mac OSX Yosemite、Xcode、Commandline Tools

### Homebrew

```bash
$ brew install python
$ pip install neovim --user

$ brew install python3
$ pip3 install neovim --user

$ brew tap neovim/neovim
$ brew install --HEAD neovim
```

### install YouCompleteMe with Vundle

```bash
$ cd ~/.vim/bundle/YouCompleteMe
$ ./install.sh --clang-completer

$ cd ~/.vim/tern_for_vim
$ npm i
```

不照這個步驟裝很容易失敗
