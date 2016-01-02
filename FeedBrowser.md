Feed Browser or “Other Feeds”
=============================

Feed browser shows feeds subscribed by other users of the instance which
are not marked as private, have no login information entered and are not
already subscribed by the user.

Data cache, applies since 1.2.31
--------------------------------

To minimize the time spent by generating the feeds index, Feed Browser
uses a cache of subscription information. This cache can be generated
with two ways:

-   Update daemon handles feed browser cache automatically. If you are
    using update daemon, you don’t have to do anything else.
-   Manually by running <code>update.php —feedbrowser</code>
