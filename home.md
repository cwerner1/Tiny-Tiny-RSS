Tiny Tiny RSS is an open source web-based news feed (RSS/Atom) reader
and aggregator, designed to allow you to read news from any location,
while feeling as close to a real desktop application as possible.

\[\[Screenshots\]\]

Sponsored by [Dealspotr]

Features
========

-   Server-side AJAX-powered application, user only needs a web browser.
-   Free software, licensed under [GNU GPLv3]
-   Self-hosted: control your own data and protect your privacy instead
    of depending on a cloud service which may be discontinued at any
    moment
-   Supports
    -   \[\[GeneratedFeeds|feed aggregation / syndication\]\],
    -   \[\[KeyboardShortcuts|keyboard shortcuts\]\],
    -   OPML import/export,
    -   multiple ways to share stuff: via RSS feeds, using plugins to
        various social sites, sharing by URL, etc,
    -   \[\[ShareAnything|sharing arbitrary content through tt-rss\]\],
    -   \[\[MobileVersion|mobile devices\]\],
    -   internationalization,
    -   \[\[Plugins|various plugins\]\] and \[\[Themes|themes\]\],
    -   detecting and filtering duplicate articles,
    -   podcasts,
    -   \[\[ContentFilters|flexible article filtering\]\],
    -   \[\[JsonApiReference|JSON-based API\]\],
    -   and much more…
-   Official [Android client]

Get in touch
============

Join [community forums] if you have any questions, comments or bug
reports.

Requirements
============

You need a \[\[CompatibleBrowsers|compatible web browser\]\] on the
client side.

Server-side
-----------

You will need a dedicated web hosting account (i.e. a VDS) or access to
a physical server running generic modern [LAMP] stack or compatible.

Everything else, including, but not limited to, shared hosting accounts,
windows and other alternative OSes, free tiers of PaaS services of any
kind, is not supported. Not supported in this case meaning: it may work
in your particular case but if you have problems you are on your own.

Additionally, tt-rss requires:

-   PHP version **5.4** or newer (\[\[PhpCompatibilityNotes|detailed
    PHP requirements\]\])
-   [PostgreSQL] (**9.1** or newer) or [MySQL] (**InnoDB is required**,
    MyISAM will not work).

You can use either of the databases, but PostgreSQL should run tt-rss
faster.

Download
========

Tiny Tiny RSS uses a [rolling release] model based on [git master]
branch which is considered stable.

There’s no warranty. If it breaks you get to keep both parts.

Please read \[\[InstallationNotes|installation guide\]\] and
\[\[UpdatingFeeds\]\] before installing.