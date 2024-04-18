# Regex Example
This regex example is intended to help understand how the sequence of characters/special characters work together to verify a search term.<br /> 
A <b>Regex</b> is a sequence of characters that defines a specific search pattern.


## Summary
The cool thing about a regex is that you can search for practically any arrangement of characters. The counterpart to having such access to searches is that the arrangement of characters and symbols can get kind of confusing. This is when we enter in! The code below will be used as the example regex that we will be breaking down to hopefully make these cute, scary expressions much easier to understand!

Example Regex:<br />
Matching an Email:<br/>

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
/`^`([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})`$`/ <br/>

Anchors are what start and end a regular expression (regex). In the example above:
- `^` indicates the beginning of a search string. <br/>
- `$` Indicates the end of the string.


### Quantifiers
/^([a-z0-9_\.-]`+`)@([\da-z\.-]`+`)\.([a-z\.]`{2,6}`)$/

Quantifiers indicate that the preceding character must be matched a certain number of times. By default, quantifiers are greedy, and will match as many characters as possible. So let's take `abc+` for example. The engine will see this and match any string with `ab` followed by at least one `c` or more if any are present.<br/>
Now, lets take a look at our email example. There are two different types of quantifiers present: 

1) ([a-z0-9_\.-]`+`) <br/>

This will match any string that contains `a-z`, `0-9`, `_`, `.`, or `-`. The quantifier + means that it has to contain at least one of these in order to have a match.

2) ([a-z\.]`{2,6}`)

This will match any string that contains `a-z` and `.` but will be limited to any result that has 2-6 characters in length. The quantifier `{}` allows you specifiy the quantity of length that the preceeding characters must match. `{1,3}` will match 1 to 3. `{3}` will match exactly 3. `{5,}` will match 5 or more.

### Grouping Constructs
/^`([a-z0-9_\.-]+)`@`([\da-z\.-]+)`\.`([a-z\.]{2,6})`$/

Grouping allow us to group multiple characters together using parentheses `()` that creates a capture group. With this capture group, we are able to do a couple of things. One of them being, we can isolate a substring within the group. Secondly, we can implement a backreference on any substring or  full group as a whole.

Referencing the example above,<br/>

`(`[a-z0-9_\.-]+`)`@<br>

These parentheses have created a capture group on `[a-z0-9_\.-]+`. The usefulness of these capture groups is that the parentheses tell the engine that any characters within these parenthesis have to match before the engine moves on to the next character/s (in this case `@` would be next to be read).

### Bracket Expressions
/^(`[`a-z0-9_\.-`]`+)@(`[`\da-z\.-`]`+)\.(`[`a-z\.`]`{2,6})$/

Bracket expressions `[ ]` are used to match any character in the set (brackets). Not only can we match one character, but we can target a range of them. 
Guidelines for matching characters include: <br>

-   `[abc]` - Matches any character in the set<br>

    -   Example: "This is `a` `c`ool pot`a`to."
-   `[e-p]` - Matches any character that is between two specified characters inclusive<br/>

    -   Example: "abcd`efghijklmnop`qrstuvwxyz"
-   `[3-8]` - Matches any character that is between two specified characters inclusive<br>

    -   Example: "12`345678`9"
-   `[-]`,`[_]`,`[\.]` - Matches `-`,`_`,`\.`<br>

    -   Example: "Hey, this is a short`-`term plan."



### Character Classes
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/


### The OR Operator
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/


### Flags
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/


### Character Escapes
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/



## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
