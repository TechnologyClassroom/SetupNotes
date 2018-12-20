# Github notes

Github is a great way to collaborate with other programmers on the Internet.

Sign up is easy and free.

Github Markdown Reference for README.md files
https://guides.github.com/features/mastering-markdown/

Anchor links in Markdown
http://stackoverflow.com/questions/5319754

Modifying wiki pages like other code repositories
https://help.github.com/articles/adding-and-editing-wiki-pages-locally/

## Usage

Clone a repository.

```git clone https://github.com/TechnologyClassroom/SetupNotes```

Change to that directory.

```cd SetupNotes```

Save a change using your favorite text editor.

```vim Github.sh```

Let git know which file you are updating.

```git add Github.sh```

Or add all files to git.

```git add .```

See which files changed.

```git status```

See the changes in those files.

```git diff HEAD```

Commit the changes with a message.

```git commit -m "Added basic usage for Github."```

Commit the changes.

```git push origin master```
