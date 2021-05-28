---
title: "Error: Can't open display: 0"
# excerpt: ""

categories:
  - Computer
tags:
  - WSL
  - stackoverflow

# toc: true 
# toc_label: "Table of Contents"
# toc_icon: "cog"
# toc_sticky: true

last_modified_at: 2021-05-28 10:54:00 +0900
---

* Solution

```
# This command can also be added in shell initialization files, for example

export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0
```


* References: 
    * Sizuji. (2021, May 28). Error: Can't open display: 0. [https://superuser.com/questions/1476086/error-cant-open-display-0](https://superuser.com/questions/1476086/error-cant-open-display-0)

