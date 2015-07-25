Support for mobile devices
==========================

There are several alternative UI perspectives for tt-rss which are
better served for mobile devices.

Mobile version using jQuery mobile by Matthieu Boinet
-----------------------------------------------------

This is currently recommended to use instead of <code>mobile/</code>.
See this URL for more information:
https://github.com/mboinet/ttrss-mobile

Forum thread: http://tt-rss.org/forum/viewtopic.php?f=10&t=1216

Native Android client for tablets and smartphones
-------------------------------------------------

http://tt-rss.org/redmine/projects/tt-rss-android/wiki

G2TT: google reader-like mobile UI
----------------------------------

Forum thread: http://tt-rss.org/forum/viewtopic.php?f=10&t=1823

Source: https://github.com/g2ttrss/g2ttrss-mobile

Digest mode for slate devices
-----------------------------

As of version:1.7.9 located in the [contrib
repository](https://github.com/gothfox/Tiny-Tiny-RSS-Contrib/tree/master/plugins/digest)

![](/redmine/attachments/161/digest_small.png)

Digest is the suggested reading mode for tablet devices. It is
accessible through tt-rss actions dropdown menu if enable digest plugin
in Preferences -\> Plugins.

Mobile version for Android and iOS devices (deprecated)
-------------------------------------------------------

As of version:1.7.9 located in the [contrib
repository](https://github.com/gothfox/Tiny-Tiny-RSS-Contrib/tree/master/plugins/mobile)

Please note that mobile/ is no longer actively developed and is
considered deprecated. It is available in version:1.7.6 as an
unsupported plugin which could be enabled in config.php.

Mobile version is an alternative web UI for tt-rss which is designed
specifically for mobile devices. Two versions of mobile UI are bundled
with tt-rss.

Requires WebKit to function properly. Should work on other devices as
long as you’re using a WebKit-derived browser. You can open it by
opening <code>mobile/</code> subfolder in your tt-rss instance. E.g.
<code>http://localhost/tt-rss/mobile/</code>.

It is based on iUI framework and looks like this:

![](/redmine/attachments/93/ScreenShot.png_small.png)
