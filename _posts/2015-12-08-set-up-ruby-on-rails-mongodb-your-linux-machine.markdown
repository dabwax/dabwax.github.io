---
layout: post
title:  "AYWAROR - Set up Ruby on Rails 4 and MongoDB in your Linux Machine"
date:   2015-12-08 10:40:51 -0200
categories: ruby rails guide ayawaror
---
## Introduction

You have so many ways to install the *Ruby* and the *Rails* gems.

I'll talk here about my preferred one: The **[RVM](http://rvm.io/)**. Is a *CLI* which allows you to easily install, manage and work with multiple ruby environments. In this way, this tool makes the installation step pretty easy.

This step-by-step works well on *Ubuntu* distro, but will work fine in any Linux distro.

## Installing Ruby and Rails

* Install RVM:
{% highlight shell %}
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
$ \curl -sSL https://get.rvm.io | bash -s stable
$ source ~/.rvm/scripts/rvm
{% endhighlight %}

* You can append "--ruby --rails" to install the latest versions from these. But we will try another approach:

* Run `rvm list known` to discover the current rubies available. Actually, the current version is 2.2-head.

* Run `rvm install 2.2-head`. It will install the Ruby 2.2 and all dependencies.

* Run `rvm use 2.2-head --default`. To set 2.2 as default version.

* Now install the Rails: `gem install rails`.

## Check if everything is okay
* To check-up all things is working fine:

{% highlight shell %}
// To get current Ruby version
$ ruby -v

// To get current Rails version
$ rails -v

// To discover where the bin of ruby is localizated:
$ which ruby
{% endhighlight %}

Now you have Ruby and Rails on latest verions available in your machine. Congratulations!

## Installing MongoDB

MongoDB is the NoSQL Database layer that we will use in our application.

* Import MongoDB public key into your package management system:
{% highlight shell %}
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
{% endhighlight %}

* Create a list file for MongoDB
{% highlight shell %}
$ echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list
{% endhighlight %}

* Now reload the package database:
{% highlight shell %}
$ sudo apt-get update
{% endhighlight %}

* Now install MongoDB with apt:
{% highlight shell %}
$ sudo apt-get install -y mongodb-org
{% endhighlight %}

* Create the folder where data will be storaged:
{% highlight shell %}
$ sudo mkdir /data/db
{% endhighlight %}

* Now we can start the MongoDB service:
{% highlight shell %}
$ sudo service mongod start
{% endhighlight %}

**Congratulations**! Now you have *Rails* and *MongoDB* installed on the best way! It will work fine as fuck.

In the next topic, i will explain about generating a new application with Rails console and with MongoDB as default ORM.

Thanks for you attention,
Cheers.