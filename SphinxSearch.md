Full-text search using Sphinx
=============================

Since version:1.5.0 tt-rss is capable of using
[Sphinx](http://www.sphinxsearch.com) search engine. Before adding
<code>search\_sphinx</code> to <code>config.php</code> directive
<code>PLUGINS</code>, you’ll have to install and configure Sphinx
indexing daemon as described in the [official
docs](http://www.sphinxsearch.com/docs/).

Example configuration files attached below. Don’t forget that you need
to update the indexes, for example using cron:

    0   0    *   *   *   /usr/bin/indexer --rotate ttrss >/dev/null 2>&0
    0  */2   *   *   *   /usr/bin/indexer --rotate delta >/dev/null 2>&0

More information on delta indexing
[here](http://sphinxsearch.com/docs/1.10/delta-updates.html)

See also: [this forum
thread](http://tt-rss.org/forum/viewtopic.php?f=16&t=2078)
