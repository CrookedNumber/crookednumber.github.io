---
layout: post
title:  "Don’t always use module_load_include()?"
date:   2012-08-15
---

<blockquote class="twitter-tweet" lang="en"><p>Do not use module_load_include() for files in your own module. require_once &#39;mymodule.inc&#39;; in mymodule.module is fine.</p>&mdash; Drupal Code Review (@drupal_review) <a href="https://twitter.com/drupal_review/status/235380645134745601">August 14, 2012</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

I think this makes sense. I'd like to know, however, like @scottr if this is an “official” thing.

Then again, at second blush, I might argue that using different include processes in different contexts makes me think! And that's not good.