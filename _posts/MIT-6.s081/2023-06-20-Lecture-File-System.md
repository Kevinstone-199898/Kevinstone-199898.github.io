---
title: 'Lecture:File System'
date: 2023-06-20
permalink: /posts/MIT-6.s081/Lecture-File-System
author_profile: true
tags:
  - Operating system
---

## Lecture Review

## Code Analysis

log.c:
``` c
void
initlog(int dev, struct superblock *sb)
{
  if (sizeof(struct logheader) >= BSIZE)
    panic("initlog: too big logheader");

  initlock(&log.lock, "log");
  log.start = sb->logstart;
  log.size = sb->nlog;
  log.dev = dev;
  recover_from_log();
}
```
