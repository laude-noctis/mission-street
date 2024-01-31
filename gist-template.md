# Mission Street (Explaing an Email Regex)
What is a regular expression? Well, a regular expression (or most commonly known as regex) is a string of characters that make up a search pattern. It uses special characters to look for different criterias. The one in which we will be dechiphering today is an email regex:  
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`  
It looks like nonsense right now but after you read this explaintion, you will read it with ease!
## Summary 
The email regex is used to validate email addresses. It consists of several components to make sure that it fits the basic standardized email pattern. It uses multiple regex components to match the username (`([a-z0-9_\.-]+)`), the literal `@` symbol, the main domain name (`([\da-z\.-]+)\`), and the top level domain (`\.([a-z\.]{2,6})`).  
`coolguy-12@gmail.com`  
`percy_blue@gmail.com`  
`annabeth.books13@gmail.com`  
These emails would all be matched by our regular expressions.  
This regex consists of the components anchors, quantifiers, character classes, character escapes, gourping and capturing, and bracket expressions.
In this explantion we will be breaking down each of these components of the regex.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)

## Regex Components
Regex components are what make up an expression. They are building blocks used to make the construct the regular expression. They are the rules and pattern for searching and matching the text to the string. There are many different kinds of components in the world of regex, such as the Literals. These are characters in which they match themselves. For example, regex `abc` will only match the "abc" string. Literals are also case sensitive by default, so the literal `cat` will only match "cat" and not "Cat" or "CAT".

To use regex in code (JavaScript), you will need to enclose the expression in `/` so that JavaScript will read it as a regex.
Now, let's discuss all the components in the "Mathing an Email"

### Anchors
This regex includes two anchors `^` and `$`.  
The `^` is used to search for anything that follows it. Such as, `^Ex` would only return every instance of a word beginning with "Ex", ex. *Ex*plain, *Ex*plore, or *Ex*stend. It would not include *ex*plain, *ex*plore, or *ex*stend due to regex being a case sensitive language.  
The `$` is used to search for anything that ends with the expression that precedes it. Such as, `thing$` would return any word that ends in 'thing', ex. 'some*thing*', 'any*thing*', or 'brea*thing*'.  
So the "Matching an Email" uses these to make sure anything in `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.])$/` begins and ends with anything that matches the pattern within the components. Now the `{2,6}` is not included because it is what is known as a quantifier.
### Quantifiers
Quantifiers! A quantifier will set limits to what will match your string or a certain part of your string. The quantifier `{2,6}` is saying anything between 2 and 6 characters long will meet the criteria.  
There are multiple quantifiers:  
`*` will match the pattern 0 or more times.  
`?` will match the pattern 0 or 1 time.  
`+` will match the pattern 1 or more times.  

The `+` quantifier is being used in the first section (username) of the email portion `[a-z0-9_\.-]+` to say that this pattern should match one or more occurences of the characters within the brackets.

Curly brackets `{}` can decides the limit to the criteria that will match:  
`{ x }` will match the exact amount of `x` times.  
`{ x, }` will match the minimum amount of `x` times.  
`{ x, y }` will the match the minimum of x to the maximum of y.  

Now the `{2,6}` will only effect the criteria `[a-z\.]` of the expression since they are attached through parenthesis `([a-z\.]{2,6})`.
### Character Classes
Character classes are used to search for a wide variety of things.  
The most common are:  
- `.` = any character except a newline character `/n`  
- `/d` = any numerical digit  
- `/w` = any character that is a letter `[a-zA-Z]` and the `_`  
- `/s` = a single whitespace, including tabs and linebreaks  
By captilizing the letter classes, it will create an inverse search. `/D` will match any value that is not a numerical digit.
### Character Escapes
The `\` is the escape character. It it used to treat special characters as normal characters. Such as the `-` and `.` are both special characters. The `.` is a special character that will match any character. And the `-` inside a character class `[]` creates a character range. `[a-c]` will search for any character that is a, b, or c.  That is why we need to put the `\` in front of them so they will be treated as the literal `.` and `-`.
### Grouping and Capturing
In the email regex, there are three different groups being captured as referenced above. It uses `()` parentheses to group these parts and look for specific components of the email address.  
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` 
The username: `([a-z0-9_\.-]+)`  
The domain name (ie. gmail, yahoo): `([\da-z\.-]+)`  
The top level domain (ie. .com, .net): `([a-z\.]{2,6})`  
Now, the username and the domain name are broken up by the literl `@`; the domain name and the top domain is broken up by the literal `.` (Remember `\.` needs the `\` in front of it so the special `.` will registered as just a normal character).
### Bracket Expressions
Bracket Expressions are used to specify what kind of characters to look for using brackets `[]`. They are also considered charcter classes that we mentioned above. `[0-9]` is used to look for any number between 0 and 9. `[a-z]` will search for any lowercase letter and `[A-Z]` will search for any uppercase letters.  In the first part of the Email regex, `[a-z0-9_\.-]` is a bracket expression. `[a-z0-9]` searchs for lowecase letters and any number. `[_\.-]` looks for the literal characters of `_`, `.`, and `-`. These can be in any order, all these will meet the criteria: `test123`, `test.123`, and `test-123-test`.
## Author
I'm Lizzie and I am studying to become a full-stack-developer.  
github is [laude-noctis](https://github.com/laude-noctis) 
