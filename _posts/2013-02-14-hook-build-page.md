---
layout: post
title:  hook_build_page() for CSS/JS
date:   2013-02-14
---

<blockquote class="twitter-tweet" lang="en"><p>Drupal 7 protip: Adding CSS or JS to every page? Use hook_page_build() and not hook_init().</p>&mdash; Dave Reid (@davereid) <a href="https://twitter.com/davereid/status/294554866649542657">January 24, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet" lang="en"><p><a href="https://twitter.com/BarisW">@BarisW</a> hook_init() runs even on AJAX requests, private file requests, etc. hook_page_build() runs when we&#39;re only delivering HTML.</p>&mdash; Dave Reid (@davereid) <a href="https://twitter.com/davereid/status/294587341576749057">January 24, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>