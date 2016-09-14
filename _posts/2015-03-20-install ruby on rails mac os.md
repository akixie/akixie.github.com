---
layout: post
title: "install ruby on rails mac os"
description: ""
comments: true
keywords: "ruby"
---


1. 安装ruby
https://ruby-china.org/wiki/rvm-guide

2. 安装ruby on rails
https://ruby-china.org/wiki/install_ruby_guide/

rails入门
http://guides.ruby-china.org/getting_started.html

rvm list known列出所有ruby版本

gem env 查看GEM环境

rvm reinstall ruby-2.0.0-p598 重新安装

ruby 升级1.8.7到1.9.3

rvm install ruby 1.9.3

ruby -v

如果还是1.8.7.

rvm use 1.9.3

列出所有版本

rvm list

设置默认的版本

rvm --default use x.x.x

rvm安装


$ curl -L get.rvm.io | bash -s stable
$ source ~/.bashrc
$ source ~/.bash_profile





修改 RVM 的 Ruby 安装源到国内的 淘宝镜像服务器，这样能提高安装速度


$ sed -i -e 's/ftp\.ruby-lang\.org\/pub\/ruby/ruby\.taobao\.org\/mirrors\/ruby/g' ~/.rvm/config/db





ruby的安装与切换

- 列出已知的ruby版本


rvm list known





- 安装一个ruby版本


rvm install 1.9.3





这里安装了最新的1.9.3, rvm list known列表里面的都可以拿来安装。

- 使用一个ruby版本


rvm use 1.9.3





如果想设置为默认版本，可以这样


rvm use 1.9.3 --default





- 查询已经安装的ruby


rvm list





- 卸载一个已安装版本


rvm remove 1.9.2



删除rvm


rvm implode





or


rm -rf ~/.rvm





删除 .bashrc and/or .bash_profile

用homebrew安装 rbenv
$ brew install rbenv
