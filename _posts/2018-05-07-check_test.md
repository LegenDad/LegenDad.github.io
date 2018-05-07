---
layout: post                          # (require) default post layout
title: "Test Check Check"                   # (require) a string title
date: 2018-05-07 17:41:02             # (require) a post date
categories: [python, django]          # (custom) some categories, but makesure these categories already exists inside path of `category/`
tags: [foo, bar]                      # (custom) tags only for meta `property="article:tag"`
image: Broadcast_Mail.png             # (custom) image only for meta `property="og:image"`, save your image inside path of `static/img/_posts`

---


왜 date에 +700인가...  


tags는 작동하는가...



<meta content="{{ tag }}" property="article:tag">  

<meta property="article:tag" content="advocate" />
<meta property="article:tag" content="Article Tag" />
<ul>
  <li property="article:tag">advocate</li>
  <li property="article:tag">charity</li>
  <li property="article:tag">crowdfunding</li>
</ul>

image???
..
