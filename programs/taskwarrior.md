# Taskwarrior

Taskwarrior or `task` is a command line task manager or todo list.

[Website](https://taskwarrior.org/)

[Doc: Usage examples](https://taskwarrior.org/docs/examples.html)

[Doc: Best practices](https://taskwarrior.org/docs/best-practices.html)

[GitHub](https://github.com/GothenburgBitFactory/taskwarrior)

## Install

Debian based systems can simply install through `apt`.

    sudo apt update && sudo apt install -y taskwarrior

## Create a new task

Tasks can be added with `task add`.  Optionally, tasks can be grouped by project and subproject.

Syntax:

    task add project:GROUP.SUBGROUP TASKDESCRIPTION

Real example:

    task add project:work.conference Configure Minetest server.

The task will be given a number.

## List tasks

Preview of some tasks across all projects.

    task

List all tasks.

    task list

List tasks by two or more projects:

    task project:git or project:work list

## Modify a task

Tasks can be modified.  Individual pieces after modify are optional.

Syntax:

    task NUMBER modify project:NEWPROJECT NEWDESCRIPTION

Change description of task 9.

    task 9 modify Make a list of new members that need physical mail.

Change project of task 12.

    task 12 modify project:work.fundraiser

## Mark a task as complete

    task 37 done

That felt good!

## Delete a task

    task 38 del

Read the confirmation text to make sure you are deleting the correct task.  To confirm type `yes` enter.

## Review completed tasks

What did I finish since last Tuesday?

    task end.after:$(date -d 'last-tuesday' +%Y-%m-%d) completed

## Shortcuts

Some of the commands can be very verbose, abbreviate common commands as aliases within your `$HOME/.bashrc` file.

```
alias taskh='task project:garden or project:home list'
alias taskw='task project:git or project:work list'
alias taskaweb='task add project:work.web'
```

After saving and starting a new terminal session, these can be used easily.

List only work tasks.

    taskw

Add a new task to the project `fsf.lp`.

    taskaweb Write blog post.
