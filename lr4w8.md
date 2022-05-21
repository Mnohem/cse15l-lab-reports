[My repository](https://github.com/Mnohem/markdown-parser)<br>
[The repository we reviewed](https://github.com/AllKeng/markdown-parser)
## First Snippet
- This test should output `[google.com]`
```
@Test
public void snippet1Test() throws IOException {
	MarkdownParse mdp = new MarkdownParse();
	Path fileName = Path.of("snippet1.md");
	String content = Files.readString(fileName);
	ArrayList links = mdp.getLinks(content);
	assertEquals(List.of("google.com"), links);
}
```
- My implementation fails: ![fail](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/my-snippet1-error.png)
- The reviewed implementation fails: ![fail](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/rev-snippet1-error.png)


## Second Snippet
- This test should output `[b.com, a.com(()), example.com]`
```
@Test
public void snippet2Test() throws IOException {
	MarkdownParse mdp = new MarkdownParse();
	Path fileName = Path.of("snippet2.md");
	String content = Files.readString(fileName);
	ArrayList links = mdp.getLinks(content);
	assertEquals(List.of("b.com", "a.com(())", "example.com"), links);
}
```
- My implementation fails: ![fail](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/my-snippet2-error.png)
- The reviewed implementation fails: ![fail](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/rev-snippet2-error.png)


## Third Snippet
- This test should output `[https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]`
```
@Test
public void snippet3Test() throws IOException {
	MarkdownParse mdp = new MarkdownParse();
	Path fileName = Path.of("snippet3.md");
	String content = Files.readString(fileName);
	ArrayList links = mdp.getLinks(content);
	assertEquals(List.of("https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule"), links);
}
```
- My implementation fails: ![fail](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/my-snippet3-error.png)
- The reviewed implementation fails: ![fail](https://raw.githubusercontent.com/Mnohem/cse15l-lab-reports/main/images/rev-snippet3-error.png)

# Questions
- I don't think there is a simple change to correct the behavior with inline code using backticks. This is because there would have to be a lot of corrections in order to account for the formatting conflicts that would occur.
- I don't think there is a simple change to correct the behavior with nested parentheses and brackets. This is because there would have to be a different algorithm to find the closing parentheses or bracket for the corresponding opening parentheses or bracket, since the current implementation does not account for nesting at all.
- An easy fix to account for newlines between the brackets and parentheses would be to check if any characters between the closing and opening bracket/parentheses are newlines, and to not consider that a link if it finds any newlines.
