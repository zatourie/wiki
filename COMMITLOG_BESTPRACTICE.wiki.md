Always write a comment when committing something to the repository. Your comment should be brief and to the point, describing what was changed and possibly why. If you made several changes, write one line or sentence about each part. If you find yourself writing a very long list of changes, consider splitting your commit into smaller parts, as described earlier. Prefixing your comments with identifiers like Fix or Add is a good way of indicating what type of change you did. It also makes it easier to filter the content later, either visually, by a human reader, or automatically, by a program.

If you fixed a specific bug or implemented a specific change request, I also recommend to reference the bug or issue number in the commit message. Some tools may process this information and generate a link to the corresponding page in a bug tracking system or automatically update the issue based on the commit.

Here are some examples of good commit messages:

Changed paragraph separation from indentation to vertical space.
```
    ...
    Fix: Extra image removed.
    Fix: CSS patched to give better results when embedded in javadoc.
    Add: A javadoc {@link} tag in the lyx, just to show it's possible.
    ...
    - Moved third party projects to ext folder.
    - Added lib folder for binary library files.
    ...
    Fix: Fixed bug #1938.
    Add: Implemented change request #39381.
```
In my experience, you have to follow up on people and give them directions whenever they don't follow the commit rules. You could of course implement a script to enforce some of the rules (like the prefixing and bug referencing), but that will not catch the lazy people who don't bother to write anything meaningful. I think it's important to explain why you want these conventions and how they will benefit the development team.

Setting up a commit e-mail list and monitor it for message is a good way to keep track of what people are doing. Whenever someone is committing something without a satisfactory message, you will know so and can tell them. I guess is the same way as with coding conventions, for them to be successful, somebody has to follow up on them.

from [stackoverflow](http://stackoverflow.com/questions/43598/suggestions-for-a-good-commit-message-format-guideline)