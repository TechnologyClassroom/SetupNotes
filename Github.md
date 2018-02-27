# Github notes

Github is a great way to collaborate with other programmers on the Internet.

Sign up is easy and free.

Github Markdown Reference for README.md files
https://guides.github.com/features/mastering-markdown/

Anchor links in Markdown
http://stackoverflow.com/questions/5319754/cross-reference-named-anchor-in-markdown

Modifying wiki pages like other code repositories
https://help.github.com/articles/adding-and-editing-wiki-pages-locally/

## Troubleshooting

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
