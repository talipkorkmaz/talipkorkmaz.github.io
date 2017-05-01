---
layout: post
title: "Force to rebuilding github pages.."
comments: true
description: "If you have a Guest post.."
keywords: "rebuild github page"
author: talipkorkmaz
---

Github told that : 
It's not currently possible to manually trigger a rebuild, without pushing a commit to the appropriate branch.

So if you want to refresh your github page after a push, you can push an empty commit to rebuild github pages..

git commit -m 'rebuild pages' --allow-empty

git push