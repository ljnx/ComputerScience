[Pro git](https://git-scm.com/book/en/v2)

## 2. Git Basics
### 2.2 Recording Changes to the Reposity & 2.3 Git history & 2.4 undo things
What:Staging area
	contains all changes to commit in the next commit.
How
	Create					`git add`
		Start tracking files.		~
		Add changes in staged files.	~
	Update
		rename tracked files		`git mv`
	Read
		check the status of all files			`git status`
			in short form				`-s`
		disaply the contents of unstaged changes	`git diff`
	Delete
		ignore local fiels		`.gitignore`
		delete tracked files		`git rm`
			but keep local copies	`--chached`
		delete a staged file		`git restore`
			unstage a file
			restore unstaged changes

---

What:Commit
	a snapshot of all staged changes
How
	Create	`git commit`
	Update a commit
		amend the previous commit		`git commit --amend`
		add more files to the previous commit	`git commit --amend` 
	Read						`git log`
		show the commit content			`-p`
		show the commit history in oneline	`--neline`
		filter the commit history by date	`--since="2 years"`
		get the last n commit history		`-2`

### 2.5 Working with Remotes
what:Remote
	a remote repo

How
	create	`git remote add`	
	read	`git remote show`
	update	`git remote rename`
	delete	`git remote remove`

### 2.6 Tagging
what:Tag
	a named reference to a commit

how
	Create		`git tag`
	Read		`git tag show`
	Update 
	Delete		`git tag -d`


### 2.7 Git Aliases
What:Alias
	a combination of git commands, like macro in excel
How
	Create	`git congfig --global alias.<name> '<git command>'`

## 3. Git Branching

What:Branch
	a copy of a repo, where you can make commits
How
	Create	
		create a new branch	`git branch`
		switch to a branch	`git checkout`
		create and switch to a new branch	`git checkout -b`
	Update
		rename a branch		`git branch --move`
		rename a remote branch	`git push --set-upstream`
		merge a branch		`git merge`
	Read
		show all branches	`git branch --all`
	Delete
		delete a local branch	`git branch -d`
		delete a remote branch	`git push origin --delete branch`
