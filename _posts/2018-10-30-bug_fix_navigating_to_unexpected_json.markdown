---
layout: post
title:      "Bug Fix: Navigating to unexpected JSON"
date:       2018-10-30 05:24:14 +0000
permalink:  bug_fix_navigating_to_unexpected_json
---


This week I tackled an issue that had been dogging one of my projects for weeks.  It was a big issue that did not prevent my applications from functioning.  However, it did leave something to be desired in terms of user experience as using the browser’s back and forward commands yielded undesirable results.  This entry will describe the situation and fix.

## Video Game Community Hub

This app had originally been written strictly in Rails and was revamped to include internal API calls using jQuery.  One of the pages was the video games index, an area where the user can see a full list of the videogames handled by the site.

If a user navigated `back` to the video games index from another page JSON would load on the screen instead of HTML.  This was not a bug that could be tolerated on a live web app.
Looking through my resources I found a line of code that could be added to the JavaScript file handling the jQuery `$.get()` request to the `/video_games` route:

```
$(document).ready(function() {
  $.ajaxSetup({ cache: false });
});
```

It turns out that the browser had been caching my AJAX requests in addition to my html requests.  So even though the `/video_games.html` request had been processed, the most recent JSON request was cached.  So browser navigation using `forward` or `back` would load the unintended JSON.  

The code above prevents all AJAX requests from being cached.  This means, the browser navigation will now flow smoothly between HTML pages.  I was surprised but relieved to see that this ended up being a silver bullet, completely fixing my bug.


