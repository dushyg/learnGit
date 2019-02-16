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

