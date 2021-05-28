---
title: "How can I copy the output of a command directly into my clipboard?"
# excerpt: ""

categories:
  - Computer
tags:
  - pipe
  - xclip
  - stackoverflow

# toc: true 
# toc_label: "Table of Contents"
# toc_icon: "cog"
# toc_sticky: true

last_modified_at: 2021-05-28 10:54:00 +0900
---

* Solution

```
sudo apt-get install xclip

# You can pipe the output into xclip to be copied into the clipboard:
cat file | xclip

# To paste the text you just copied, you shell use:
xclip -o
```


* References: 
    * Legend. (2021, May 28). Error: How can I copy the output of a command directly into my clipboard?. [https://stackoverflow.com/questions/5130968/how-can-i-copy-the-output-of-a-command-directly-into-my-clipboard](https://stackoverflow.com/questions/5130968/how-can-i-copy-the-output-of-a-command-directly-into-my-clipboard)


