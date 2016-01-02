Frequently Asked Questions
==========================

### I can't post issues on the tracker

This is working as intended, use the forums.

### But I want to fix stuff and post merge requests!

[Here's the relevant wiki page](HowToContribute)

### I’m on a shared hosting, and…

### I’m using some third-party package of tt-rss and/or a third party hosted service

If you didn’t download it yourself from this site and use it on your own
VDS, preferably using Git, nobody here cares about your problems.

Although we do have a [special
subforum](http://tt-rss.org/forum/viewforum.php?f=24) for people with
shared hosting related questions. You can try posting there.

### I’m using lastpass and stuff is broken

Lastpass arbitrarily breaks tt-rss forms preventing various stuff like
saving settings from functioning properly. Why? Ask lastpass developers.

See also:
http://tt-rss.org/forum/viewtopic.php?f=1&t=2060&start=15\#p17969

### I’m experiencing random failures / UI glitches (error codes 6 & 7)

Almost every time those are caused by malfunctioning and/or badly
written browser extensions. Always try opening tt-rss without browser
extensions running (i.e. separate Firefox profile, Chrome incognito
mode, etc). This way you will be able to figure out which extension
breaks things.

One of the extensions that causes such problems is Lastpass.

Also, see this forum thread:
http://tt-rss.org/forum/viewtopic.php?f=1&t=2060

### What should I use - MySQL or PostgreSQL?

PostgreSQL should give you much better performance, especially if you
tune it a bit.

See also: [this
thread](http://tt-rss.org/forum/viewtopic.php?f=1&t=2053&start=45#p11015)

### I need a URL I can call to subscribe to feed to integrate with some third party browser extension/application.

<code>SELF\_URL\_PATH/public.php?op=subscribe&feed\_url=%s﻿</code>

SELF\_URL\_PATH = http://your.ttrss.server/tt-rss/

### I need to get the number of unread articles in the simplest way.

([Forum thread](http://tt-rss.org/forum/viewtopic.php?p=415))

<code>SELF\_URL\_PATH/backend.php?op=getUnread&login=LOGIN</code>

No password required. In single user mode, use “admin” for login.

### I read this feed which goes through FeedBurner and it behaves strangely.

FeedBurner seems to discriminate against tt-rss for some reason.

See [this thread]()
http://tt-rss.org/forum/viewtopic.php?f=1&t=418&hilit=feedburner for
more information.

N.B. Real classy behavior there, Google. Thanks a lot!

### I have used the update daemon before, but switched away from it. However, the UI keeps nagging me about the daemon not running or not updating feeds or whatever.

Find and delete daemon lock file in <code>LOCK\_DIRECTORY</code>.
Usually, it’s <code>lock/update\_daemon.lock</code>. You can also remove
<code>update\_daemon.stamp</code>.

### I have questions about article purging / I don’t think purging works.

In short, you may and will see articles with date older than the cutoff
for purging. Here’s why:

1. Starred articles are not purged.
2. Purging is done based on article import date internal to tt-rss which
could be different from the date specified in the original feed (e.g.
article has date 01-01-1970, but it was imported today).
3. When tt-rss sees articles still exist in the feed it bumps the import
date because otherwise the articles will get purged and reimported
periodically causing annoyingly reappearing duplicates. This is mostly
relevant for rarely updated feeds.
4. Purging is performed when the feed is updated hence disabled updates
= no purging.

Please see these forum threads for more information:

-   http://tt-rss.org/forum/viewtopic.php?f=1&t=792
-   http://tt-rss.org/forum/viewtopic.php?f=9&t=560&p=2649&hilit=delete\#p2649

You can see article import date if you mouse over displayed date in
tt-rss web UI.

Related question:

### I like to manually archive or delete articles and I get duplicates. Why?

Because the articles are still in the feed and get imported again.

http://tt-rss.org/forum/viewtopic.php?f=1&t=2020&p=10635\#p10635

### Using Firefox, “OPML Import window” always visible in Preferences

Apparently it’s some addon or a browser setting problem, using clean
profile helps.

See also: \#649

### I'm having problems with tt-rss following HTTP redirects properly

This is a PHP/CURL problem. If you have open_basedir restrictions enabled, it forbids CURL from following
HTTP redirects altogether. Why? Ask PHP developers. Previously (before 4c467026), tt-rss used a very ugly 
hack to manually resolve 30x URLs if open_basedir was enabled, this is now removed.

So, it's either disabling open_basedir, disabling CURL, or living without HTTP redirects, the choice is yours.

Note that several tt-rss plugins depend on CURL so turning it off will effectively prevent them from working. Base functionality will not be affected.

### Embedded video doesn’t work properly in articles

What you’re looking for is [videoframes
plugin](http://tt-rss.org/redmine/projects/tt-rss/wiki/Plugins#Enable-embedded-videos-in-feeds-videoframes)

### I have HTTP authentication enabled and get “Your access level is insufficient to run this script” error on login

The problem is that if you have auth\_remote enabled in config.php
tt-rss tries to automatically log you in as the user specified by the
server using HTTP authentication, which may not have administrative
privileges. You will need to either temporarily disable auth\_remote
(replace it with auth\_internal in config.php), temporarily disable HTTP
authentication, or give yourself administrative permissions using the
SQL client:

    update ttrss_users set access_level = 10 where login = 'you';

### I’m having performance problems, why is tt-rss so slow?

Most likely you don’t have enough hardware for your requested amount of
feeds. Switch up to a faster VDS tier or use something else.

