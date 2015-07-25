Making plugins
==============

Sorry, plugin API documentation is not written yet. You can use example
plugins bundled with tt-rss and other finished plugins as a starting
point. Ask on the [forums](http://tt-rss.org/forum/viewforum.php?f=22)
if you need help.

Plugins may render new preference panes or embed themselves into several
existing one, store data using simple key -\> value data or directly in
the database, modify how articles are rendered, alter feed data, and
many more things.

List of hooks you can use is available in
<code>classes/pluginhost.php</code>.

Due to API changes in version:1.7.9 your plugin will need to be updated,
please see [this
thread](http://tt-rss.org/forum/viewtopic.php?f=1&t=1859&p=9279#p9279)
for more

Example plugins are available in the [contrib
repository](https://github.com/gothfox/Tiny-Tiny-RSS-Contrib/).

Javascript hooks are available since version:1.7.9, see here:
http://tt-rss.org/forum/viewtopic.php?f=10&t=1924&p=9796\#p9714
