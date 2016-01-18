---
layout: post
title: "Guide to IRC"
summary: "The IRC guide I wish I read earlier"
categories: productivity
comments: true
share: true
date: 2015-08-06T13:18:42+08:00
update_date: 2016-01-18
---

I myself only started using IRC a few weeks back, whenever I needed help. I just figured out things as they were needed, along the way. It would've certainly helped if I had an explanatory guide to follow at the time.

I don't want to write a full feature article on IRC, because it's already been covered pretty well by others. I suggest reading [this tutorial](http://code.tutsplus.com/tutorials/irc-is-back-heres-your-starter-guide--net-31369) first.

After reading that, here are some quick tips to jumpstart your experience.

* You can stick with Freenode and ignore the other networks for now, as it seems to be the most populated network for most topics.
* If you want to get started right away, the easiest way is to try [Freenode webchat](https://webchat.freenode.net/). All you need to enter is a nickname and which channel you'd like to join (e.g. #jquery, #rubyonrails, ##math).
* Most channels require authentication before you're allowed to speak. To do this, type `/msg nickserv register <password> <email>`. The nick you joined with will be registered to you with the password you specify, and a confirmation will be sent to your email.
* When you join the channel again, type `/msg nickserv identify <nick> <password>` to use your previously registered nickname.
* One of the most important settings you'll want to change is to [hide join/quit/part messages](http://wiki.xkcd.com/irc/Hide_join_part_messages), to avoid getting your screen getting flooded with useless messages.

Eventually, you'll want to download a real IRC client. I like to keep it old school with [irssi](https://irssi.org/), though I sometimes use [Limechat](http://limechat.net/mac/) as well. Google around and find something you like :)
