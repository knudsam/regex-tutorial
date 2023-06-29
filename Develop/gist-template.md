# ReGex Tutorial When Matching a URL

Regular Expressions (Regex) can be used when one is trying to match a certain character combination within a string. This is great for pulling out information from a given body of code as well as being used for validation. For example, this tutorial will follow an example code snippet that can be used to match a URL. This tutorial will follow the different components of regular expressions.

## Summary

The following code will be used throughout the tutorial to give specific examples for how the components of regex can be used. The following code can be used for matching a URL. One use for this code is that it can be used to validate to make sure that a URL follows the correct format.

Matching URL-

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

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

The two principal anchors in this regex expression are the ^ at the beginning and the $ at the end which constitute an exact string match with the components included within the two anchors. When used alone, the ^ anchor matches any string that begins with the characters that follow the anchor. The $ matches any string that ends with the characters that precede it. By enclosing the regex between these two anchors, we are asking the search function to match exactly is included between them.

### Quantifiers

Notice that some of the components of capture groups end with a ? or a *. These are generally known as quantifiers. Quantifiers are used to define the number of times a given expression may be identified. The ? makes a single instance of the character preceding the quantifier optional, whereas the * makes multiple instances of the characters preceding the quantifier optional. For example, the grouping

(https?:\/\/)?
contains two ? quantifiers. This expression is looking for an http:// OR an https://. For this reason a single internal s is optional. The same is true for the entire expression included in the parenthesis, for which reason it is followed by a ?. In other words, a valid URL may begin with http:// OR https://, or it may not begin with either of them at all (the input begins with www.). The same applies for the / at the very end of the expression.

Similarly, the * makes the expression optional, but in this case it may be one or more instances that are optional. So if we look at the fourth grouping:

([\/\w \.-]*)*
The expression is allowing for any number of filepath characters that may follow an initial specified domain.

Finally, the {} quantifier defines a range of possible instances where a match may be identified. In evaluating the Top level domain, the regular expression allows for the top level domain to consist of 2 to 6 characters.

### Grouping Constructs

So what is included between the two anchors. If we examine the expression, we can see that there are a number of components separated by parentheses (). Parentheses are used in regex to create separate groups of interest. Within each of these groups, there is a regex that we may look at separately to see what is evaluated. These include:

the initial https component: (https?:\/\/)
the domain name (e.g. www.google, or pets): ([\da-z\.-]+)\.
the top level domain (.com, .gov, etc): ([a-z\.]{2,6})
the file path: ([\/\w \.-]*)*

### Bracket Expressions

Anything inside a set of square brackets ([]) represents a range of characters that we want to match are called 
bracket expressions. 

[a-z]—The string can contain any lowercase letter between a–z. Keep in mind that this looks for lowercase characters only. If we wanted to include uppercase characters, we would need to change the expression to [a-zA-Z].

[0-9]—The string can contain any number between 0–9

[_-]—The string can contain an underscore or hyphen. Both the underscore and the hyphen are called special characters. Special characters include any non-alphanumeric characters, such as punctuation or symbols. In this case, we only want a string that includes _ or -. It's important to note that the hyphen here is not the same hyphen that we used in our alphanumeric ranges. In bracket expressions, special characters that we want to include follow alphanumeric character ranges within the brackets.

In our URL expression we have three different sets of bracket expressions. 

[\da-z\.-] - The first bracket expression how we are looking for string featuring a decimal point followed by any letters a-z, 
followed by any character except the newline character (.), and this string can contain an underscore or hyphen. 

[a-z\.] The second expression is looking for a string that has any letters a-z, followed by a characture class (.), which means
any matches of a character except the newline character. 

[\/\w \.-] The last bracket expression is looking for a sting that has a / slash , a /w - word characture, character except the 
newline character (.), and the string can contain an underscore or hyphen. 

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/ 

### Character Classes

A character class in a regex defines a set of characters, any one of which can occur in an input string to fulfill a match. 

.—Matches any character except the newline character (\n)

\d—Matches any Arabic numeral digit. This class is equivalent to the bracket expression [0-9].

\w—Matches any alphanumeric character from the basic Latin alphabet, including the underscore (_). This class is equivalent to the bracket expression [A-Za-z0-9_].

\s—Matches a single whitespace character, including tabs and line breaks

### The OR Operator

The main OR operator used in the above regex is the []. The expression will match for any characters or character classes included in the brackets. For example the [\da-z\.-] expression matches for any digits (\d) OR any characters between a and z (a-z) OR any '.' (\.) OR any '-' (-).

### Flags

Flags can be used to make your search even more specific. Using optional flags can allow you to search globally, multi-line,
case insensitive and more. These flags can be used separately or together.

In our example we do not have any added flags but if we wanted to add a flag to look at the global scale
it would look like this:

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*, 'g')*\/?$/

### Character Escapes

A character escape comes in the form of a backslash. The backslash (\) in a regex precedes a character and "escapes" them 
as to not be taken literally. It can change the meaning of the character. You can escape literal or common character classes.  

For \w in our example, having the backslash would be shorthand for looking up a word character [a-zA-Z0-9_]. 
\. would be a period (special character: so it needs to be escaped by a \). Without the escape the . could mean any 
character except for a line break. 

## Author

Samantha Knudsen studied web development at Rutgers University in 2023. To view more of her work, you can visit her GitHub Profile.
