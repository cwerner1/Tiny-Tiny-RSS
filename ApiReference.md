JSON API Reference
==================

Supported since version:1.4.0.

The API is pluggable, plugins can use host
<code>add\_api\_method()</code> to add custom API calls (see
<code>classes/pluginhost.php</code> for details).

Summary
-------

The API is stateful. You need to login and maintain a session ID to
perform further operations. Session ID should be specified using JSON
parameter **sid**. I.e.

    $ curl -d '{"sid":"your-session-id","op":"getVersion"}' http://example.dom/tt-rss/api/

All API calls output JSON-encoded data. API can be enabled or disabled
per-user in the preferences. Client parameters should be passed encoded
using JSON in HTTP POST data (supported since version:1.5.3). Older
versions allowed passing parameters using HTTP GET and POST, but this is
no longer supported.

Testing API calls (using curl)
------------------------------

    $ curl -d '{"op":"login","user":"you","password":"xxx"}' http://example.dom/tt-rss/api/

Most of the calls (except login, logout, isLoggedIn) require valid login
session or will return this error object:
<code>{"error":"NOT_LOGGED_IN"}</code>

Output format
-------------

### 1.5.0 and above

All API methods return JSON data like this:

<code>{"seq":0,"status":0,"content":{"version":"1.4.3.1"}}</code>

-   seq (integer) is the sequence number supplied by client (&seq=131)
-   status (integer) indicates whether request has been completed
    successfully, can be either 0 (API\_STATUS\_OK) or 1
    (API\_STATUS\_ERR)
-   content is the actual reply content, as documented below in method
    descriptions.

### 1.4.3 and below (obsolete)

Methods return the “content” object below, sequence numbers and statuses
are not supported.

Methods
-------

### getApiLevel (since version:1.5.8, api level 1)

Return an abstracted integer API version level, increased with each API
functionality change. This is the proper way to detect host API
functionality, instead of using getVersion.

<code>{"level":1}</code>

Whether tt-rss returns error for this method (e.g. version:1.5.7 and
below) client should assume API level 0.

### getVersion

Returns tt-rss version. As of, version:1.5.8 it is not recommended to
use this to detect API functionality, please use getApiLevel instead.

<code>{"version":"1.4.0"}</code>

### login

Parameters:

-   user (string)
-   password (string)

Returns client session ID.

<code>{"session\_id":"xxx"}</code>

It can also return several error objects:

-   If API is disabled for this user:
    <code>error: "API_DISABLED"</code>
-   If specified username and password are incorrect:
    <code>error: "LOGIN_ERROR"</code>

In case it isn’t immediately obvious, you have to login and get a
session ID even if you are using single user mode. You can omit user and
password parameters.

On version:1.6.0 and above login also returns current API level as an
<code>api\_level</code> integer, you can use that instead of calling
getApiLevel after login.

### logout

Closes your login session. Returns either status-message <code>{"status":"OK"}</code> or an error (e.g. <code>{"error":"NOT_LOGGED_IN"}</code>)

### isLoggedIn

Returns a status message with boolean value showing whether your client
(e.g. specific session ID) is currently logged in.

<code>{"status":false}</code>

### getUnread

Returns an integer value of currently unread articles.

<code>{"unread":"992"}</code>

### getCounters

Returns JSON-encoded counter information. Requires version:1.5.0.

* output\_mode (string, default: flc) - what kind of information to return (f - feeds, l - labels, c - categories, t - tags)

### getFeeds

Returns JSON-encoded list of feeds. The list includes category id,
title, feed url, etc.

Parameters:

-   cat\_id (integer) - return feeds under category cat\_id
-   unread\_only (bool) - only return feeds which have unread articles
-   limit (integer) - limit amount of feeds returned to this value
-   offset (integer) - skip this amount of feeds first
-   include\_nested (bool) - include child categories (as Feed objects
    with is\_cat set) **requires version:1.6.0**

Pagination:

Limit and offset are useful if you need feedlist pagination. If you use
them, you shouldn’t filter by unread, handle filtering in your app
instead.

Special category IDs are as follows:

*  0 Uncategorized
* -1 Special (e.g. Starred, Published, Archived, etc.)
* -2 Labels

Added in version:1.5.0:

-   -3 All feeds, excluding virtual feeds (e.g. Labels and such)
-   -4 All feeds, including virtual feeds

Known bug: Prior to version:1.5.0 passing null or 0 cat\_id to this
method returns full list of feeds instead of Uncategorized feeds only.

### getCategories

Returns JSON-encoded list of categories with unread counts.

-   unread\_only (bool) - only return categories which have unread
    articles
-   enable\_nested (bool) - switch to nested mode, only returns topmost
    categories **requires version:1.6.0**
-   include\_empty (bool) - include empty categories **requires
    version:1.7.6**

Nested mode in this case means that a flat list of **only** topmost
categories is returned and unread counters include counters for child
categories.

This should be used as a starting point, to display a root list of all
(for backwards compatibility) or topmost categories, use getFeeds to
traverse deeper.

### getHeadlines

Returns JSON-encoded list of headlines.

Parameters:

-   feed\_id (integer) - only output articles for this feed
-   limit (integer) - limits the amount of returned articles (see below)
-   skip (integer) - skip this amount of feeds first
-   filter (string) - currently unused (?)
-   is\_cat (bool) - requested feed\_id is a category
-   show\_excerpt (bool) - include article excerpt in the output
-   show\_content (bool) - include full article text in the output
-   view\_mode (string = all\_articles, unread, adaptive, marked,
    updated)
-   include\_attachments (bool) - include article attachments (e.g.
    enclosures) **requires version:1.5.3**
-   since\_id (integer) - only return articles with id greater than
    since\_id **requires version:1.5.6**
