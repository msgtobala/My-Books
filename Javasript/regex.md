**FLAGS**

 

**/g - global flag -** searches all the string

**/i - insensitive flag -** searches the string with case insensitively

 

**SYNTAX**

 

**[ng]inja -** searches the string either starting with n or g and ends(either g or n in the 1st position).

**[^p]000 -** matches all the characters at the first position except p

**[^pe]000 -** matches all the characters at the first position except p and e

**[a-z]000 -** matches all the characters in the alphabets(this uses range)

**[^a-z]000 -** matches all the characters in the except alphabets(this uses range)

**[a-zA-Z]000 -** matches all the lower case and upper case alphabets

**[^0-9]000 -** matches all the values between 0 - 9

**[0-9]{11} -** matches number ranges for 11 times long or greater

**[a-z]{5} -** matches all characters with length of 5 or greater

**[a-z]{5, 8} -** matches all characters with length range of 5 to 8

**[a-z]{5, } -** matches all characters with at-least the length of 5 and greater 

**META-CHARACTERS**

**\d -** matches any digits ( [0-9] )

**\w -** matches word characters like a-z, A-Z, 0-9, underscores(_s)

**\s -** matches white space character

**\t -** matches tab character

**SPECIAL CHARACTERS**

**+, \ , [ ], [^]**

**+ -** One or more qualifier

**\ -** escape character

**[ ] -** Character set

**[^ ] -** negate character

**? -** zero or one quantifier...like optional

**. -** Period

*** -** 0 or more quantifier( but + is at least or more)

**| -** matches or characters mentioned

hello? - matches the character with hell or hello also o is optional

[a-z]?000 - first alphabet is optional but it must have 000

car. - **.** can be any character except new line

.+ - matches all the characters with atleast character of length one

a[a-z]* - a should be there but the next character(s) can be of length 0 or more

(p|t)yre - matches pyre or tyre

**START AND END PATTERNS**

**^ -** start character 

**$ -** end character

 

**^[a-z]{5}$ -** the string should have length of only 5 between start and end

**[a-z]{5}$ -** the string should have match at the end of 5 characters

**^[a-z]{5} -** the string should have match at the start with length of 5

**(pet|crazy|street) dog -** matches all strings like pet dog, crazy dog, street dog

**(pet|crazy|street)? dog -** matches _dog or [any_string] dog pet, crazy, street is optional

 

 

 

 

 

PASSWORD REGEX

| Regex              | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| ^                  | The password string will start this way                      |
| (?=.*[a-z])        | The string must contain at least 1 lowercase alphabetical character |
| (?=.*[A-Z])        | The string must contain at least 1 uppercase alphabetical character |
| (?=.*[0-9])        | The string must contain at least 1 numeric character         |
| (?=.*[!@#\$%\^&*]) | The string must contain at least one special character, but we are escaping reserved RegEx characters to avoid conflict |
| (?=.{8,})          | The string must be eight characters or longer                |

var strongRegex = new RegExp("^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[!@#\$%\^&\*])(?=.{8,})"); 

var mediumRegex = new RegExp("^(((?=.*[a-z])(?=.*[A-Z]))|((?=.*[a-z])(?=.*[0-9]))|((?=.*[A-Z])(?=.*[0-9])))(?=.{6,})");

email = /^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/

password regex

https://www.w3resource.com/javascript/form/password-validation.php

 

 [http://regexlib.com/Search.aspx?k=password   ](http://regexlib.com/Search.aspx?k=password)

 

 

 