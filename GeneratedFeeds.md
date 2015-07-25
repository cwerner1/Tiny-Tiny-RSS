Generated feeds and syndication
===============================

(Almost) anything you see in the headlines buffer can also be accessed
and syndicated further via a generated RSS feed by clicking the **little
feed icon** at the right of the currently loaded feed title:

![](/images/syndicated_feed_icon.png)

Or in version:1.12 next to the feed list near the top:

![](/images/redmine/112_feed_icon.png)

You can access labels, categories, tags, search results as RSS feeds.
Since version:1.5.0 you can also limit the articles which go into
generated feeds, e.g. you can have a generated feed which includes
published articles from category X.

Data protection
---------------

Generated feeds are protected using random unique keys. Key can be
regenerated at any time.

![](/images/gen_feed_dialog.png)

Anatomy of a generated feed URL
-------------------------------

Consider an example:

    http://x.y.z/tt-rss/backend.php?op=rss&id=61&is_cat=1&view-mode=adaptive

-   id (integer) - requested feed ID
-   is\_cat (boolean) - whether the feed is a category
-   view-mode (string) - see below
-   key (string) - automatically generated access key (since
    version:1.5.0)

Optional parameters:

-   login, pass - see above
-   format - since version:1.6.0 specifies output format, possible
    values: atom, json
-   limit - amount of articles to output, default: 30
-   offset - start output while skipping this amount of articles,
    default: 0 (since version:1.6.0)
-   order - override default headlines order (since version:1.8)
-   ts - output articles newer than timestamp in
    [strtotime](http://www.php.net/manual/en/function.strtotime.php)
    accepted format (since version:1.12) i.e. stuff like
    <code>ts=1%20month%20ago</code>

Special feed IDs:

-   ~~1~~ Starred articles
-   ~~2~~ Published articles
-   ~~3~~ Fresh articles
-   ~~4~~ All articles
-   0 - Archived articles

Feed IDs \< ~~10 are considered Labels.
\
Special category IDs (is\_cat=1):
\
\* 0~~ Uncategorized\
\* ~~1~~ Special category (includes Starred, Published, etc.)\
\* ~~2~~ Labels category (includes your labels)

View mode values:

Note: It’s probably not a very good idea to use Adaptive view mode for
generated feeds.

-   <code>adaptive</code> - shows unread articles only when they are
    unread articles, shows everything otherwise
-   <code>marked</code> (this means starred), <code>has\_note</code>,
    <code>published</code>, <code>unread</code>,
    <code>unread\_first</code> - should be self explanatory

Actual output may differ between modes for several special feeds for
usability reasons, e.g. recently read feed ignores <code>unread</code>
specifier because unread articles are never part of the feed).

Order values:

-   default - depends on the feed: either import batch date or (for
    published and starred feeds) last\_published and last\_marked
-   title - sort by title
-   date\_reverse - reverse sort by batch date
-   feed\_dates - sort by feed-provided article dates

See also: [[PublishArticles]], [this forum
thread](http://tt-rss.org/forum/viewtopic.php?f=1&t=446&p=3015#p3015)
and [this other forum
thread](http://tt-rss.org/forum/viewtopic.php?f=8&t=354)
