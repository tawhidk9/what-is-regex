# What in the code is Regex?

A jumble of characters. An enigma of symbols. A disARRAY (ha) of seemingly random letters, numbers, and special characters that strike fear (or at the least some worry) into the minds of even the most seasoned developers. But lets take a deep dive of Regex and look at this complex language in smaller, more digestable bits.

## Summary

A Regex (cooler way of saying Regular Expression) is a sequence of letters,numbers, and symbols that match character combinations. Usually these combinations are used by string-searching algorithms for "find" or "find and replace" operations on strings. Pretty handy stuff!

But lets actually look at some regex shall we? The code below is an example of regex that matches an HTML tag!

`/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

Scary stuff right? But fear not! All it takes is a calm mind, sharp eye, and some metaphorical elbow grease to figure out how regex works!



## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
At its core Regex is made of a mish mash of different **components** that make up a realively short piece of code, but with a massive range of applications such as adding/removing data or strings. Lets take a look at the components.

### Anchors

Akin to GPS coordinates, Anchors help locate specific positions in the text! Anchors denote the beginning and end of a line with hard boundaries (or delimiters).

* Within the example: `/^<([a-z]` AND `|\s+\/>)$/`
    * Caret (^) matches the start of a string.
    * Dollar sign ($) matches the end of a string.


* `/`
    * Forward slashes are akin to angle brackets in HTML. It is often used to encase a regex pattern. 


Bonus Info: MORE Boundaries!

* `\b` and `\B`	
    * `\b` Essentially matches the transition between a word character ('\w') and a non-word character ('\W')
    * `\B` Is very much the negation of \b. It matches any position in the text that is not a word boundary.

### Quantifiers
Quantifiers specify the number of times a character or group of characters should occur in a pattern! Just as a tape measure will measure length with inches/centimeters, Quantifiers are essentially the measuring stick of regex.

Asterisks ( * ) matches zero or **more** occurrences of the preceding character or group.
* Within the example: `([a-z]+)([^<]+)*`

Plus signs ( **+** ) matches one or more occurrences of the preceding character or group.
* Within the example: `([a-z]+)([^<]+)`

Question marks ( **?** ) matches zero or ***one*** occurrence of the preceding character or group.
* Within the example: `(?:>(.*)`            

Curly braces ( **{}** ) specify the exact number of occurrences or a range.
* None in the example. 


### OR Operator
Denoted by the pipe symbol ( **|** ), OR Operators essentially specify multiple **ALTERNATIVE** patterns! Much like if/else statements, OR Operators are read from left to right (in the case of if/else top to bottom). Once a match is found, it stops the search!

* Within the example: `<\/\1>|\s+\/>`

### Character Classes
Character classes allow you to define a set of characters to match! Similar to organizing a closet and grouping items based on shared attributes.

* `\d` matches any digit (0-9).

* `\w` matches any alphanumeric character (a-z, A-Z, 0-9, and underscore _).

* `\s` matches any whitespace character (space, tab, newline, etc.).

### Flags
Regex flags are modifiers that affect how regular expression patterns are matched. Very similar to how wearing different types of glasses or lenses when observing the world around you. Each flag modifies how you perceive and interpret what you see in the code. 

* Case Insensitivity (`i`): The `"i"` flag makes the pattern match regardless of letter case. It allows uppercase and lowercase letters to be treated as the same. For example, `/regex/i` would match `"regex"`, `"Regex"`, `"REGEX"`, etc.

* Multiline Matching (`m`): The `"m"` flag enables matching of patterns across multiple lines. By default, regex matches operate on a single line, treating line breaks as regular characters. However, with the `"m"` flag, you can match patterns across multiple lines.

* Global Matching (`g`): The `"g"` flag allows the pattern to match multiple occurrences within the text rather than stopping after the first match. It enables a global search that continues beyond the initial match.

### Grouping and Capturing
Groups can be used for capturing specific parts of a match or for applying quantifiers to multiple characters. Not so different than a container in the sense that they allow the isolation and extration of certain elements. Think of separating different ingredients when cooking!

* G&C is denoted by Parentheses `()`
    * The example itself is grouped and has multiple groupings within it!  `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

### Bracket Expressions
Bracket expressions are very much similar to Character Classes! Almost like a menu at a restaurant, bracket expressions represent the available options in the regex code. 

* Positive Character Class: A positive character class matches any single character that is within the specified set of characters. It's represented by square brackets `[ ]` enclosing the characters. For example, [`aeiou`] matches any vowel character.
    * Within the example: `[a-z]`

* Negative Character Class: A negative character class matches any single character that is not within the specified set of characters. It's represented by square brackets with a caret [ `^` ] preceding the characters. For example, [`^aeiou`] matches any consonant character.
    * Within the example: `[^<]`

* Character Ranges: Bracket expressions can also include character ranges to define a consecutive range of characters. For example, [`0-9`] matches any digit from `0` to `9`.


### Greedy and Lazy Match

Greedy and Lazy Matches are a fun concept in regex!

Greedy matches are very much like someone who overpacks for a vacation (we all know one). Greedy tries to match as much of the pattern as possible, consuming as many characters as it can. It matches the longest possible sequence that satisfies the pattern.

Lazy matches are the inverse of Greedy! Lazy matches aren't concerned with overpacking. In fact, Lazy Matches just pack the bare necessities. It matches the shortest possible sequence that satisfies the pattern. It stops as soon as it finds a valid match, without consuming any additional characters.

Heres a link to some nifty examples: https://javascript.info/regexp-greedy-and-lazy

### Boundaries
Refer to Anchors!

### Back-references
Back references allow you to, you guessed it, reference back to prevously matches portions of a pattern (within the same expression).

Backreferences are commonly used to ensure that the same content appears multiple times within a string. For example, if you want to find repeated words, you can use a backreference to `match` the same word that was previously captured. They are like `little arrows` pointing to earlier captured text, enabling you to `replicate` and work with repeated patterns within a string, very much like using backreferences to recreate patterns within a puzzle.

A more thorough explanation: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Backreference

### Look-ahead and Look-behind
Look-aheads and Look-behinds act as `virtual lenses` that let you examine the text `ahead` or `behind` the current position, ensuring certain conditions are met or not met `without including` the viewed patterns in the final match. They are useful for asserting certain conditions that `should or should not` be met in relation to the current position in the text.

More info on Look-ahead and Look-behind: https://javascript.info/regexp-lookahead-lookbehind

## Author

Tawhid Kamal (https://github.com/tawhidk9)