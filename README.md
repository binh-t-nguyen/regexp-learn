# Regular Expression Learning Notes
## Basic Set:
### Wildcard:

**fooa\*bar**: 0,1, or multiple 'a's between foo and bar
```
>grep 'fooa*bar' regex01.txt
```

**foo.bar**: exactly one character between foo and bar
```
>grep 'foo.bar' regex02.txt
```

**foo.\*bar**: 0, 1 or multiple characters between foo and bar
```
>grep 'foo.*bar' regex03.txt
```

**foo\s\*bar**: 0, 1 or multiple spaces between foo and bar
```
>grep 'foo\s*bar' regex04.txt
```

### Character Classes:

*Character class is staying in between []*

**[f,d,l]oo**: word starting with either f,d,l
```
>grep '[f,d,l]oo' regex05.txt
```
*Notes: if there is ^ inside [] and at the beginning, it means negate*

**[^m,h]oo**: word must not start with either 'm' or 'h'
```
>grep '[^m,h]oo' regex06.txt
```

**[j-m]oo**: word starts with one character in the range from 'j' to 'm'
```
>grep '[j-m]oo' regex07.txt
```

**[j-mz]oo**: word starts with one character in the range from 'j' to 'm' or outliner character 'z'
```
>grep '[j-mz]oo' regex08.txt
```

**[j-mJ-Mz]oo**: word starts with one character in the range from 'j' to 'm' or from 'J' to 'M' or outliner character 'z'
```
>grep '[j-mJ-Mz]oo' regex10.txt
```

**x\*\\.y\***: 0 to mulitple 'x's followed by . and then followed by 0 or multiple 'y's
*Notes: the \\. is an escape of .*
```
>grep 'x*\.y*' regex11.txt
```

***x[#:.]y***: one character between x and y. It could be either #, :,.
*Notes: inside the [], the . does not have special meaning (like wildchar) so it is treated as literal*
*The -, ^ have special meaning inside [] so it needs to be escaped if we need to use it*
```
>grep 'x[#:.]y' regex11.txt
>grep 'x[#:\^]y' regex12.txt
>grep 'x[#\\\^]y' regex13.txt
```

### Anchors:

**^foo.\***: lines starting with 'foo' and followed by any characters
```
>grep '^foo.*' regex15.txt
```

**.\*bar$**: lines starting with any characters and ending with 'bar'
```
>grep '.*bar$' regex16.txt
```

**^foo$**: lines starting and ending with foo
```
>grep '^foo$' regex17.txt
```

## Extended Set:

### Repeater:
**^\[0-9]{3}$**: lines starting with 3 digits.
*Notes:* the {3} tells the regexp engine repeat the search 3 times
```
>grep '^\[0-9]{3}$' reg18.txt
```
