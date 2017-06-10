# Git

## Content:

* Learning how to develop software is learning how to learn
* Git, GitHub, Gradle/Travis, JUnit
* What is version control?

* How does Git work?
	* works in any regular folder
	* `.git` folder contains all Git-related information; `git` commands look into it (i.e. no magic!)
	* Git distinguishes:
		* files you have in your directory ("worktree")
		* changes you consider making permanent ("staging area")
		* files you committed to Git ("repository")
		* other repositories (likely online) that contain files ("remote")
	* Git allows to:
		* stage changes to the worktree with `git add`
		* commit staged changes to the repository with `git commit`
		* push committed changes to another repository with `git push`
* [trygit.io](https://try.github.io)


## Homework:

General tip: get a good editor like [Sublime](http://sublimetext.com/), [Notepad++](https://notepad-plus-plus.org/), or [Atom](http://atom.io/).

Watch these videos (maybe set speed to x1.25 or x1.5; no need to follow along yet, we'll do that later):

* [Git Tutorial for Beginners: Command-Line Fundamentals](https://www.youtube.com/watch?v=HVsySz-h9r4) (until 15:00)
* [Git Tutorial for Beginners 4 Git Concepts and Architecture](https://www.youtube.com/watch?v=ihKRRWBVn5k) (until 7:15)
* [Learn Git in 20 Minutes](https://www.youtube.com/watch?v=Y9XZQO1n_7c&t=1m30s) (until 11:15; the dude is weird but his explanations are good)

Work through _on your own machine_ (so you have Git set up correctly afterwards):

* [Pro Git](https://git-scm.com/book/en/v2) (Chapter 1; make sure to set up [your editor in 1.6](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup#_your_editor)!)
* [trygit.io](https://try.github.io) (1.1 - 1.9; online only)
* [Hubspot](http://product.hubspot.com/blog/git-and-github-tutorial-for-beginners) (#1-#5)
* [Pro Git](https://git-scm.com/book/en/v2) (Sections 2.1 to 2.3)
* [Pro Git](https://git-scm.com/book/en/v2) (Sections 3.1 and 3.2 up to and including "Basic Merging")

To complete this part of the course, create a repository with:

* a handful commits on master
* two branches with a few commits each
* one branch should have been merged back into master

Hand in the result of `git log --graph --pretty=tformat:'%Cred%h%Creset (%Cgreen%cd%Creset, %C(bold blue)%an%Creset, %ce): %s%C(yellow)%d%Creset' --date=format:'%d.%m. %H:%M' --abbrev-commit`.

## Further Sources:

* [Vogella](http://www.vogella.com/tutorials/Git/article.html)
* [Pro Git](https://git-scm.com/book/en/v2)
