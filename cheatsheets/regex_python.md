### Elements that define a regular expression
# \A	  restricts the match to the start of string
# \Z	  restricts the match to the end of string
# ^	    restricts the match to the start of line
# $	    restricts the match to the end of line
# \n	  newline character is used as line separator
# \b	  restricts the match to the start/end of words,
#       word characters: alphabets, digits, underscore
# \B	  matches wherever \b doesn’t match
# re.MULTILINE or re.M	flag to treat input as multiline string
### Characters
# [aeiou]	  Match any vowel
# [^aeiou]	^inverts selection, so this matches any consonant
# [a-f]	    -defines a range, so this matches any of abcdef characters
# \d	      Match a digit, same as [0-9]
# \D	      Match non-digit, same as [^0-9] or [^\d]
# \w	      Match word character, same as [a-zA-Z0-9_]
# \W	      Match non-word character, same as [^a-zA-Z0-9_] or [^\w]
# \s	      Match whitespace character, same as [\ \t\n\r\f\v]
# \S	      Match non-whitespace character, same as [^\ \t\n\r\f\v] or [^\s]
### Groups
# |	    multiple RE combined as conditional OR each alternative can have independent anchors
# (RE)	group pattern(s), also a capturing group
# a(b|c)d   is same as abd|acd
# (?:RE)	  non-capturing group
# (?P<name>pat)	  named capture group
# .	      Match any character except the newline character \n
# []	    Character class, matches one character among many
# *	      Match zero or more times
# +	      Match one or more times
# ?	      Match zero or one times
# {m,n}	  Match m to n times (inclusive)
# {m,}	  Match at least m times
# {,n}	  Match up to n times (including 0 times)
# {n}	    Match exactly n times
# pat1.*pat2	            any number of characters between pat1 and pat2
# pat1.*pat2|pat2.*pat1	  match both pat1 and pat2 in any order
# (?!pat)	  negative lookahead assertion
# (?<!pat)	negative lookbehind assertion
# (?=pat)	  positive lookahead assertion
# (?<=pat)	positive lookbehind assertion
# (?!pat1)(?=pat2)	multiple assertions can be specified in any order as they mark a matching location without consuming characters
# ((?!pat).)*	Negate a grouping, similar to negated character class
### re flags
# re.IGNORECASE     or re.I	flag to ignore case
# re.DOTALL         or re.S	allow . metacharacter to match newline character
# flags=re.S|re.I	  multiple flags can be combined using | operator
# re.MULTILINE or re.M	allow ^ and $ anchors to match line wise
# re.VERBOSE or re.X	allows to use literal whitespaces for aligning purposes and to add comments after the # character escape spaces and # if needed as part of actual RE
# re.ASCII or re.A	match only ASCII characters for \b, \w, \d, \s
#  	and their opposites, applicable only for Unicode patterns
# re.LOCALE or re.L	  use locale settings for byte patterns and 8-bit locales
# (?#comment)	        another way to add comments, not a flag
# (?flags:pat)	      inline flags only for this pat, overrides flags argument
#  	                  flags is i for re.I, s for re.S, etc, except L for re.L
# (?-flags:pat)	negate flags only for this pat
# (?flags-flags:pat)	apply and negate particular flags only for this pat
# (?flags)	apply flags for whole RE, can be used only at start of RE anchors if any, should be specified after (?flags)
### re module functions
# re.search	    Check if given pattern is present anywhere in input string
#  	            Output is a re.Match object, usable in conditional expressions
#  	            r-strings preferred to define RE
#  	            Use byte pattern for byte input
#  	            Python also maintains a small cache of recent RE
# re.fullmatch	ensures pattern matches the entire input string
# re.compile	  Compile a pattern for reuse, outputs re.Pattern object
# re.sub	      search and replace
# re.sub(r'pat', f, s)	function f with re.Match object as argument
# re.escape	    automatically escape all metacharacters
# re.split	    split a string based on RE
#  	            text matched by the groups will be part of the output
#  	            portion matched by pattern outside group won’t be in output
# re.findall	  returns all the matches as a list
#  	            if 1 capture group is used, only its matches are returned
#  	            1+, each element will be tuple of capture groups
#  	            portion matched by pattern outside group won’t be in output
# re.finditer	  iterator with re.Match object for each match
# re.subn	      gives tuple of modified string and number of substitutions
