Basic Regex characters | Meaning
------|------------
. | Any one single character
[ ] | Any one specified character
[ ^ ] | Not the one specified character
"asterisk" | Zero or more of the previous character
^ | If first character in the pattern, then pattern must be at beginning of the line to match otherwise just a literal ^
$ | If last character in the pattern, then pattern must be at the last of the line to match, otherwise just  a literal $



Extended Regex characters | meaning
----|----
'+' | One or more of the previous pattern
? | The preceding pattern is optional
{ } | Specify minimum, maximum or exact matches of the previous pattern
/<this but straight | Alternate - a logical 'or'
( ) | Used to create groups




| Regex Pattern | Use |
| --- | --- |
| [0-9] | Matches any single digit from 0 to 9 |
| [a-z] | Matches any lowercase letter from a to z |
| [A-Z] | Matches any uppercase letter from A to Z |
| [a-zA-Z] | Matches any letter, either lowercase or uppercase |
| . | Matches any single character except for a newline |
| ^ | Matches the start of a string |
| $ | Matches the end of a string |
| * | Matches zero or more of the preceding character or group |
| + | Matches one or more of the preceding character or group |
| ?Not | Makes the ehh preceding character or group optional (matches zero or one times) |
| \d | Matches any digit |
| \w | Matches any word character (letters, digits, or underscores) |
| \s | Matches any whitespace character (spaces, tabs, or newlines) |
| () | Creates a capturing group for extracting a portion of a match |

| Regular Expression | Use |
| --- | --- |
| \d | Matches any digit (0-9) |
| \w | Matches any word character (letters, digits, or underscores) |
| . | Matches any character except for a newline |
| ^ | Matches the beginning of a line |
| $ | Matches the end of a line |
| + | Matches one or more occurrences of the preceding character or group |
| * | Matches zero or more occurrences of the preceding character or group |
| ? | Matches zero or one occurrence of the preceding character or group |
| [ ] | Matches any single character in the specified set |
| [^ ] | Matches any single character not in the specified set |
| ( ) | Creates a capturing group for extracting a substring from the matched text |