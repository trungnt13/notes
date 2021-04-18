# Github Markdown Cheatsheets

There are two ways to create links.

    [I'm an inline-style link](https://www.google.com)

    [I'm an inline-style link with title](https://www.google.com "Google's Homepage")

    [I'm a reference-style link][Arbitrary case-insensitive reference text]

    [I'm a relative reference to a repository file](../blob/master/LICENSE)

    [You can use numbers for reference-style link definitions][1]

    Or leave it empty and use the [link text itself].

    URLs and URLs in angle brackets will automatically get turned into links.
    http://www.example.com or <http://www.example.com> and sometimes
    example.com (but not on Github, for example).

    Some text to show that the reference links can follow later.

    [arbitrary case-insensitive reference text]: https://www.mozilla.org
    [1]: http://slashdot.org
    [link text itself]: http://www.reddit.com


[I'm an inline-style link](https://www.google.com/)

[I'm an inline-style link with title](https://www.google.com/)

[I'm a reference-style link](https://www.mozilla.org/)

[I'm a relative reference to a repository file](https://github.com/adam-p/markdown-here/blob/master/LICENSE)

[You can use numbers for reference-style link definitions](http://slashdot.org/)

Or leave it empty and use the [link text itself](http://www.reddit.com/).

URLs and URLs in angle brackets will automatically get turned into links. [http://www.example.com](http://www.example.com/) or [http://www.example.com](http://www.example.com/) and sometimes example.com (but not on Github, for example).

Some text to show that the reference links can follow later.

Images
--------

    Here's our logo (hover to see the title text):

    Inline-style:
    ![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

    Reference-style:
    ![alt text][logo]

    [logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"


Here's our logo (hover to see the title text):

Inline-style: ![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png)

Reference-style: ![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png)


Code and Syntax Highlighting
------------------------------

Code blocks are part of the Markdown spec, but syntax highlighting isn't. However, many renderers -- like Github's and _Markdown Here_ -- support syntax highlighting. Which languages are supported and how those language names should be written will vary from renderer to renderer. _Markdown Here_ supports highlighting for dozens of languages (and not-really-languages, like diffs and HTTP headers); to see the complete list, and how to write the language names, see the [highlight.js demo page](http://softwaremaniacs.org/media/soft/highlight/test.html).

    Inline `code` has `back-ticks around` it.


Inline `code` has `back-ticks around` it.

Blocks of code are either fenced by lines with three back-ticks ` ``` `, or are indented with four spaces. I recommend only using the fenced code blocks -- they're easier and only they support syntax highlighting.

    ```javascript
    var s = "JavaScript syntax highlighting";
    alert(s);
    ```

    ```python
    s = "Python syntax highlighting"
    print s
    ```

    ```
    No language indicated, so no syntax highlighting.
    But let's throw in a <b>tag</b>.
    ```


var s \= "JavaScript syntax highlighting";
alert(s);

s \= "Python syntax highlighting"
print s

    No language indicated, so no syntax highlighting in Markdown Here (varies on Github).
    But let's throw in a <b>tag</b>.


[](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#tables)Tables
---------------------------------------------------------------------------------

Tables aren't part of the core Markdown spec, but they are part of GFM and _Markdown Here_ supports them. They are an easy way of adding tables to your email -- a task that would otherwise require copy-pasting from another application.

    Colons can be used to align columns.

    | Tables        | Are           | Cool  |
    | ------------- |:-------------:| -----:|
    | col 3 is      | right-aligned | $1600 |
    | col 2 is      | centered      |   $12 |
    | zebra stripes | are neat      |    $1 |

    There must be at least 3 dashes separating each header cell.
    The outer pipes (|) are optional, and you don't need to make the
    raw Markdown line up prettily. You can also use inline Markdown.

    Markdown | Less | Pretty
    --- | --- | ---
    *Still* | `renders` | **nicely**
    1 | 2 | 3

Math
------

  - 'dollars' (default)
    - inline: $...$
    - display: $$...$$
    - display + equation number: $$...$$ (1)
  - 'brackets'
    - inline: \(...\)
    - display: \[...\]
    - display + equation number: \[...\] (1)
  -'gitlab'
    - inline: $`...`$
    - display: ```math ... ```
    - display + equation number: ```math ... ``` (1)
  - 'julia'
    - inline: $...$ or ``...``
    - display: ```math ... ```
    - display + equation number: ```math ... ``` (1)
  - 'kramdown'
    - inline: $$...$$
    - display: $$...$$
    - display + equation number: $$...$$ (1)
