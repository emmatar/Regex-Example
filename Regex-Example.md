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
- `^` The beginning of a search string. <br/>
- `$` The end of the string.<br>

Extras: 
-   `\b` A word boundary.
-   `\B` Not a word boundary.

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
/^([a-z0-9_\.-]+)@([`\d`a-z\.-]+)\.([a-z\.]{2,6})$/

Character classes will match a character from a specific set. Although, there are many default classes you can choose from (bracket expressions, from the above section, are considered a character class), a user can define their own set of character classes. <br/>
Some examples below:

-   `[ABC]` Character Set: Matches any character in the set.
-   `[^ABC]` Negated Set: Matches any character that is not in the set.
-   `[A-Z]` Range: Matches any character between the two specified characters inclusive.
-   `.` Dot: Range: Matches any character except linebreaks.
-   `[\s\S]` Match Any: Matches any character, including line breaks, without the dotall flag (s).
-   `\d` Digit: 
-   `\D` Not Digit
-   `\s` Whitespace
-   `\S` Not whitespace

In our email example above, we can see that in the second capture group `([\da-z\.-]+)` that `\d` (digit) is being used FIRST in the bracket expression. The `\d` tells the engine to recognize any digit 0-9 (another way of writing this would be `[0-9]`).

### The OR Operator
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Although not present in this email example, the OR operator `|` acts like a boolean, where it matches the expressions before or after itself. Most of the time, this operator can be seen used within a group, but it can also be used on whole expresssions. <br>

For example, `(a|b|c)` will search for anthing with a, b, OR c.
-   "`B`endy str`a`ws `a`re kind`a` `cool."

### Flags
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Regex flags can change how the expression is interpreted. Flags follow the closing forward slash of the expression (Ex: /[abc]/`igm`). Although optional, flags allow functionality like searching for characters globally, with case-insensitivity, in multiple-lines, and more! Unfortunately, our email example doesnt include any flags shown so we shall create some for us!

-   Example: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`gi`<br>

`gi` are the flags included on this regex. `g` makes the expression search for all occurrences, while, `i` makes the the expression search case-insensitive. Other flags include: `m` Multi-line, `s` Dot All, `y`, Sticky, and `u` Unicode.


### Character Escapes
/^([a-z0-9_`\.`-]+)@([`\d`a-z`\`.-]+)`\.`([a-z`\.`]{2,6})$/

Character escapes represent a character that may not be able to access its literal form. The great thing about character escapes is that they all start with a backslash `\`. In our regex email example, we can see the escape infront of the periods `\.` and also, infront of our digit character `\d`. Naturally, if we were to just use `.` in our regex, the engine will make matches with any and all characters with the exception of linebreaks. If we just want to match our search for single periods, we will have to use an escape `\` in order to tell the engine not to use the dot implementation (that selects all) but instead read the periods as themselves.

Example:<br>
- Lets say we have a document, and we want to search for anything that is a word. Naturally, if we were to enter `[w]` in our search, our response would bring back all w's in the document, but thats not what we want. In order to return anthing that is a word, we can use a character escape on the 'w', like so: `\w`. When the escape is implemented, 'w' no longer registers as the letter 'w', but now tells the engine that its value is every word! This is how character escapes can change the behavior of character tokens.<br>

## Author

Hi! My name is Elijah, and I am a student seeking knowledge in the field of software development through the KU Bootcamp. Cheers!

GitHub Account: [emmatar](https://github.com/emmatar)

