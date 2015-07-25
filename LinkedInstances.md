Linked tt-rss instances
=======================

TL;DR: If you connect instances of tt-rss together, you’ll be able to
see feeds from linked instances in Subscribe to feed ~~\> More feeds~~\>
Popular dialog.

See also: \#270

Since version:1.5.3 it is possible to connect independent installations
of Tiny Tiny RSS to share feed subscription information displayed in
Popular feeds. The idea is that by connecting instances it would be
easier to subscribe to potentially interesting content. The code is
considered experimental but it seems to work.

The functionality is available in Preferences (Linked tab) and should be
self explanatory. Setup connections on both ends of a link using the
same access key and you should be good to go - tt-rss would
automatically ping the links once in 6 hours. You can erase the last
connection timestamp by editing and saving the linked instance in the
Preferences.

All information shared is anonymous and doesn’t identify your users.
Feeds which are marked as excluded from the feed browser or configured
with login/password are excluded from the Popular feeds browser and not
shared in any way.

Tiny Tiny RSS doesn’t reshare feed subcription acquired from linked
instances - i.e. only local feeds are shared between instances.