-   include\_nested (boolean) - include articles from child categories
    **requires version:1.6.0**
-   order\_by (string) - override default sort order **requires
    version:1.7.6**
-   sanitize (bool) - sanitize content or not **requires version:1.8**
    (default: true)
-   force\_update (bool) - try to update feed before showing headlines
    **requires version:1.14 (api 9)** (default: false)
-   has\_sandbox (bool) - indicate support for sandboxing of iframe
    elements **<span class="10 api"></span>** (default: false)
-   include\_header (bool) - adds status information when returning
    headlines, instead of array(articles) return value changes to
    array(header, array(articles)) (api 12)

Limit:

Before **API level 6** maximum amount of returned headlines is capped at
60, API 6 and above sets it to 200.

This parameters might change in the future (supported since **API level
2**):

-   search (string) - search query (e.g. a list of keywords)
-   search\_mode (string) - all\_feeds, this\_feed (default), this\_cat
    (category containing requested feed)
-   match\_on (string) - ignored

Special feed IDs are as follows:

-   -1 starred
-   -2 published
-   -3 fresh
-   -4 all articles
-   0 - archived
-   IDs \< -10 labels

Sort order values:

-   date\_reverse - oldest first
-   feed\_dates - newest first, goes by feed date
-   (nothing) - default

### updateArticle

Update information on specified articles.

Parameters:

-   article\_ids (comma-separated list of integers) - article IDs to
    operate on
-   mode (integer) - type of operation to perform (0 - set to false, 1 -
    set to true, 2 - toggle)
-   field (integer) - field to operate on (0 - starred, 1 - published, 2 - unread, 3 - article note **since api level 1**)
-   data (string) - optional data parameter when setting note field
    (since **api level 1**)

E.g. to set unread status of articles X and Y to false use the
following:

<code>?article\_ids=X,Y&mode=0&field=2</code>

Since version:1.5.0 returns a status message:

<code>{"status":"OK","updated":1}</code>

“Updated” is number of articles updated by the query.

### getArticle

Requests JSON-encoded article object with specific ID.

-   article\_id (integer) - article ID to return **as of 15.10.2010
    git** or version:1.5.0 supports comma-separated list of IDs

Since version:1.4.3 also returns article attachments.

### getConfig

Returns tt-rss configuration parameters:

<code>{"icons_dir":"icons","icons_url":"icons","daemon_is_running":true,"num_feeds":71}</code>

-   icons\_dir - path to icons on the server filesystem
-   icons\_url - path to icons when requesting them over http
-   daemon\_is\_running - whether update daemon is running
-   num\_feeds - amount of subscribed feeds (this can be used to refresh
    feedlist when this amount changes)

### updateFeed

Tries to update specified feed. This operation is not performed in the
background, so it might take considerable time and, potentially, be
aborted by the HTTP server.

-   feed\_id (integer) - ID of feed to update

Returns status-message if the operation has been completed.

<code>{"status":"OK"}</code>

### getPref

Returns preference value of specified key.

-   pref\_name (string) - preference key to return value of

<code>{"value":true}</code>

### catchupFeed

Required version: version:1.4.3

Tries to catchup (e.g. mark as read) specified feed.

Parameters:

-   feed\_id (integer) - ID of feed to update
-   is\_cat (boolean) - true if the specified feed\_id is a category

Returns status-message if the operation has been completed.

<code>{"status":"OK"}</code>

### getCounters

Required version: version:1.5.0

Returns a list of unread article counts for specified feed groups.

Parameters:

-   output\_mode (string) - Feed groups to return counters for

Output mode is a character string, comprising several letters (defaults
to “flc”):

-   f - actual feeds
-   l - labels
-   c - categories
-   t - tags

Several global counters are returned as well, those can’t be disabled
with output\_mode.

### getLabels (since API level 1)

Returns list of configured labels, as an array of label objects:

<code>{"id":2,"caption":"Debian","fg\_color":"#e14a00","bg\_color":"#ffffff","checked":false},</code>

Before version:1.7.5

Returned id is an internal database id of the label, you can convert it
to the valid feed id like this:

<code>feed\_id = \-11 - label\_id</code>


After:

No conversion is necessary.

Parameters:

* article\_id (int) - set “checked” to true if specified article id has returned label.

### setArticleLabel (since API level 1)

Assigns article\_ids to specified label.

Parameters:

\* article\_ids - comma-separated list of article ids\
 \* label\_id (int) - label id, as returned in getLabels\
 \* assign (boolean) - assign or remove label

Note: Up until version:1.15 setArticleLabel() clears the label cache for
the specified articles. Make sure to regenerate it (e.g. by calling API
method getLabels() for the respecting articles) when you’re using
methods which don’t do that by themselves (e.g. getHeadlines())
otherwise getHeadlines() will not return labels for modified articles.

### shareToPublished (since API level 4 - version:1.6.0)

Creates an article with specified data in the Published feed.

Parameters:

* title - Article title (string)
* url - Article URL (string)
* content - Article content (string)

### subscribeToFeed (API level 5 - version:1.7.6)

Subscribes to specified feed, returns a status code. See
subscribe\_to\_feed() in functions.php for details.

Parameters:

* feed\_url - Feed URL (string)
* category\_id - Category id to place feed into (defaults to 0, Uncategorized) (int)
* login, password - Self explanatory (string)

### unsubscribeFeed (API level 5 - version:1.7.6)

Unsubscribes specified feed.

Parameters:

* feed\_id - Feed id to unsubscribe from

### getFeedTree (API level 5 - version:1.7.6)

* include\_empty (bool) - include empty categories

Returns full tree of categories and feeds.

Note: counters for most feeds are not returned with this call for
performance reasons.
