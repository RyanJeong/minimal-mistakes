---
title: "How Many Palindromes?"
# excerpt: ""

categories:
  - Puzzle
tags:
  - Palindrome

# toc: true 
# toc_label: "Table of Contents"
# toc_icon: "cog"
# toc_sticky: true

last_modified_at: 2019-08-11 12:29:00 +0900
---

In the April 1984 Scientific American "Computer Recreations" column, an article appeared about mathematical patterns (F. Gruenberger, Computer Recreations, "How to Handle Numbers with Thousands of Digits, and Why One Might Want To.", Scientific American, 250 [No. 4, April, 1984], 19-26.). Here's the algorithm:

1. Pick a number.
1. Reverse its digits and add this value to the original number.
3. If this is not a palindrome, go back to step 2 and repeat.

Do all numbers eventually become palindromes by this process? It was suggested that this is the case.
