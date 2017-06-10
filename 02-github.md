# GitHub

## Org Questions

* passing the course is based on a small project everybody has to complete
* for that project you need all programs/services set up and running
* exercises are not mandatory

## Content:

* Learning how to develop software is learning how to learn
	* hours per exercise: `(2 + 1) * [1,5 .. 2] * [2 .. 3] - 2 ~ [7 .. 16]`
	* learn how to branch and merge, you'll need to know!
* How to share code?

### How can Git share code?

* so far we've only used Git locally
* a "remote" is like a local repository but on a different machine
* most projects have a natural remote repository, to which they belong - it is usually called "origin"
* changes can be "pulled from" or "pushed to" a remote

### How does GitHub work?

[GitHub](https://github.com) is a free project management service that revolves around Git.
A GitHub project has:

* a Git repository that can be used as a remote
* an "issue tracker", where tasks are being managed
* a view on "pull requests" where developers offer changes to the project

Usually only very few people working on a project have direct access to the repository, so the following developed as the default workflow:

* create a "fork", a copy of the project on which you can work
* clone the fork and use the fork as a remote; your fork is usually called "origin", the original project is usually added as "upstream"
* to do a task:
	* create a new branch from master to work on (locally, with regular pushes to the fork)
	* once a feature is done (or just to get feedback), offer the changes to the original project in a "pull request"
	* the project maintainers look at the changes and accept them (or not)

![](original-fork-local.png)

## Homework

Learning how to use Git and GitHub collaboratively is a little of a chicken-and-egg problem and you kind of have to learn both at the same time.
I try to sequentialize this but it's not perfect - if you don't understand something, make a note and see whether it was cleared up later.

### GitHub

During some videos and tutorials you will see that GitHub brings many of Git's command-line features that we used and are going to use to the browser (you will particularly recognize committing, branching, and merging) but we won't be using that beyond the tutorials.
Start by watching these videos:

* [Intro to GitHub • GitHub & Git Foundations](https://www.youtube.com/watch?v=vDv5K5PbvO8)
* [GitHub - Part 1 "Getting Started"](https://www.youtube.com/watch?v=rGfzy21yVRU) (until 3:54)

Then, go to http://github.com and create an account (it is free! if you enter credit card info or log into PayPal, you're doing it wrong) and work through the following tutorials:

* [Hello World](https://guides.github.com/activities/hello-world/)
* [Creating a new repository](https://help.github.com/articles/creating-a-new-repository/)
* [Cloning a repository](https://help.github.com/articles/cloning-a-repository/)
* [Which remote URL should I use?](https://help.github.com/articles/which-remote-url-should-i-use/) (SSH vs HTTPS)

### Git

Now it's time to learn more about remote repositories and how to use them.
Continue watching these videos (no need to follow along yet, you'll do that later):

* [Learn to Git: Basic Concepts](https://www.youtube.com/watch?v=8KCQe9Pm1kg)
* [Git Tutorial for Beginners: Command-Line Fundamentals](https://www.youtube.com/watch?v=HVsySz-h9r4&t=14m55s) (from 14:55)
* [Git & GitHub Crash Course For Beginners](https://www.youtube.com/watch?v=SWYqp7iY_Tc&t=21m48s) (from 21:48 on)
* if you want to learn a little on Git's internals: [Git Tutorial for Beginners 4 Git Concepts and Architecture](https://www.youtube.com/watch?v=ihKRRWBVn5k&t=7m15s) (from 7:15 on)

(If you're interested in reverting changes, [ProGit section 2.4](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things) has you covered.)

* [trygit.io](https://try.github.io) (you did some parts already, focus on 1.10 and following; online only)
* [Pro Git](https://git-scm.com/book/en/v2) (Sections 2.5, 3.3 to 3.7; on either a new or last week's repository)

### GitHub

We're back to theory - watch these videos:

* [Forking • GitHub & Git Foundations](https://www.youtube.com/watch?v=5oJHRbqEofs)
* [Pull Requests • GitHub & Git Foundations](https://www.youtube.com/watch?v=d5wpJ5VimSU)
* [GitHut - Pull request tutorial](https://www.youtube.com/watch?v=NnBb9NTk-To)

Then, do the following tutorials either with the existing or a new local repository:

* [Fork A Repo](https://help.github.com/articles/fork-a-repo/)
* [Hubspot](http://product.hubspot.com/blog/git-and-github-tutorial-for-beginners) (you did some parts already, focus on #6 and following)

Now you should now all about how to create or fork a repository, clone it locally, create a branch, push it, and open a pull request.

Finally, to properly express yourselfon GitHub, have a look at [GitHub's Markdown flavor](https://guides.github.com/features/mastering-markdown/).

### Hand In

To complete this part of the course:

* setup
	* go to https://github.com/nicolaiparlog/energy-model, fork the project, and clone the fork (!) locally
	* import the project into IntelliJ IDEA, take a look around, and run it
* code
	* on GitHub, pick at least two of the issues you want to work on
	* read the linked documents and ask questions on the issues if you're not sure what exactly you need to do
	* create a new branch `homework-NO` for each issue (where `NO` is the issue number), solve the task, and commit the changes (in one or more commits)
* sharing
	* push the branch to your fork, go back to GitHub and open a pull request for each from your branch in your fork to the master branch in the original project
	* send a mail to [nipa@codefx.org](mailto:nipa@codefx.org) with a link to the pull request

Deadline for the pull request is **May 1st**.

## Further Sources:

* [Vogella](http://www.vogella.com/tutorials/Git/article.html)
* [Pro Git](https://git-scm.com/book/en/v2)
* [GitHub Help](https://help.github.com/)
* [GitHub Guides](https://guides.github.com/)
