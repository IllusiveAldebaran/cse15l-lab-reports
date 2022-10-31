# Week 5 Lab Report
---

## 1) GREP

For this lab report we will be focusing on grep. By far it is the one with more that I don't know and more to offer thatn than `less` or `find`, though I think `find` and some of it's options may be useful to learn later. But grep is useful in many contexts. And I need to review it. I remember that egrep, now `grep -e` is I think for regex expressions. I have used `--` as a flag to escape `-`, and somehow I think `-o` flag to look for multiple expressions. Either way for this lab I will look at three examples of flags for grep. I will also list out some useful ones but the less work I have to type out, format, and paste pictures on the lab is more practice time for me in the terminal and messing around with linux.

For starters `grep` seems to come from `g/re/p`, or a global search of a regular expression, then print. It reminds me of the substiture command in vim. For more information off wiki read [here](https://en.wikipedia.org/wiki/Grep). 

Let's see a first example: 

**The -o ** flag. 



The following are useful flags that are so self explanatory I couldn't be bothered to choose them for the lab, yet are good to note:
| Flag         | Description   ||--------------|------------|| -i | ignore case || -v | omit lines with the reg. expression || -c | counts the number of times regex appears in file || -l | prints just the file names if regex is found || -r | include subdirectories || -A [number] | prints number of line after regex line as well  || -B [number] | Like -A, but backwards. || -C [number] | Like both -A and -B | -n | print with line numbers ||


[Link back](index.md)