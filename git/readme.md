# GIT Version Control

Assume that everything committed will be open sourced in the future. Pretend the whole world is watching. Do not commit sensitive information such as passwords or config files. Include a config.sample file with dummy information instead.


## Work Flow

- Anything in the `Master` branch is always deployable!
- To work on something new, create a descriptively named branch off of master (ie: new-about-content).
- Commit to that branch locally and regularly push your work to the same named branch on the server.
- When you need feedback or help, or you think the branch is ready for merging, open a pull request.
- After someone else has reviewed and signed off on the feature, you can merge it into master.
- Once it is merged and pushed to ‘master’, you can and should deploy immediately.


## Commit Messages

Taken from [Tim Pope's guidlines](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html):

```
Capitalised, short (50 characters or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, preceded by a
  single space, with blank lines in between, but conventions vary here

- Use a hanging indent
```

## Branching/merging conventions

## Git Push

Never call `git push -f` without additional arguments