---
layout: post
title: "How to make this blog"
author: "Samuel Ward"
categories: thoughts
tags: [draft]
image: shutters.jpg
---

# How to github pages

## Introduction

Warning: there is currently a big mess in how this stuff is installed if you're running Ubuntu. I show a work around here - hopefully the community will sort it soon. Make sure to _read_ the [Installation](#introduction) section first _before_ beginning - do not just start following the commands.

## Installation

Begin by installing Ruby, with Jekyll and Bundler. Definitely do these first steps.

``` bash
sudo apt-get install ruby-full build-essential zlib1g-dev

echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

gem install jekyll bundler
```

[[1]](https://jekyllrb.com/docs/installation/ubuntu/)


OK, now I realised that github pages only works with Ruby v2.7 since latest Jekyll and Ruby do not get along...so originally I thought I could get around this using a Ruby version manager: 

``` bash
gpg2 --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB

\curl -sSL https://get.rvm.io | bash -s stable --auto-dotfiles

rvm install 2.7
```

[[2]](https://stackoverflow.com/questions/37315192/how-to-downgrade-ruby-version-on-ubuntu)
[[3]](https://rvm.io/)

...but I run Ubuntu 22.04, which uses OpenSSL 3.0 which does not like Ruby 2.7. The only fix has been implemented via rbenv [[here]](https://github.com/rbenv/ruby-build/pull/1974#issue-1231997356), so then I tried using that instead:

``` bash
sudo apt install rbenv
rbenv install 2.7.0 # <--- this failed here 

```

OK so instead, I finally went back to RVM; It turns out you can just install a new version of Ruby and use the working version of OpenSSL within it.

```bash
rvm pkg install openssl
rvm install 2.7.6 --with-openssl-dir=$HOME/.rvm/usr
bundle install
/bin/bash --login # at this point, need to enter a login shell 
rvm use 2.7.6 
ruby -v # check which version is activated 
bundle exec jekyll serve
# navigate to http://localhost:4000/ to see your blog!
```

[[4]](https://stackoverflow.com/questions/72179373/cant-install-ruby-via-rvm-error-running-rvm-make-j4-on-ubuntu-22-04)[[5]](https://rvm.io/rvm/basics)

So when you want to write new posts and display the results locally, just write stuff then run:

```bash
/bin/bash --login # at this point, need to enter a login shell 
rvm use 2.7.6 
bundle exec jekyll serve
```

Phew.

## Theme

I use [millenial](https://github.com/LeNPaul/Millennial).

    