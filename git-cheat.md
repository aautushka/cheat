
git status -s

# remove file from stage: 
git rm --cached <filename>
git rm --staged <filename>

# diff staged files
git diff --staged
git diff --cached

# diff unstaged files
git diff

# show commit diff
git diff-tree -p COMMIT
git diff-tree -p HEAD
git diff-tree -p HEAD~1

# unstage file
git reset <filename>
git reset HEAD <filename>

# show user configuration
git config --list

# show specific configuration parameter
git config <parameter>

# show commit history starting from beginning
git log --reverse

# show the difference introduced in two last commits
git log -p -2

# amend the last commit (e.g. when forgot a file)
git commit -amend

# revert local changes in file
git checkout -- <filename>

# see remote servers
git remote
git remote -v

# add new remote repository
git remote add bitbucket https://bitbucket.org/example/example.git 

# download (do not merge) all changes from remote repository
# the repo would become accessible as bitbucket/master
git fetch bitbucket

# download and merge remote branch from (from origin by default)
git pull

# push changes from master to upstream repo (origin in this case)
git push origin master

# push changes from local branch to upstream branch
git push remote-repo branch-name

# push changes from local branch to upstream branch with different name
git push remote-repo my-branch:their-branch

# show more info about particular remote
git remote show origin

# rename a remote
git remote rename bitbucket bb

# remove a remote 
git remote rm bitbucket

# list all available tags
git tag

# list tags matching a pattern
git tag -l "v1.8.5*"

# create an annotated tag
git tag -a v1.4 -m "software version 1.4"

# see the annotated tag data
git show v1.4

# create a lightweight tag
git tag v1.4

# create a tag fro specific commit
git tag v1.4 <commit-hash>

# push tag to remote server (git push does not work with tags by default)
git push origin v1.4

# push all tags
git push origin --tags

# create a new brach with a specific tag
# git checkout does not work with tags, need to create a branch (??)
git checkout -b [branch-name] [tag-name]

#create and switch to local branch to track a remote one
git checkout -b my-branch origin/my-branch

# set alias for git command
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'

# create new branch but do not yet switch to it
git branch branch-name

# show what branch you're on
git log --oneline --decorate

# switch branch
git checkout branch-name

# create a branch and switch to it
git checkout -b branch-name

# merge (and commit if successful) another branch
git merge branch-name

# merge favoring their side of conflict
git merge -X theirs branch-name

# delete a branch
git branch -d branch-name

# list existing branches
git branch

# list branches and show last commit
git branch -v

# list already merged branches
git branch --merged

# list not yet merged branches
git branch --no-merged

# force delete brach containing edits not yet merged
git delete -D branch name

# see full list of remote references
git ls-remote [remote]
git remote show [remote]

# track remote branch
git checkout --track remote/branch
git checkout remote/branch

# track another remote branch
git branch -u remote/branch

# see what branches are being tracked
git branch -vv

# fetch from all remotes
git fetch --all

# delete a remote branch
git push origin --delete branch-name

# rebase - take all changes made in current branch and apply them to another
# the end result is pretty much the same as merge
git rebase new-base-branch

# replay onto new base changes made in branch-2 in relation to branch-1 (changes made in branch-1 not included)
# 
# c1-c2-c5-c6-[new-base-branch]
#     Lc3-c4-c10-[branch-1]
#       Lc8-c9-[branch-2]
#     
#     results in
#
# c1-c2-c5-c6-[new-base-branch]-c8-c9-[branch2]
#     Lc3-c4-c10-[branch-1]
#
git rebase --onto new-base-branch branch-1 branch-2

# rebase branch-1 onto base-branch
git rebase base-branch branch-1

# get total number of lines changed since the given date in c++ files
git log --stat --since "02/23/2016" --no-merges | grep -E "(\.cpp)|(\.hpp)" | awk "{s+$3} END {print $3}"

# set up a read-only remote 
git remote add origin-readonly https://url.to/remote.git
git remote set-url origin-readonly --push "You shall not push" 

# remove unstaged files
git clean -f

# discard all unstaged changes
git checkout -- .

# remove modifications
git reset --hard

# revert a commit
git revert dd61ab32

# delete the last commit, where x^ is the parent of x, + is a forced non-fastforward push
git push origin +dd61ab32^:master

# delete the last commit
git reset HEAD^ --hard
git push -f

# merge specific commmit (could be any remote)
git merge <hash>

# squal commits
git merge --squash master
git merge --squash origin/master


#glossary
tracking branch - tracks an upstream branch, pulling on this branch would pull the upstream
upstream branch - resides on a remote server and being tracked by the tracking branch

