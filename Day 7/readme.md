# RegEx Notes (JS Flavour)
------------------------------
Uses
1. Used in Email Validation
2. Password pattern matching


literal characters -> character is taken literally.
meta characters -> specifies a more generalized , ground of characters

### Single Char
-----------------------
\d -> digit 0 to 9
\w -> Any character A-Z, a-z , 0-9
\s -> whitespace
. -> any character whatsoever

\D -> not a \d
\W -> not a \w
\s -> not a whitespace

### Quantifiers (meta chars that modify the single char)
-----------------------------------
* -> 0 or more 
+ -> 1 or more
? -> optional ( 0 or 1)
{n} -> n no. of characters

### Position
------------------------
^ -> beginning of line
$ -> end of line
\b -> word boundary

Side Note: \. means literal dot(.)

### Character Classes (OR like operation)
-------------------------------------
[abc ] -> means a or b or c or space

dash(-) and carrot(^) are special characters inside character classes if they are not the first character in it.
Ex -> [a-z] => a or b or c ..... or z
Ex -> [^0-5] => anything other that 0 to 5.

### Alteration (OR like operation but for words)
-------------------------------
(net | com) -> matches "net" or "com"