[Pro git](https://git-scm.com/book/en/v2)

## 2. Git Basics
### 2.2 Recording Changes to the Reposity
__git add__
* start tracking a new file
* stage a modified tracked file

__git status__
* in short format: `-s` or `--short`

__git commit__
* create a snapshot of the current staging area
* __[ok]__  skip staging and commmit all modified tracked files `-a`
* __[no]__  skip staging and commit untrackfiles

__git restore__
* __[ok]__ restore staging area 
* __[ok]__ restore modified tracked file 
  * unstage changes first:`git restore --staged`
  * then:`git restore`
* __[no]__ restore untracked files

__git diff__
* __[ok]__ show the differences of unstaged changes of tracked files
* __[no]__ show the differences of changes of untracked files
* __[ok]__ show the differences of changes of staged changes of tracked files `--staged`

__git rm__
* __[ok]__ delete staged files, this automatically stages the delete action 
* __[no]__ delete untracked files
* delete staged files and keep local files `--cached`
__git mv__
* __[ok]__ rename tracked files
* __[no]__ rename untraked files

`.gitignore`
* ignore local files
* create a `.gitignore` stage and commit the file.

### 2.3 Viewing the Commit History
__git log__
* show the commit history(hashId, author, commit message)
* show the commit content `-p` or `-patch`
* show the commit history in oneline `--pretty=oneline`
* filter the commit history based on time `--since="2 years"`
* limit the lines of log history. `-2`

### 2.4 Undoing Things
__git commit --amend--__

workflow1: change the lasted commit message but dont't create a new commit 
* after make a commit, run this command
* edit commit message

workflow2: you make a commit, but later find that you forget to add some files
* after making a commit
* add more file
* run this command


__git restore__

workflow1: you accidently modifiy a tracked file
* `git restore <file name>`

workflow2: you want to unstage a change
* `git restore --staged <file name>`

### 2.5 Working with Remotes

__Create__ 
`git remote add <name> <url>`

__Read__
 `git remote show <remote>`

__Update__ 
`git remote rename <old name> <new name>`

__Delete__
`git remove <remote>`


### 2.6 Tagging
__what__
* a named reference to a commit

__how__
* __Create__ a tag -> `git tag <name> [<hashId>]`
* __Read__ a tag -> `git tag`
* __Update__ 
* __Delete__ a tag -> `git tag -d`



