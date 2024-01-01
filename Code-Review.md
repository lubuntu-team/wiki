# Workflow

After uploading your commit, the reviewers will have a look at your commit. If there are some problems in your change, the reviewers will request you to fix them. If all problems are fixed, the commit will be uploaded to the archive.

Code review is a quality assurance activity. The main goal is to improve code quality and avoid introducing errors and flaws. The author of a commit is often very focused and does not see problems. An author should never take it personally, if a reviewer requests some changes. A request for change is always pointing to a problem in the code and is not related to the author.

It is possible, that a reviewer requests some changes, but the author has good reasons for doing it that way. Code review helps in understand the code and find the best solution together.

# Abbreviations

| Abbreviation | Meaning |
| ------------ | ------- |
| -2           | This shall not be merged: Fix the issues and wait until the reviewer, which gave -2, removes the -2 |
| -1           | I would prefer this is not merged as is: Fix the minor issues |
| +1           | Looks good to me, but someone else must approve |
| +2           | Looks good to me, approved |
| LGTM         | Same as +1 |

# Why code review?

  * Better code quality: Better naming of variables; also other people understand your code
  * Knowledge transfer: You can and will learn from others and improve your own coding skills
  * Finding better solutions: Maybe there are better/simpler solutions for a problem
  * Finding defects: performance problems, security vulnerabilities, external aspects, ...
