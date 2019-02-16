- cloning repository
	git clone <repoUrl>

- initializing / creating new repository into git
	git init

- create and switch to new branch
	git checkout -b <branchName>

- Adding files to staging area
	git add -u (stage edited files already being tracked, doesnt touch untracked files)
	git add . (adds all edited files to index / stages all edited files in current directory - including any changes inside subfolders)

- Unstage files

	git reset (unstage all files and keep the edits, Warning this will reset all of your unpushed commits to master!)
	git reset --hard (discards all edits, doesnt delete newly added files though)
	git reset HEAD README.md (unstage files by file names)
	git reset is specifically about updating the index, moving the HEAD.
 
	Eg. what git reset --hard and then subsequent push does to the commits which were locally reset
	git reflog  (Lets say we had these commits)
	014df6a (HEAD -> master) HEAD@{0}: commit: Local commit #5
	6237772 HEAD@{1}: commit: Local commit #4
	593794d HEAD@{2}: commit: Local commit #3
	b1a6865 HEAD@{3}: commit: Local commit #2
	8a3358e HEAD@{4}: commit: Local commit #1
 
	git reset --hard 593794d	(Now we reset to local commit #3)
	
	head will reset to local commit #3 but commits 4 and 5 still remain in the local history.
	
	But if we push these changes after git reset --hard , only commits till #3 will be shown on the server. local commits 4 & 5 will be lost and not shown in the history.
	
	git reset vs git revert : With git revert reverted commits are retained in the history and a new commit that reverts the older commit is created while with get reset the commits after the commit we reverted to will not be shown in the history on the server.
	
- Checking pending changes
	git status

- Viewing repository (commit) log
	git log

- Undo file changes (before staging or commiting) - i.e. discard local changes
	git checkout Readme.txt
	git checkout . (revert changes made to your working copy)
	git checkout is about updating the working tree (to the index or the specified tree). It will update the HEAD only if you checkout a branch
	git checkout discards any unstaged edited files, but doesnt touch newly added files with content in them.

- list branches
	git branch

- see difference between previous commit and current changes
	git diff

- If you want to remove untracked files (e.g., new files, generated files): 
	git clean -f

- commiting changes
	git commit -m "Message for the commit"

- Revert commits
	git revert <commit1> <commit2>

	git revert commit should be first 6 chars of sha1

	If we revert 3rd commit out of 5 last commits, only the changes associated to the 3rd commit are reverted. Changes with commits 1, 2 , 4, 5 are retained.
	If there are multiple changes to a single file in all the commits, then a merge conflict happens.

- show history of all actions
	git reflog

- Cherry picking commits from same or other branch
When you git cherry pick a commit only the changes associated with that commit are reapplied to the working tree.
eg. If we added 5 diff files each with its own commit and then deleted all files with the 6th commit, then if we cherry pick the 3rd commit, it will bring back file added with that commit. Other files will not be brought back.
eg. If we added 5 diff files each with its own commit and then deleted all files with the 6th commit, then if we cherry pick the 3rd commit, it will bring back file added with that commit. Other files will not be brought back.
When you git-cherry-pick a commit, a completely new commit is created on the branch

Commands to update the server branch
- updating server branch with local commits
	git push origin develop (will sync develop branch on origin with local commits)
	git push origin master (will sync master branch on origin with local commits)

-