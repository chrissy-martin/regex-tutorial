# Regex Tutorial: Validating the hexadecimal color code.

This is a tutorial for showing you how to validate hexadecimal color code using Regex. Regular expressions (regex) are a way to describe patterns in string data. While findning these patterns could be done with a call to indexOf, regex allows us to express more complicated patterns. Regex is a type of object that can be constructed with either the RegExp constructor or written as a literal by putting the pattern in forward slash (/) characters. For example:

`let re1 = new RegExp("abcd");`

`let re2 = /abcd/;`

## Summary

Regex patters are composed of simple characters, like `/abcd/`, or a combination of simple and special characters, like `/ab*c/` or `/Chapter (\d+) \ .\d */`. Simple patterns are made up of characters that find a direct match. For example, the pattern `/ing/` matches character combinations in strings only when the exact sequence "ing" occurs together and in that order. Therefore, the string `"I am singing"` would match the `/ing/` pattern but the string `"I am in good company"` would not. When searching for more than a direct match, specail characters are used. These special characters are often called “metacharacters” and most of them are errors when used alone.

This tutorial focuses on the hexadecimal color code. The hexadecimal color code, or hex color code is a 6-symbol code made of up to three 2-symbol elements. Each of the 2-symbol elements expresses a color value from 0 to 255. The code is written using a formula that turns each value into a unique 2-digit alphanumeric code. For example, the RGB code (224, 105, 16) is E06910 in hexadecimal code.

The regex of the hex color code that we are taking a look at is:  `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

This particular regex allows us to find any hex code, whether it begins with a numeral sign `#` or not, and whether it has 6 or 3 characters (digits and leters) in it.



## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)

## Regex Components

### Anchors

Anchors in regex have special meaning. They do not match any characters but instead match a position before or after the character. 

The carot `^` matches at the beginning of the text and the dollar `$` matches the end of the text. We can see that in our hex regex: /`^`#?([a-f0-9]{6}|[a-f0-9]{3})`$`/

The default of the anchor `^` or `$` is the single-line mode. In the single-line mode, the anchor `^` and `$` matches the beginning and the end of a string.


### Quantifiers

 Quantifiers in regex indicate numbers of characters or expressions to match. They frequently include the minimum and maximum number of characters that your regex is looking for. Our hex regex uses two types of quantifiers: `?` and `{n}`.

 The `?` quanitifier matches the preceding item  0 or 1 times. For example, `/e?le?/` matches the `"el"` in `"angel"` and the `"le"` in `"angle"`. In our case, since `?` is preceded by #, our expression will match either a string that begins with # or not.

 The `{n}` quantifier matches the pattern exatly `n` number of times. For example, `{10}` would match a string pattern of 10 characters. Let's take a look at our hex regex: /^#?([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/. We can see that in our pattern there are two instances of `{n}`: `{6}` and `{3}`. This means that we are looking to match our pattern first a string of 6 characters and/or a string of 3 characters.

### OR Operator

The OR operator `|` tells us that the string does not need to meet of the requirements in the pattern. For example, the expression `[ing]` could be written as `(i|n|g)`. By using the OR operator, strings with `a` OR `b` OR `c` would match. 

In our regex, take a look at where the OR operator is located: /^#?([a-f0-9]{6}`|`[a-f0-9]{3})$/

This tells us that the string we want to match has a length of 6 characters OR a length of 3 characters.

### Character Classes

Character classes define a set of characters, any of which can occur in an input string to fulfill a match. There are many types of character classes including: `.` , `\d`, `\w`, and `\s`. We only use one type of character class in our regex called bracket notation, which will be discussed later on. 

/^#?(`[a-f0-9]`{6}|`[a-f0-9]`{3})$/

### Grouping and Capturing

Grouping is used to break up different sections that may fulfilldifferent requirements to check multiple parts of a string.The primary way you group a section of a regex is by using parentheses (`()`). This is also known as a subexpression. 
Let's take a look at our regex:  /^#?`([a-f0-9]{6}|[a-f0-9]{3})`$/

Grouping constructs have two main categories: `capturing `and `non-capturing`. Capturing groups `(x)` match what is inside the parantheses and remembers the match. Non-capturing groups `(?:x)` macth waht is inside the parenthases but doesn not remember the match. Our regex is using a capturing group.

### Bracket Expressions

Bracket expressions are used to represent a range of characters that we want to match. We can write them to include all of the characters we want to include. It is common to see a hyphen used between alphanumeric characters to represent a range of possible characters. For example,` [A-Z]` is looking for a string containing any uppercase letter between A-Z. It is important to note that the characters are case sensitive. `[A-Z]` will only find uppcase letters, while `[a-z]` will only find lowercase letters. If we want to find both lowercase and uppercase letters it would look like this, `[a-zA-Z]`.

Let's take a look at out regex: 
/^#?(`[a-f0-9]`{6}|`[a-f0-9]`{3})$/

Our brackets tell us that we want our string to contain any lowercase letter between `a-f` and any number between `0-9`.


## Author

Chrissy Martin

- Github: [chrissy-martin](https://github.com/chrissy-martin)
- Email: cmart131@yahoo.com 
