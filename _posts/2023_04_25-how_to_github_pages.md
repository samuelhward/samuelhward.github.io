---
layout: post
title: "How to github pages"
author: "Samuel Ward"
categories: thoughts
tags: [draft]
image: pic1.png
---

# How to make this blog

## Installation

Begin by installing Ruby, with Jekyll and Bundler


``` bash
sudo apt-get install ruby-full build-essential zlib1g-dev

echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

gem install jekyll bundler
```

[[1]](https://jekyllrb.com/docs/installation/ubuntu/)


OK, now realise that github pages only works with Ruby v2.7 since Jekyll 3 ... 

``` bash
gpg2 --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB

\curl -sSL https://get.rvm.io | bash -s stable

rvm install 2.7
```

[[2]](https://stackoverflow.com/questions/37315192/how-to-downgrade-ruby-version-on-ubuntu)
[[3]](https://rvm.io/)

But I run Ubuntu 22.04, which does not like RVM. Use rbenv instead.

``` bash
sudo apt install rbenv
rbenv install 2.7.0 # <--- failing here 

```

[[4]](https://github.com/rbenv/ruby-build/pull/1974#issue-1231997356)


## Theme

I use [millenial](https://github.com/LeNPaul/Millennial)

    