Tiny Tiny RSS is an open source web-based news feed (RSS/Atom) reader
and aggregator, designed to allow you to read news from any location,
while feeling as close to a real desktop application as possible.

<a target="_blank" href="http://tt-rss.org/images/1.12/1.png"><img src="http://tt-rss.org/images/1.12/thumb/1.jpg"></a>

Sponsored by [Dealspotr](http://dealspotr.com/)

<form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
<input type="hidden" name="cmd" value="_donations">
<input type="hidden" name="business" value="cthulhoo@gmail.com">
<input type="hidden" name="lc" value="US">
<input type="hidden" name="item_name" value="Tiny Tiny RSS">
<input type="hidden" name="currency_code" value="EUR">
<input type="hidden" name="bn" value="PP-DonationsBF:btn_donate_SM.gif:NonHosted">
<input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif" border="0" name="submit" alt="PayPal - The safer, easier way to pay online!">
<img alt="" border="0" src="https://www.paypalobjects.com/en_US/i/scr/pixel.gif" width="1" height="1">
</form>

Features
========

-   Server-side AJAX-powered application, user only needs a web browser.
-   Free software, licensed under [GNU
    GPLv3](http://www.gnu.org/copyleft/gpl.html)
-   Self-hosted: control your own data and protect your privacy instead
    of depending on a cloud service which may be discontinued at any
    moment
-   Supports
    -   [feed aggregation / syndication](GeneratedFeeds),
    -   [keyboard shortcuts](KeyboardShortcuts),
    -   OPML import/export,
    -   multiple ways to share stuff: via RSS feeds, using plugins to
        various social sites, sharing by URL, etc,
    -   [sharing arbitrary content through tt-rss](ShareAnything),
    -   [mobile devices](MobileVersion),
    -   internationalization,
    -   [Plugins](Plugins) and [themes](Themes),
    -   detecting and filtering duplicate articles,
    -   podcasts,
    -   [flexible article filtering](ContentFilters),
    -   [JSON-based API](ApiReference),
    -   and much more…
-   Official [Android client](http://tt-rss.org/redmine/projects/tt-rss-android/wiki)

Get in touch
============

Join [community forums](http://tt-rss.org/forum) if you have any questions, comments or bug reports.

Requirements
============

You will need a modern web browser on the client side.

Server-side
-----------

You will need a dedicated web hosting account (i.e. a VDS) or access to
a physical server running generic modern [LAMP](http://en.wikipedia.org/wiki/LAMP_(software_bundle)) stack or
compatible.

Everything else, including, but not limited to, shared hosting accounts,
windows and other alternative OSes, free tiers of PaaS services of any
kind, is not supported. Not supported in this case meaning: it may work
in your particular case but if you have problems you are on your own.

Additionally, tt-rss requires:

-   PHP version **5.4** or newer ([detailed PHP requirements](PhpCompatibilityNotes))
-   [PostgreSQL](http://www.postgresql.org) (**9.1** or newer) or
    [MySQL](http://www.mysql.com) (**InnoDB is required**, MyISAM will
    not work).

You can use either of the databases, but PostgreSQL should run tt-rss
faster.

Download
========

Tiny Tiny RSS uses a [rolling release](http://tt-rss.org/forum/viewtopic.php?f=10&t=3262) model based on git master branch which is considered stable.

There’s no warranty. If it breaks you get to keep both parts.

Please read the [installation guide](InstallationNotes) and [UpdatingFeeds](UpdatingFeeds) before installing.
