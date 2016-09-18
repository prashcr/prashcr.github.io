---
layout:     post
title:      Asynchronous linting in Vim 8
date:       2016-09-18
summary:    Enjoy lag-free, IDE-like linting in vim
categories: productivity vim
---

Earlier this month, [Vim 8.0 was released](https://groups.google.com/forum/#!topic/vim_announce/EKTuhjF3ET0)

This release is the first major release in over 10 years, and brings several new features, most exciting of which
is asynchronous I/O support. Previously, you would use a plugin like [Syntastic](github.com/scrooloose/syntastic) that runs synchronously on buffer open, write or manually with a command like `:SyntasticCheck`, preventing you from doing anything else while the buffer is being linted. This is far from the linting experience that modern editors like Atom/Sublime/WebStorm provide, where linters are run in the background after text is typed without disrupting your flow. In fact, this was such a badly wanted feature that it was one of the reasons why the [NeoVim](https://neovim.io/) project came to be, among other things. 

Well today, you can enjoy the future in vim.

<script type="text/javascript" src="https://asciinema.org/a/86122.js" id="asciicast-86122" async data-t="05"
data-autoplay="0"></script>

I'm using the [ALE](http://github.com/w0rp/ale) plugin, which currently supports linters for JavaScript, Bash, Python, Ruby, with more in development. Documentation is a bit lacking at the moment, but you just need to install it with your package manager then make sure you have one of the supported linters available on your `$PATH`. 

Happy linting!
