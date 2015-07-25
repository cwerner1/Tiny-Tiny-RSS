Filters
=======

Filters are a very powerful and flexible tool which may significantly
ease the task of extracting useful information from the sea of data that
is RSS feeds. Filters are applied to articles based on [regular
expression](http://en.wikipedia.org/wiki/Regular_expression) match
against specified fields. After the match had been found, configured
actions are taken. Matching is case-insensitive,
[PCRE](http://php.net/manual/en/reference.pcre.pattern.syntax.php)
pattern syntax is used.

Exact filtering algorithm has changed several times during tt-rss
development. Most current one is described in the section below.

Filters in version:1.7.6 (current)
----------------------------------

### Order of loading and processing

Filters are loaded in user-specified order and applied sequentially. It
is possible to reorder filters using drag and drop. If no manual sorting
is specified, filters are sorted alphabetically according to user
configured caption. If no caption is specified for any filter, loading
order is not guaranteed.

### Filter objects

Each filter object may contain an arbitrary amount of regular expression
rules and actions. Each expression may have inverse flag set, which
inverts matching result. On top of that, filter may also have an inverse
flag, which inverts the final matching.

Filter object may be configured to successfully match when either one or
all rules match.

Regular expressions may be matched against several article fields, such
as, title, content, author, etc.

### Matching articles and applying actions

Filter matching is performed during feed processing.

Some actions may be applied only when the article is initially imported
from the feed. Other actions may be applied every time article is seen
in the originating feed. It is suggested to only rely on filters
applying to articles imported after the filter had been created.

Several actions are available:

1\. Delete article - do not import article from the feed, does not
actually delete anything from the database\
2. Mark as read - imports article automatically marked as read\
3. Set starred - sets article starred automatically on import\
4. Assign tags - assigns custom tags on import\
5. Publish article - sets article published automatically on import\
6. [[Scoring|Modify score]] - modifies article overall score based on
the parameter, a signed integer number. Final article score is
calculated after all filters had been applied and is a sum of all
matched scoring actions. I.e. if 3 actions matched the article: ~~5, +5,
+10~~ the overall score will be 10.\
7. Assign label - assigns specified label to the article on import\
8. Stop / Do nothing - stops further filter processing for this article,
no following filters will be checked nor rules applied.

After all matching filters had been computed for the article, it is
either imported with modifications as specified by the rules, or dropped
if Delete article action has been found.

### Filter testing

Filter testing routine uses database regular expression engine which may
not be completely compatible with (usually supporting a subset of)
[PCRE](http://php.net/manual/en/reference.pcre.pattern.syntax.php)
library used for actually applying filters when tt-rss is processing
articles. This can cause filters not returning valid results while
testing but otherwise working correctly or vice versa.

Filters in version:1.6.0 up to version:1.7.5
--------------------------------------------

In version:1.6.0 filters have been improved to support multiple
arbitrary match rules and actions per filter. You can migrate old
filters to new format using <code>update.php —convert-filters</code>
after updating the database schema to current version. It is also
possible to combine filters together.

Also, date filtering and inverse filters have been removed.

Please note that order of filters and rules being loaded is not
guaranteed, do not make filters depending on the output of previous
filter. You will run into problems.

Filters in older versions
-------------------------

One match and one action per filter are supported. Supported actions:
delete (do not import) article, mark article as read, set starred,
assign tag(s). Filters can be defined globally and for some specific
feed.

Exact filtering algorithm is different between versions:

### 1.2.7 and older

First matching filter is used for the article. If two filters match one
regular expression, only one filter will be applied. Behaviour for
selecting the filter is undefined, thus creation of overlapping filters
is strongly not recommended.

### 1.2.8 and newer

Since 1.2.8, multiple and inverse matching are supported. All matching
filters are considered when article is being imported and all actions
executed in sequence. Inverse matching reverts matching result, e.g.
filter matching XYZZY in title with inverse flag will match all
articles, except those containing string XYZZY in title.

See also: [[Scoring]]
