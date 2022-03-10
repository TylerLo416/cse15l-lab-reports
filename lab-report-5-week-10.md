## Lab Report 5 Week 10 ##
-------------------------

# Searching for 2 tests with different results #

I manually searched through test files until I found 2 test files that had different answers than the week 9 implementation. To do this, I printed out all the tests on the week 9 implementation, and then with my own markdown parse ```getLinks()``` method. I used the same provided Map ```getLinks``` method to print out the test results for both repositories. I then checked for discrepencies between the outputs and found 2 tests that had different outputs from the week 9 repository and my groups repository.

Code I used to print out the tests for both my repository and the given repository
![Screenshot-0](main-method-test-output.PNG)

Week 9 repository:
![Screenshot-1](my-test-output.PNG)

My groups repository: 
![Screenshot-2](my-actual-test-output.PNG)

# Bug 1: test 489 #

Week 9 repository test 489: 
![Screenshot-3](489-my-output.PNG)

My groups repository:
![Screenshot-4](489-week-9-output.PNG)

Contents of test ```489.md```:

![Screenshot-3.5](489-test.PNG)

Commonmark preview of the contents of test 489:

![Screenshot-3.6](commonmark-489.PNG)

As shown in the commonmark preview, there is no link. Therefore, my groups repository was incorrect, because it returned a link. 

![Screenshot-3.7](489-error.PNG)

The error in my groups repository was that the ```closeParen``` automatically jumps to the index of the next closed parenthesis. However, if there is a line break in between the open and close parenthesis, the link will not work properly. Therefore, there should be an if statement that checks for line breaks in between open paren and close paren, and if there is a line break, it skips past closed paren and onto the next link without adding anything to the arrayList.

# Bug 2: test 505 #

Week 9 repository test 505:
![Screenshot-5](505-their-output.PNG)

My groups repository:
![Screenshot-6](505-my-output.PNG)

Contents of test ```505.md```:

![Screenshot-3.6](505-test.PNG)

Commonmark preview of the contents of test 505:

![Screenshot-3.9](commonmark-505.PNG)

As shown in the commonmark preview, ```505.md``` should produce a link. This means that the week 9 output is incorrect because it does not return a link, but my group's repository has the correct output. 

![Screenshot-7](505-error)

The error in the week 9 repository is that the link is disregarded if there is a space in it, when in reality it is acceptable to have a space if the next character after the space is a quotation mark. Because of this, there needs to be an additional if statement that checks if the character after a space is a quotation mark, which in that case will make the link continue to function regardless of the space (the space is actually required when there is a quotation mark in the link).