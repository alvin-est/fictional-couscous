# RegEx Short & Sweet Guide

Welcome! At first glance, regular expressions can be very daunting. But, at the same time, they are often used in the development world due to its power and simplicity.

In this guide, we will walk you through on its concepts and components. 

But first! A quick history lesson:
>*In the realm of computing, where machines were just beginning to grapple with the complexity of human language, a hero emerged from the abstract world of mathematics. This hero was not a person but an idea - **regular expressions**, conceived by Stephen Cole Kleene in the 1950s.*  

> *Kleene, with his mathematical mind, crafted a language for machines to understand and manipulate text, not with the brute force of code, but with elegance and precision. Yet, this idea remained in the theoretical shadows until Ken Thompson, a visionary at Bell Labs, breathed life into it in the 1960s. He crafted regex into the **ed** editor, allowing computers to search and edit text with unprecedented finesse.* (excerpt)

## Summary

A gist guide into the world of regular expressions. We will explain how it functions and break down each part of the expression to explain what it does.

## Table of Contents

**Regular Expressions**
- [RegEx as a String](#regular-expressions)
- [Component Breakdown](#component-breakdown)

**Further Information**
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

## Regular Expressions
### As a String
Here's an example regex to start. This will match an email:  
>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

In the section below, we will learn how it works.

### Component Breakdown

> **Component**: 
> `/ ... /`

**Description:** The dual slash is notation used at the start and end of what is called a 'literal.' This represents the nature of the regex.

> **Component**: 
> `^ ... $`

**Description:** The `^` and `$` at the start and end of the regex are called *<ins>anchors</ins>*. The former signifies that any subsequent character is part of the string we want to match. The latter signifies that any preceding character is part of this aforementioned string. Together, they work similar to HTML opening and closing tags.

> **Component:**
> `( ... )`

**Description:** The round brackets represent what is called a *<ins>grouping construct</ins>*. It allows us to divide the string into different sections that can fulfil different requirements. It is used similar to its use in arithmetic:

eg. (1+1) - (2*3)

Whereas in arithmetic each bracket may have different operations, in regex each bracket may have different matching requirements.

> **Component:**
> `[ ... ]`

**Description:** The square brackets defines a set of characters where any one of the characters inside it can be a match.

> **Component:**
> `[a-z0-9_\.-]`

**Description:** This specific component aims to match any lowercase character from a-z as well as numbers 0-9, underscores, dots, or hyphens.

In simple terms, it will find any alphanumeric lowercase string that may also include those special characters mentioned.

eg. alvin-est007 will be a match

> **Component:**
> `+`

**Description:** This is a *<ins>quantifier</ins>* used to match the preceding element at least one or more times. It is telling us that we can have multiple occurences of the defined string requirement.

> **Component:**
> `@`

**Description:** This is a string 'literal' requirement used to match the @ character. It tells us that after the preceding pattern, there should be a subsequent @ character in the string to match.

> **Component:**
> `([\da-z\.-]+)`

**Description:** The `\d` matches any digit 0-9 similar to using `[0-9]`. The `a-z` will simply match any lowercase characters. The `\.` is simply a period. The slash represents an escape so the period is treated as a character literal instead of its special meaning in regex. The `-` is also a character literal. However, as it does not have a special meaning in regex, it does not need to be escaped with a slash.

Simply put, this tells us to match any alphanumeric lowercase strings that may have a period or a hyphen (or both).

This will be useful for capturing the domain name or its sub-domains.

eg. maps.google(.com) or alvins-website(.com)

It does not match the TLD which is the last part of the domain name. That will be explained in the next component.

> **Component:**
> `\.([a-z\.]{2,6})`

**Description:** The `\.` is an escaped period. As before, it represents the character literal. The `[a-z\.]` matches any lowercase alphabetical characters that may also have a period. The `{2,6}` part specifies the preceding requirements should occur between 2 and 6 times.

eg. .com or .com.au

## Further Information

### Anchors

- **`^`**
- **`$`**

These match the start and end of the string.

### Quantifiers

- **`+`** : One or more occurrences.
- **`?`** : Zero or one occurrence of the preceding element.
- **`{n}`** : Exactly n occurrences.
- **`{n,}`** : At least n occurrences.
- **`{n,m}`** : Between n and m occurrences.
- and more..

Defines the requirements for the occurrence of the string.

### OR Operator

- **`|`**

This will match either expression on the left or right.

### Character Classes
- **`[abc]`** : Matches any character within the brackets.
- **`[^abc]`** : Matches any character not in the brackets.
- **`\d`** : Matches any digits (numeric).
- **`\D`** : Matches any non-digit (non-numeric).
- **`\w`** : Matches upper and lower case alphanumeric.
- **`\W`** : Matches any special characters.

### Flags
- **`g`** : Finds all matches, not just the first.
- **`i`** : Matches become case-insensitive.
- **`m`** : Allows for multi-line matches.
- **`s`** : Lets `.` match newline characters.
- **`u`** : Enables unicode support.
- **`y`** : Looks for a match only at the last index.

When specified, these flags change the default match behavior of the regular expression.

### Grouping and Capturing

- **`( ... )`**

As specified above, allows the creation of groups for operations.

### Bracket Expressions

- **`[ ... ]`**

As specified above, creates a set of characters. Useful for specifiying a range.

### Greedy and Lazy Match
- **`Greedy`** : Match as many times possible.
- **`Lazy`** : Match as few times possible.

Specifies the behaviour of the regular expression.

### Boundaries

- **`\b`, `\B`** : Defines where words begin or do not begin.

These can be used to ensure matching a whole word, as opposed to parts within a word.

### Back-references

- **`\1`, `\2`** : References previously matched groups within the same regex.

Useful for matching duplicated words (eg. yo-yo) and to ensure both are the same.

### Look-ahead and Look-behind

- **`(?=...)`, `(?!...)`, `(?<=...)`, `(?<!...)`**

A look-ahead will traverse the string from the beginning of the line a while look-behind will start from its end.

## Author

Thank you for reading! 

If you have any questions, please contact me at [contact@alvin-the.dev](mailto:contact@alvin-the.dev). You can also find me on GitHub at [@alvin-est](https://github.com/@alvin-est).  
