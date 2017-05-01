---
layout: post
title: "How to serve github pages locally for any jekyll theme"
comments: true
description: "This post is intented to show how to serve static jekyll sites at local computers.."
keywords: "jekyll local development"
---


Hi all,

My new post will be about development in jekyll.
Jekyll is very simple and it doesnt need any database or comment moderation etc for cms.
It is a static site generation tool with simple markdown files.

<div class="divider"></div>

Jekyll is working with ruby.
Install ruby and try to see the output below.

```shell
D:\github\talipkorkmaz.github.io>ruby --version
ruby 2.3.3p222 (2016-11-21 revision 56859) [x64-mingw32]
```

if you don't get an valid response please download ruby first.

[ Ruby 2.3.3 ](https://rubyinstaller.org/downloads/)

Then you should get devkit of ruby.

[ For use with Ruby 2.0 and above x64 - 64bits only ](https://rubyinstaller.org/downloads/)

Download it and extract to a path.
###### Then execute the commands in order

1. Extract DevKit to path D:\Apps\Ruby\DevKit
2. cd D:\Apps\Ruby\DevKit
3. ruby dk.rb init
4. ruby dk.rb review
5. ruby dk.rb install
6. gem install rails -r

Now you are ready to access your jekyll site.

Let's clone some jekylle theme from jekylle theme sites.

You can find themes from [here](http://jekyllthemes.org/)

Choose of course an open source theme and fork to yourself in github.
Then clone to local.

After that If you dont have a GemFile in your repository, create a "GemFile" file and edit inside like below.

```ruby
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
```

Execute the command below.

```shell
bundle install
```

Now you can serve your static site with 

```shell
bundle exec jekyll serve
```

The output is : 

```shell
D:\github\talipkorkmaz.github.io>bundle exec jekyll serve
Configuration file: D:/github/talipkorkmaz.github.io/_config.yml
Configuration file: D:/github/talipkorkmaz.github.io/_config.yml
            Source: ./
       Destination: ./_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 1.312 seconds.
  Please add the following to your Gemfile to avoid polling for changes:
    gem 'wdm', '>= 0.1.0' if Gem.win_platform?
 Auto-regeneration: enabled for './'
Configuration file: D:/github/talipkorkmaz.github.io/_config.yml
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

You can access your site locally via http://127.0.0.1:4000/

Happy bloggin..

