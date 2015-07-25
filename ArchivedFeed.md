“Archived articles” feed
========================

Please note the following: There’s usually no point in manually
archiving articles.

If you want to keep articles for later, just star them, and they won’t
get purged. Manual archiving may have side effects, e.g. if you archive
an article while it still exists in the originating feed XML, it will be
reimported and create a duplicate entry. In short, unless you are
absolutely sure, you don’t need to manually archive anything.

In general, consider manual un/archiving of articles an advanced
function. The point of this feed is to give you access to externally
shared data ([[ShareAnything]]) which has no feed by definition or your
starred articles if originating feed no longer exists in tt-rss
database.

Supported since version:1.4.0.

Archived article feed works as such:

-   When you unsubscribe from the feed, all starred articles are moved
    into the archive for safe-keeping.
-   You can also manually archive articles from the feed actions (i.e.
    More…) dropdown menu and subsequently move them back if the
    originating feed is still available (e.g. subscribed).
-   Archived articles are not subject to the usual automatic expiration
    process.
-   Articles created using [[ShareAnything]] are placed into Archived
    feed.
