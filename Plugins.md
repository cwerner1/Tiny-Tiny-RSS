Plugins
=======

Tiny Tiny RSS supports several kinds of plugins - social plugins which
enable sharing articles on various sites, article filter plugins which
mangle feed data on import (for example, inlining images or changing
content), hotkey plugins which alter the way keyboard shortcuts work,
etc.

There are two kinds of plugins: user and system. User plugins are
enabled in Preferences ~~\> Plugins. System plugins require adding them
to a <code>config.php</code> directive <code>PLUGINS</code> which is a
comma-separated list of enabled system plugins, i.e.

<code>define(’PLUGINS’, ’updater, digest, auth\_remote, auth\_internal, googlereaderimport’);\</code>

Installation of plugins is as simple as copying a folder into the
’plugins’ folder of your tt-rss and then activating (via a checkbox) it
in the settings panel.

If you add a user plugin to <code>PLUGINS</code> this will force enable
it for all users.

Themes and plugins are also available on the
[forum](http://tt-rss.org/forum/viewforum.php?f=22).

If you are interested in making plugins, see [MakingPlugins](MakingPlugins).

Since version version:1.7.5, the plugin architecture of tt-rss is pretty
stable. But for one or other reason, some plugins may profit if someone
agrees to maintain them. Plugin authors who agree to do that could post
a link to their github account or simply let us know that they are
available to be contacted in the forums or per email, then we’ll add
that information here.

If multiple search plugins are loaded, only the first one is used.

Several more plugins are available in the [contrib
repository](https://github.com/gothfox/Tiny-Tiny-RSS-Contrib/) including
example plugins to get you started making your own.

p{color:red}. Please note that we’re not responsible for third party
plugins. Use at your own risk.

Social plugins
--------------

### Share to Pinterest, Owncloud, Pocket, Twitter, Identica, Google+

Previously bundled in trunk.

http://tt-rss.org/forum/viewtopic.php?f=22&t=1548&p=7081

### Share to Evernote, Kindle and Pinboard

http://tt-rss.org/forum/viewtopic.php?f=22&t=1422

### Share to Facebook

http://tt-rss.org/forum/viewtopic.php?f=22&t=1486

### Share to Flattr

https://github.com/nhoening/ttrss-flattr

### Share to Instapaper, Facebook

http://tt-rss.org/forum/viewtopic.php?f=22&t=1401

### Share to Hootsuite

http://tt-rss.org/forum/viewtopic.php?f=22&t=1436

### Share to Tumblr

http://tt-rss.org/forum/viewtopic.php?f=22&t=1448

### Share to SemanticScuttle

http://tt-rss.org/forum/viewtopic.php?f=22&t=1347

### Share to Readability

http://tt-rss.org/forum/viewtopic.php?f=22&t=1600

### Send to Kindle with one click

http://tt-rss.org/forum/viewtopic.php?f=22&t=2839

Keyboard shortcut plugins
-------------------------

### Example plugin to base other shortcut plugins on

http://tt-rss.org/forum/viewtopic.php?f=22&t=1382

h2. Feed data manipulation plugins

### Enable embedded videos in feeds~~ videoframes

https://github.com/tribut/ttrss-videoframes

### Configurable plugin to replace an article stub by content from the linked URL’s page

https://github.com/mbirth/ttrss\_plugin-af\_feedmod

### Comic plugin Ctrl+Alt+Del & Superosity

http://tt-rss.org/forum/viewtopic.php?f=22&t=1526

### Comic plugin GU Comics, Married to the sea & Toothpaste for dinner

https://github.com/tribut/ttrss-comics

### Full Feed for many newspaper websites

http://tt-rss.org/forum/viewtopic.php?f=22&t=1539

### Cleanup Google News feed

http://tt-rss.org/forum/viewtopic.php?f=22&t=1606

### Enlarge images in Flickr feeds

http://tt-rss.org/forum/viewtopic.php?f=22&t=1612

### Lint/tidy plugin to repair invalid feeds

https://github.com/Churten/tt-rss-ff-xmllint

### Embed content from Tapastic rss streams

https://github.com/ldidry/af\_tapastic.git

### XML Start tag cleaner

http://tt-rss.org/forum/viewtopic.php?f=22&t=2626

### Faking of referral for images (anti hotlinking protection).

https://github.com/Alekc/af\_refspoof

API plugins
-----------

### getCompactHeadlines

Requested by the author of News+ (former GReader) Android app to allow
two way synchronization.

http://tt-rss.org/forum/viewtopic.php?f=22&t=2465&p=13986\#p13984

Other plugins
-------------

### Instapaper clean view plugin

http://tt-rss.org/forum/viewtopic.php?f=22&t=1452

### Plugin for Yourls

http://tt-rss.org/forum/viewtopic.php?f=22&t=1429

### Favicon badge plugin

http://tt-rss.org/forum/viewtopic.php?f=22&t=1373

### Open in background tab (Chrome/Opera only)

http://tt-rss.org/forum/viewtopic.php?f=22&t=1658

### Next-Prev Toolbar

Toolbar for easy access to feed functions

http://tt-rss.org/forum/viewtopic.php?f=22&t=1659

### On-demand generation of QR-Codes for each article (that does not depend on external service).

https://github.com/jonrandoem/ttrss-qrcode
