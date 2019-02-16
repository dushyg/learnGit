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

- Revert commits
git revert <commit1> <commit2>
