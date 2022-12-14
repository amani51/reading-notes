# Class-17
## Automation
### Reading
##### Python Regular Expressions Tutorial

![](https://tutorial.eyehunts.com/wp-content/uploads/2018/09/Python-Regex-Regular-Expression-or-RE-Operations-Examples-.png)
- Regular expressions are a powerful language for matching text patterns.
The Python "re" module provides regular expression support.

- In Python a regular expression search is typically written as:

```python
import re
match = re.search(pat, str)
```

- The re.search() method takes a regular expression pattern and a string and searches for that pattern within the string. If the search is successful, search() returns a match object or None otherwise.
- Therefore, the search is usually immediately followed by an if-statement to test if the search succeeded,for example: search for the pattern 'word:' followed by a 3 letter word:

```python
import re
str = 'an example word:cat!!'
match = re.search(r'word:\w\w\w', str)
if match:
    print('found', match.group())
else:
    print('did not find')
```

- The code `match = re.search(pat, str)` stores the search result in a variable named `match`. Then the if-statement tests the match -- if true the search succeeded and `match.group()` is the matching text (e.g. 'word:cat'). Otherwise if the match is false (None to be more specific), then the search did not succeed, and there is no matching text.

- The `'r'` at the start of the pattern string designates a python "raw" string
which passes through backslashes without change which is very handy for regular
expressions.

Basic Patterns
--------------

- The power of regular expressions is that they can specify patterns, not just fixed characters. Here are the most basic patterns which match single chars:

-   `a`, `X`, `9`, `<` -- ordinary characters just match themselves exactly.
    The meta-characters which do not match themselves because they have
    special meanings are: `. ^ $ * + ? { [ ] \ | ( )`
        
    -   `.` (a period): matches any single character except newline '\\n'
    -   `\w`:  (lowercase w) matches a "word" character: a letter or digit or underscore `[a-zA-Z0-9\_]`. Note that although "word" is the mnemonic for this, it only matches single word char, not a whole word. `\W` (upper case W) matches any non-word character.
    -   `\b`: boundary between word and non-word
    -   `\s`: (lowercase s) matches a single whitespace character (space), newline, return, tab, form `[ \n\r\t\f]`. `\S` (upper case S) matches any non-whitespace character.
    -   `\t`, `\n`, `\r`: tab, newline, return
    -   `\d`: decimal digit `[0-9]` (some older regex utilities do not support but `\d` but they all support `\w` and `\s`)
    -   `^` = start, `$` = end: match the start or end of the string
    -   `\`: inhibit the "specialness" of a character. So, for example, use `\.` to match a period or `\\` to match a slash. If you are unsure if a character has special meaning, such as `@`, you can put a slash in front of it, `\@`, to make sure it is treated just as a character.

Basic Examples
--------------
The basic rules of regular expression search for a pattern within a string are:
-   The search proceeds through the string from start to end, stopping at the first match found.
-   All of the pattern must be matched, but not all of the string.
-   If `match = re.search(pat, str)` is successful, match is not `None`and in particular `match.group()` is the matching text

```python
import re

## Search for pattern 'iii' in string 'piiig'.
## All of the pattern must match, but it may appear anywhere.
## On success, match.group() is matched text.
match = re.search(r'iii', 'piiig')
print(match.group()) # output: iii

match = re.search(r'igs', 'piiig')
print(match.group()) # output: None

## . = any char but \n
match = re.search(r'..g', 'piiig')
print(match.group()) # output: iig

## \d = digit char, \w = word char
match = re.search(r'\d\d\d', 'p123g')
print(match.group()) # output: 123

match = re.search(r'\w\w\w', '@@abcd!!')
print(match.group()) # output: abc
```

Repetition
----------

Things get more interesting when you use `+` and `*` to specify repetition in the pattern

-   `+`: 1 or more occurrences of the pattern to its left, e.g. 'i+' = one or more i's
-   `*`: 0 or more occurrences of the pattern to its left
-   `?`: match 0 or 1 occurrences of the pattern to its left

### Leftmost & Largest

- First the search finds the leftmost match for the pattern, and second it tries to use up as much of the string as possible: i.e. `+` and `*` go as far as possible (the `+` and `*` are said to be "greedy"). 

Repetition Examples
-------------------

```python
import re

## i+ = one or more i's, as many as possible.
match = re.search(r'pi+', 'piiig')

## Finds the first/leftmost solution, and within it drives the +
## as far as possible (aka 'leftmost and largest').
## In this example, note that it does not get to the second set of i's.
match = re.search(r'i+', 'piigiiii')
print(match.group())# output: ii

## \s* = zero or more whitespace chars
## Here look for 3 digits, possibly separated by whitespace.
match = re.search(r'\d\s*\d\s*\d', 'xx1 2   3xx')
print(match.group())# output: 1 2   3
match = re.search(r'\d\s*\d\s*\d', 'xx12  3xx')
print(match.group())# output: 12   3
match = re.search(r'\d\s*\d\s*\d', 'xx123xx')
print(match.group())# output: 123
## ^ = matches the start of string, so this fails:
match = re.search(r'^b\w+', 'foobar')
print(match.group())# output: None
## but without the ^ it succeeds:
match = re.search(r'b\w+', 'foobar')
print(match.group())# output: 
```

Emails Example
--------------

- Suppose you want to find the email address inside the string  ' purple alice-b@google.com monkey dishwasher'. We'll use this as a running example to demonstrate more regular expression features. Here's an attempt using the pattern r'\\w+@\\w+':

```python
import re
str = 'purple alice-b@google.com monkey dishwasher'
match = re.search(r'\w+@\w+', str)
if match:
    print(match.group())
```

- The search does not get the whole email address in this case because the `\w` does not match the `-` or `.` in the address. We'll fix this using the regular expression features below.

### Square Brackets

- Square brackets can be used to indicate a set of chars, so `[abc]` matches 'a' or 'b' or 'c'. The codes `\w`, `\s` etc. work inside square brackets too with the one exception that dot (`.`) just means a literal dot. For the emails problem, the square brackets are an easy way to add `.` and `-` to the set of chars which can appear around the `@` with the pattern `r'[\w.-]+@[\w.-]+'` to get the whole email address:

```python
import re
str = 'purple alice-b@google.com monkey dishwasher'
match = re.search(r'[\w.-]+@[\w.-]+', str)
if match:
    print(match.group())
```

- You can also use a dash to indicate a range, so `[a-z]` matches all lowercase letters. - To use a dash without indicating a range, put the dash last, e.g. `[abc-]`. A caret (up-hat) (`^`) at the start of a square-bracket set inverts it, so `[^ab]` means any character except 'a' or 'b'.

Group Extraction
----------------

- The "group" feature of a regular expression allows you to pick out parts of the matching text. Suppose for the emails problem that we want to extract the username and host separately. To do this, add parenthesis `()` around the username and host in the pattern, like this: `r'([\w.-]+)@([\w.-]+)'`. In this case, the parenthesis do not change what the pattern will match, instead they establish logical "groups" inside of the match text. On a successful search, `match.group(1)` is the match text corresponding to the 1st left parenthesis, and `match.group(2)` is the text corresponding to the 2nd left parenthesis. The plain `match.group()` is still the whole match text as usual.

```python
str = 'purple alice-b@google.com monkey dishwasher'
match = re.search('([\w.-]+)@([\w.-]+)', str)
if match:
    print(match.group())   ## 'alice-b@google.com' (the whole match)
    print(match.group(1))  ## 'alice-b' (the username, group 1)
    print(match.group(2))  ## 'google.com' (the host, group 2)
```

- A common workflow with regular expressions is that you write a pattern for the thing you are looking for, adding parenthesis groups to extract the parts you want.

findall
-------

- `findall()` is probably the single most powerful function in the `re` module.
- `findall()` finds *all* the matches and returns them as a list of strings, with each string representing one match.

```python
## Suppose we have a text with many email addresses
str = 'purple alice@google.com, blah monkey bob@abc.com blah dishwasher'

## Here re.findall() returns a list of all the found email strings
emails = re.findall(r'[\w\.-]+@[\w\.-]+', str) ## ['alice@google.com', 'bob@abc.com']
for email in emails:
    # do something with each found email string
    print(email)
```

findall With Files
------------------

- For files, you may be in the habit of writing a loop to iterate over the lines of the file, and you could then call findall() on each line.
- Instead, let findall() do the iteration for you -- much better! Just feed the whole file text into findall() and let it return a list of all the matches in a single step (recall that `f.read()` returns the whole text of a file in a single string):

```python
# Open file
with open('foo.txt', 'r') as f:
  text = f.read()

strings = re.findall(r'another', text)
print(strings)
```

findall and Groups
------------------

- The parenthesis `( )` group mechanism can be combined with `findall()`. 
- If the pattern includes 2 or more parenthesis groups, then instead of returning a list of strings, `findall()` returns a list of \*tuples\*.
- Each tuple represents one match of the pattern, and inside the tuple is the group(1), group(2) .. data. 
- So if 2 parenthesis groups are added to the email pattern, then findall() returns a list of tuples, each length 2 containing the username and host, e.g. ('alice', 'google.com').

```python
str = 'purple alice@google.com, blah monkey bob@abc.com blah dishwasher'

tuples = re.findall(r'([\w\.-]+)@([\w\.-]+)', str)
print(tuples)

for tuple in tuples:
    print(tuple[0])
    print(tuple[1])
```
- Once you have the list of tuples, you can loop over it to do some computation for each tuple. If the pattern includes no parenthesis, then `findall()` returns a list of found strings as in earlier examples. If the pattern includes a single set of parenthesis, then `findall()` returns a list of strings corresponding to that single group. (Obscure optional feature: 
- Sometimes you have paren `( )` groupings in the pattern, but which you do not want to extract. In that case, write the parens with a `?:` at the start, e.g. `(?: )` and that left paren will not count as a group result.

Options
-------

- The `re` functions take options to modify the behavior of the pattern match. The option flag is added as an extra argument to the `search()` or `findall()` etc., e.g. `re.search(pat, str, re.IGNORECASE)`.

-   `IGNORECASE` -- ignore upper/lowercase differences for matching, so 'a' matches both 'a' and 'A'.
-   `DOTALL` -- allow dot (`.`) to match newline -- normally it matche anything but newline. This can trip you up -- you think `.*` matches everything, but by default it does not go past the end of a line. Note that `\s` (whitespace) includes newlines, so if you want to match a run of whitespace that may include a newline, you can just use `\s*`
-   `MULTILINE` -- Within a string made of many lines, allow `^` and `$` to match the start and end of each line. Normally `^/$` would just match the start and end of the whole string.

Substitution (optional)
-----------------------

- The `re.sub(pat, replacement, str)` function searches for all the instances of pattern in the given string, and replaces them. The replacement string can include `'\1'`, `'\2'` which refer to the text from `group(1)`, `group(2)`, and so on from the original matching text.

- Here's an example which searches for all the email addresses, and changes them to keep the user (`\1`) but have yo-yo-dyne.com as the host.

```python
str = 'purple alice@google.com, blah monkey bob@abc.com blah dishwasher'
## re.sub(pat, replacement, str) -- returns new string with all replacements,
## \1 is group(1), \2 group(2) in the replacement
print(re.sub(r'([\w\.-]+)@([\w\.-]+)', r'\1@yo-yo-dyne.com', str))
```
Reference
------------------
- [Python Regular Expressions](https://github.com/AstunTechnology)