---
layout: custom_post
title: "Documenting Github Projects"
date: 2013-05-16 09:30
comments: true
categories:
  - github
  - documentation
author: Nathan Hopkins
gravatar: 254ec240c9143768df8ec27182764cad
github: hopsoft
twitter: natehop
linkedin: 2951631
---

Our team has struggled with finding the best solution for project documentation.
Some projects require internal documentation while others require public API docs.
Several projects require both.

Then I stumbled into how 37 Signals manages their [public API docs](https://github.com/37signals/api).
They basically create a new public repo for each public API they need to document.

This is great, but maintaining docs separate from the project can be challenging,
so we've opted for having 2 document branches in our projects.

* doc
* gh-pages

The *doc* branch is used for internal documentation.
We delete all code after branch creation, then simply maintain an organized set of markdown files.

The *gh-pages* branch is used for all public documentation.
The great thing about [github pages](http://pages.github.com/) is that the site they generate is always public...
even for private repos. We leverage this to expose public docs.

For a simple example, you can review one of our public APIs [here](http://engineering.1on1.com/lead_assure/).

For those with access to the private repo, you can view the various doc branches.
[doc](https://github.com/one-on-one/lead_assure/tree/doc) [gh-pages](https://github.com/one-on-one/lead_assure/tree/gh-pages)

Managing docs on the project itself helps ensure our docs get written and maintained.

