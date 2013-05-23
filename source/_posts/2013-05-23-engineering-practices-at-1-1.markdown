---
layout: custom_post
title: "Engineering Practices at 1:1"
date: 2013-05-16 09:30
comments: true
categories:
  - best practices
author: Nathan Hopkins
gravatar: 254ec240c9143768df8ec27182764cad
github: hopsoft
twitter: natehop
linkedin: 2951631
---

Expediency often rules the day in business, but at 1:1 we've establised a couple
of practices to help ensure that developers don't shoot themselves, *or the team*,
in the foot.

## No Hot Patches!

The definintion of hot-patch in this context means:
*live code editing on production servers*.

As crazy as this sounds, it has happened in the past.
Sometimes the convenience seems too tempting... especially for minor experiments.
But the convenience isn't worth team members getting pulled out of bed in the
wee hours only to discover a typo someone made in a live edit.

It's especially frustrating because it doesn't leave a paper trail.
The tools we employ, like Git, become effectively useless in this scenario.

**Never make live code edits on the server! Always make a formal commit and deploy.**

## Always Create a Topic Branch!

All new development should be occur on a
[topic branch](http://git-scm.com/book/en/Git-Branching-Branching-Workflows),
not the master branch.

The master branch should always be stable and production ready.
A deploy might occur at any time, so the code on master must be production ready.

**This rule is universal (no exceptions)**... even for developers working on their own.
Once the work is complete, a [pull request](https://help.github.com/articles/using-pull-requests)
should be created. After the pull request is created the change-set should be code reviewed,
*ideally by someone other than the original developer*.
Once the pull request is approved, the topic branch should be merged into master.

