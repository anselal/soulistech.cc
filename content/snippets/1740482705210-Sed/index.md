---
title: "Sed"
date: 2025-02-25
draft: false
description: "Sed examples"
tags: ["snippet", "sed"]
---

## Command list

- ranges, {}
- -n
- p/d
- ;
- =/n
- P/D/N
- a/i/c
- x/h/H/g/G
- q
- l
- y///
- s///p
- s///I
- s///w
- r
- \#
- -f

> replace pattern/regular expression with something in the file`
> this does NOT alter the file`

`$ sed 's/pattern/something/' file`

> replace pattern/regular expression with something in the file`
> this DOES alter the file`

`$ sed -i 's/pattern/something/' file`

> replace test with Test
> this only replaces the first occurance in each line

`$ sed 's/test/Test/' file`

> replaces test globally

`$ sed 's/test/Test/g' file`

> you can replace / with anything you want
> very useful when you want to replace slaces so you don't have to escape them like \/

`$ sed 's_test_Test_' file`

> replace every test that is in the beginning of the line

`$ sed 's/^test/Test/g' file`

> replace every test that is in the end of the line

`$ sed 's/test$/Test/g' file`

> replace pattern/regular expression with itself

`$ sed 's/test/&/g' file`

> ignore case

`$ sed 's/test/Test/Ig' file`

> find exact match (whole word)
> define boundaries

`$ sed 's/\btest\b/Test/g' file`

> delete every line that includes pattern/regular expression

`$ sed '/pattern/d' file`

> show only first n lines. e.g. first 5 lines

`$ sed '5q' file`

> delete lines n through m, e.g. 4 through 5

`$ sed '4,5d' file`

> ignore first line in file`

`$ sed '1!{s/test/Test/g}' file`

> print line number before each line

`$ sed '=' file`

> print lines numbers without anything else

`$ sed -n '=' file`

> print last line number without anything else

`$ sed -n '$=' file`

> count lines in a file`
> same as before but append the actual line after the line number
> by replacing every new line character with a space

`$ sed '=' file | sed 'N; s/\n/ /'`

> count lines in a file`
> Don't show empty lines

`$ sed '/./=' file | sed '/./N; s/\n/ /'`

> print every other line

`$ sed 'n;d' file`
`$ sed -n 'p;n' file`

> print evry other line. Start with the 2nd

`$ sed '1!n;d' file`

> print every 3rd line

`$ sed -n 'p;n;n' file`
