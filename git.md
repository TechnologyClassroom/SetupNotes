# git

git is a great way to track changes to text files.

https://git-scm.com/

## Troubleshooting

Problem: I overwrote one of my scripts and I was able to track down the change
and recover my lost code.

```git whatchanged```

I looked for recent commits that involved the overwritten file.

```git diff c4d6ee5cdf4f170e27731999cac63191134e06c6```

Replace ```c4d6ee5cdf4f170e27731999cac63191134e06c6``` with the unique identifer
for the commit.

The diff shows patch style changes included in the commit.  I found my lost
code.

Problem: One optional folder in a repo is adding a large amount of size to an
otherwise very small repository.
Solution: Remove the folder and its history from the repo.

This is also userful if you accidentally add a password or sensitive
information to a public repo.

Based on Mohsen, Mathias Bynens, knocte, and Lázaro Clapp from
https://stackoverflow.com/questions/10067848

Note: Backup the folder into another repository first.

```
git clone http://github.com/technologyclassroom/dice-mechanic-sim
cd dice-mechanic-sim
git remote set-url origin git@github.com:TechnologyClassroom/dice-mechanic-sim.git
git rm -fr data
git add .
git commit -m "Remove data packs"
git push origin master
```

This deleted the folder, but the size of the repo stayed the same near 25mb.
These commands pruned the history destructively:

```
git filter-branch --tree-filter 'rm -rf data' --prune-empty HEAD
git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d
git commit -m 'Removing data from git history'
git gc
git push origin master --force
```

Now the repo is under 1mb.
