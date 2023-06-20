---
permalink: /blogs/MIT-6.s081/Lecture-File-System
title: "Lecture:File System"
author_profile: true
tags:
  - Operating system
---

{% include base_path %}


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
