Scoring
=======

Since version:1.2.23, tt-rss supports scoring in a way similar to some newsreaders, albeit more limited. The score is calculated on article import using special filters with a "Modify score" action. The resulting score is a sum of all score modifiers from all matching filters. So, for example, if the article matches two filters A (score +100) and B (score -50), the resulting score will be 50.

Article score affects the position of the article in the headline buffer (which is sorted by score) and alters the way article is displayed:

| Score | Display / Action |
|-------|------------------|
| < -500 | Score indicator is dark, headline is gray and striked through, article is automatically marked as read
| < -100 | Score indicator is dark, headline is gray and striked through
| < 0    | Score indicator is half-filled dark, version:1.5.0: article is excluded from Fresh feed and (as of version:1.5.10 also excluded from email digest) |
|   0    | Display normally |
| > 0    | Score indicator is half-filled green |
| > 500  | Score indicator is green and headline text is highlighted green |
| > 1000 | Same as above, article is also marked as starred |

Calculated score for an individual article may be adjusted by clicking on score indicator in the headlines list.

![](http://tt-rss.org/images/score_indicator.png)