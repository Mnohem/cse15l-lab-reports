# First Fix
- ![Diff](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/fix1.png)
- [Failing Test](https://raw.githubusercontent.com/Mnohem/markdown-parser/main/new-test.md)
- **Incorrect Output**: ![Output](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/Pictures/slurped-2022-05-06-17%3A40%3A03.png)
- Due to the similarities between images and links in markdown files, the parser initially confused them. This was fixed by checking for their one difference, that being that images have an exclamation point before the opening bracket.

# Second Fix
- ![Diff](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/fix2.png)
- [Failing Test](https://raw.githubusercontent.com/Mnohem/markdown-parser/main/test3.md)
- **Incorrect Output**: ![Output](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/Pictures/slurped-2022-05-06-17%3A41%3A02.png)
- Initially when parsing, the distance between the closing bracket and the opening parentheses was not considered, even though they should be right next to each other for a link. This bug caused links to appear if there was the correct ordering of brackets and parentheses, and was fixed by simply checking if the closing bracket came directly before the opening parentheses.


# Third Fix
- ![Diff](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/fix3.png)
- [Failing Test](https://raw.githubusercontent.com/Mnohem/markdown-parser/main/test4.md)
- **Incorrect Output**: ![Output](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/Pictures/slurped-2022-05-06-17%3A42%3A59.png)
- Due to my first fix, I check for an exclamation mark before the opening bracket. If the opening bracket is in the zeroth index, then we try to index at -1, which leads to the exception. To fix this, we simply don't check for the exclamation point if the opening bracket is at index 0. 
