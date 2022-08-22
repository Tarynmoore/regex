# Regex Tutorial

When coding you may run across a Regex, or a regular expression. 
A regex looks like a toddler banged their hands on the keyboard but in reality its a sequence of characters that define a specific search pattern. Regex's pattern must be wrapped in slashes (//). This is because it is considered a literal. 

Regex can be helpul when wanting to get information from a document or a database. This tool can be used in almost all programming languages as well. 

## Summary

The Regex we will be breaking down is used to match an email. 
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
This is what is used to match an email. When you first look at it it's not easy to understand what this is trying to say. 
In this tutorial I am going to break down this email regex and explain all the contents of a regex to help further understand what this pattern does and how to possibly read other regex's. 

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

Email example 
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

### Anchors 
The ^ and $ characters are called anchors. The ^ anchor is a string that begins with the characters that 
come after the ^ anchor. An example would be ^Food, the string would be "Food". Keep in mind regex is case sensitive so if you are trying to search for an something that was "food" it would not match this regex. 
The $ anchor is the string that is on the end of the regex. 
In our example the ^ anchor is followed by [a-z0-9_\.-] and the $ anchor has before it {2,6}

### Quantifiers
Using a quantifier sets the limit on the string that is being used in your regex. They also match as many occurences as possible, in regards to the pattern. Quantifiers include:
+ (+) = Matches the patter one or more times. 
+ (?) = Matches zero or one time. 
+ (*) = Matches zero or one time. 
+ {} can be used 3 different ways 
    + { n } = Matches exactly n number of times. 
    + { n, } = Matches pattern at least n number of times. 
    + { n, x} = Matches a minimum of n times to a max of x number of times. 

In our example we have {2,6} at the end of the regex. (Notice it is before the $ anchor) This means that we can find a pattern 2-6 times which indicates that our string has to be between 2-6 characters long. 

### OR Operator
When using square brackets it only searches for what is inside of the pattern. Sometimes you'll want to do the same logic outside of the bracket expression. This should be used within a grouping construct or between different groupings. 
The OR operater uses the (|) which would look like this, (a|b|c) which is the same as writing [abc].  
We do not have any OR Operators in our expression. 
This acts like an "or" statement. 

### Character Classes
These are used to define a set of characters that can occur in an input string to fulfill a match. Examples of character classes:
+ (.) = Matches any chracter except the new line character. 
+ (\d) = Matches numbers. This is equal to [0-9].
+ (\w) = Matches alphanumeric characters including the underscore. This is equal to [A-Za_z0-9_]
+ (\s) = Matches single whitespace characers. This inclues tabs and line breaks. 

In the last three examples you can change the letters to capital letters it creates an inverser of what you're trying to do. For example \D matches any non number characters. 
In our example we have a character class in the middle, [\da-z\.-]. This means that our pattern can include all numbers along with letters a-z and specified special characters. 
### Flags
These are placed at the end of the regex's, after the second slash. These define additional funcionality or limits on the regex. Examples of flags: 
+ (g) = Global Search. Meaning the regex should be tested against all possible matches in the string. 
+ (i) = Case-insesitive search. This means that uppercase and lowercase matches should be ignored. 
+ (m) = Multi-line search. This multiple line input should be treated as multiple lines. 

Flags can be used seperately or together in any order. 
We do not have any flags in our example. 

### Grouping and Capturing
This can be used to get information from strings or data. This is used with parentheses (). Here are some examples: 
+ a(bc) = captures the group with the value bc in the pattern. 
+ a(?:bc) = disables the capturing group. 

Not in our example. 

### Bracket Expressions
When you put characters inside [] it shows us the range of characters that our regex can fall into. They almost act like an outline of what characters we can use in our regex. 
If you place the characters [a-t] in a regex that means you can only use the letters [a-t]. The same goes for numbers. Just because the bracket requires has all letters and all numbers doesn't mean we have to use all of them. It's just what could be used in the pattern. 
In our example we have a couple of brackets. 
First we have [a-z0-9_\.-] meaning that we can use all the letters in the alphabet, all numbers, and include special characters including [_\.-] in our email address. 
The second set of brackets we have is [\da-z\.-] 
The \d matches any single digit, meaning this section could have any number, letters a-z and the special characters that are defined. 
The third set of brackes is [a-z\.] which means it can contains letters a-z and the characters \.  

### Greedy and Lazy Match
Using a greedy match is what is typically used by default. In the greedy mode a quantified character is repeated as many times as possible. Meaning it will go through the pattern and backtrack by each letter in the string until it finds what the pattern is matching. Once it finds the last character it is searching for it will stop it's search and return what is inside of the string. 

A lazy match is repeated as minimal number of times. This means it will move throught the pattern character by character until it find's its match. 
In our example we are only using greedy matches. 

### Boundaries
Uses the character (\b) is also considered an anchor. It matches a position that is considered a word boundary. The word boundary match has zero length. 
There are three positions that are qualifies as word boundaries:
+ If the first character is a word then it can be before the first character. 
+ If the last character is a word then it can be after the last character. 
+ It can be between two characters in a string if one is a word character and the other is not. 

We do not have boundaries in our example. 

### Back-references
A back-refernce is used to match the text previously matched by a capturing group. This can be used to make sure two pieces of a string match. 

### Look-ahead and Look-behind
These are used to match characters, and returns only one result match or no match. These are called assertions. They go through the characters but only assert whether a match is possible or not.

Look-Ahead's can be positive and negative. A negative lookahead won't work if you want something to match that is followed by something else. Negative lookahead is used with a pair of parentheses with the opening parenthesis followed by a question mark and exclamation point. Here's an example 
r(?!t) 
This would return the letter 't'.
A positive lookahead works the same. However, it is constructed with parentheses, with the opening parenthesis followed by a questions mark and an eqal sign. An example would be
r(?=t)
Which would also return the letter 't'.

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
