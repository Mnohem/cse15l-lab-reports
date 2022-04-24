# First Fix
- ![Diff]()
- [Failing Test](https://raw.githubusercontent.com/Mnohem/markdown-parser/main/new-test.md)
- **Incorrect Output**: [https://something.com, some-thing.html, yeah.html, something.png]
- Due to the similarities between images and links in markdown files, the parser initially confused them. This was fixed by checking for their one difference, that being that images have an exclamation point before the opening bracket.

# Second Fix
- ![Diff]()
- [Failing Test](https://raw.githubusercontent.com/Mnohem/markdown-parser/main/test3.md)
- **Incorrect Output**: [Parentheses, https://something.com, some-thing.html]
- Initially when parsing, the distance between the closing bracket and the opening parentheses was not considered, even though they should be right next to each other for a link. This bug caused links to appear if there was the correct ordering of brackets and parentheses, and was fixed by simply checking if the closing bracket came directly before the opening parentheses.


# Third Fix
- ![Diff]()
- [Failing Test](https://raw.githubusercontent.com/Mnohem/markdown-parser/main/test4.md)
- **Incorrect Output**: IndexOutofBoundsException
- Due to my first fix, I check for an exclamation mark before the opening bracket. If the opening bracket is in the zeroth index, then we try to index at -1, which leads to the exception. To fix this, we simply don't check for the exclamation point if the opening bracket is at index 0. 