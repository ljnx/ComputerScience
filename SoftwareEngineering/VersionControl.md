[Pro git](https://git-scm.com/book/en/v2)

2022-04-13
[学到这儿: Git on the Server](https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols)

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
	read	
		download objects and refs from another repo		`git fetch <repo>`
	update	
		change remote repo name					`git remote rename`
		update remote refs along with associated objects	`git push <remote> <branch>`
		join two or more development histories together		`git merge <remote branch>
		clone a remote branch					`git checkout -b <new-branch> <start-point>`
		git fetch + git merge(not recommended)
			`git pull`


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

		replays changes from one line of work onto another in the order they were introduced
			Expression
				rebase A onto B
					B <- A
			Illustration
				before
					       	  ->C5->C6       (experiment)	
					C1->C2->C3->C4 	         (master)

				after
					C1->C2->C3->C4->C5'->C6' (master)

			Code
				```
				$git checkout experiment
				$git rebase master

				First, rewinding head to replay your work on top of it...
				Applying: added staged command

				$git checkout master
				$git merge experiment
				```

		replays changes from something other than the rebase targe branch
			Illustration
				before
					C1<-C2<-C5<-C6      (master)
					      <-C3<-C4<-C10 (server)
					          <-C8<-C9  (client)
				after
					C1<-C2<-C5<-C5<-C8'<-C9' (master/client)
					      <-C3<-C4<-C10	 (server)
			Code
				```
				$ git rebase --onto master server client
				$ git checkout master
				$ git merge client
				```

	Read
		show all branches	`git branch --all`
	Delete
		delete a local branch	`git branch -d`
		delete a remote branch	`git push origin --delete branch`

Tracking Branches
When
	* checking out a local branch from a remote-tracking branch automatically creates a tracking branch
	* cloning a repo autimatically creates a `master` branch that tracks origin/master
	
What
	local branches that have a direct relationship to a remote branch
Why
How
	Create
		a tracking Branch 
			```
			git checkout --track origin/serverfix
			Branch serverfix set up to track remote branch serverfix from origin.
			Switched to a new branch `serverfix`
			```
		if the branch name you're trying to checkout (a) doesn't exist and (b) exactly matches a name on only one remote
		Git will create a tracking branch for you
			```
			git checkout serverfix
			Branch serverfix set up to track remote branch serverfix from origin.
			Switched to a new branch 'serverfix'
			```
		set up a local branch with a different name than the remote branch
			```
			git checkout -b sf origin/serverfix
			Branch sf set up to track remote branch serverfix from origin.
			Switched to a new branch 'sf'
			```
	Update
		change the upstream branch you're tracking
			```
			git branch -u origin/serverfix
			Branch serverfix set up to track remote branch serverfix from origin
			```

			```
			git branch --set-upstream origin/serverfix
			```
	Read
		see what tracking branches you have set up
			```
			git branch -vv
			iss53	7e424c3	[origin/iss53: ahead 2] Add forgotten brackets
			```

# 4.1 Git on the Server
How
	1. choose your server's protocols
	2. set up protocols 
	3. chose a host
				
	
