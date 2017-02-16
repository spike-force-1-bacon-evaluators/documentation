# Ways of Working

* [Overview](#Overview)
* [Definition of Done](#markdown-header-definition-of-done)
* [Issue tracking](#markdown-header-issue-tracking)
* [Topic branches](#markdown-header-topic-branches)
* [Commit messages](#markdown-header-commit-messages)
* [Code review](#markdown-header-code-review)
* [Release](#markdown-header-release)
* [Gitflow](#markdown-header-gitflow)



## Overview

This project is version tracked with Git and available in the [Spike Force 1 - Bacon Evaluators](https://github.com/spike-force-1-bacon-evaluators) organisation on GitHub.

The main branch is called `master` and contains the most updated and stable version of the code.

Features and bug fixes are implemented in topic branches which stem from the mainline (master branch) and should be merged into `master` as soon as the implementation attends to the [Definition of Done](#Definition-of-done). If the feature/fix takes longer than five days to be concluded, please consult with the team.


## Definition of Done

* code written and validated
* tests written (unit, acceptance)
* documented code (comments, docstrings, ...)
* code reviewed
* issue closed
* topic branch removed


## Issue tracking

Every `feature` and `fix` must have an issue linked to it.
Open an issue for the task to be implemented providing a title and a description.


## Topic branches

Tasks are implemented on topic branches stemming from the master.

Topic branches should implement small tasks and take no more than **one** day to be integrated into the mainline. This avoids long codes to be reviwed, conflicts during integration and promotes a short and dynamic development cycle.

After merging into the mainline, topic branches must be removed locally and remotely in order to keep the development environment clean and sane.


## Commit messages

Commit messages should be written on the following pattern:

* separate subject from body with a blank line
* limit the subject line to 50 characters
* capitalize the subject line
* do not end the subject line with a period
* use the imperative mood in the subject line
* wrap the body at 72 characters
* use the body to explain what and why vs. how

For example:

```
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like log, shortlog
and rebase can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here
```

## Code review

With a task completed (see: [DoD](#markdown-header-definition-of-done)) a `Pull Request` must be open.

Provide the necessary information in the description area to help other team members to understand the changes that your code proposes. Make reference to the issue tracker related to your task.

For convenience, the pull request (PR) title can be the same as the topic branch name (slightly formatted).

### Reviewer guidelines

The main areas to focus during the code review:

* unit tests coverage and quality
* comment and coding conventions
* error handling
* commits are logical and messages are clear
* functionality
* security

Everything in this list has high priority. The reviewer can go be beyond that, but these points are all important and must be covered.

The code is ready to be merged into the mainline when:

1. all proposed changes were answered/applied
2. code was reviewed and approved by at least 50% of the team
3. code was approved by Product Owner and lead member of technical staff related to the task

### Tips for the Reviewer

* critique code instead of people â€“ be kind to the coder, not to the code.
* treat people who know less than you with respect, deference, and patience.
* the only true authority stems from knowledge, not from position.
* please note that Review Meetings are NOT problem solving meetings.
* ask questions to clarify the reasoning behind the code instead of making accusatory statements.
* avoid the **why** questions.
* remember to praise.
* make sure you have good coding standards to reference.
* remember that there is often more than one way to approach a solution.
* you shouldn't rush through a code review - but also, you need to do it promptly.
* keep feedback near the code in question to optimize the review.


## Release

Code is released manualy under the Product Owner's approval using `annotated git tags` and follows the [Semantic Versioning 2.0.0](http://semver.org/spec/v2.0.0.html) specification.

### Tagging versions

```
git tag -a 1.0.0 -m 'the foo release'
git push origin --tags
```


## Gitflow

#### 1. Create topic branch

```
git fetch
git checkout <branch-created-on-github>
```

#### 2. Code < insert your magic here >

#### 3. Push your code

It is strongly recommended to often push your code to the remote repository.

When pushing for the first time, add the flag `-u`. It may help if you don't want to manually specify the remote every time you run git push.

```
git push -u origin <topic-branch>
```

#### 4. Update topic branch with latest changes from the mainline

```
git checkout master
git fetch
git checkout <topic-branch>
git rebase origin/master
git push -f origin <topic-branch>
```

This proccess will:

* update the topic branch with any possible change on master
* force the topic branch push to the origin

#### 5. Open a Pull Request

Before merging a topic branch into the mainline a pull request must be open. See [Principles for Evaluating Pull Requests](docs/pull-request-evaluation.md).

Announce the pull request in the project's channel on Slack and make a *Call for Review*.

#### 6. Merge the topic branch

Announce in the Slack channel that you will merge your work.

**DO NOT** merge your code while another merging proccess is in progress.

Ensure that the topic branch is updated (see step 4)

```
git checkout master
git merge <topic-branch>
git push origin master
```

#### 7. Clean your stuff

* remove the topic branch from your local repository
* remove the topic branch from the remote repository

```
git checkout master
git branch -D <topic-branch>
git push origin :<topic-branch>
```

Tell your colleagues that the merging process is completed.

#### 8. If something goes wrong please don't try to fix it by yourself. **Communicate with the rest of the team**.



### Reference

[How to Write a Git Commit Message](http://chris.beams.io/posts/git-commit/)

[Code Review Guidelines](http://www.codeproject.com/Articles/524235/Codeplusreviewplusguidelines)

[Semantic Versioning 2.0.0](http://semver.org/spec/v2.0.0.html)

[Git tags](https://git-scm.com/book/en/v2/Git-Basics-Tagging)

