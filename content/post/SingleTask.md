+++
author = "RsyncOSX"
date = "2020-04-16"
title =  "Executing single tasks"
tags = ["single task","edit tasks"]
categories = ["synchronize"]
description = "Execute single task, first a verify run and then the real run."
lastmod = "2020-07-16"
+++
In Synchronize view (which is the opening view) tasks can be executed as singletasks. Execute single tasks requires a couple of double clicks: one for **estimation** run and the second for **executing** the real task. The output from rsync is presented after each run.

![](/images/RsyncOSX/master/singletask/singletask.png)

There are three options for editing after selecting a task in row:
- edit
- params (to rsync)
- delete task

After selecting a row choosing one of the above pops up a new view according to selection. Select Edit task to editing basic information about task. Select Delete task to delete the selected row (task).

The `Shell` column is on, it indicates there is attached pre and post shell scripts to the task, also see more info about shell command in the [add configuration](/post/addconfigurations/).

## Execute single task

Execute single tasks is a two step operation, one for estimation (dry-run) and one for the real task. A drop down view is automatically presented after both tasks. A single task is executed by  a double click on the selected task/row. There are five numbers in bottom page. Only version 3.x counts the number of remote directories. The numbers are files to be transferred and remote numbers. Another double click executes the real run and a progress bar is presented.

The actual rsync command to be executed is shown below right corner in view. It is only the estimation command which is shown. You might copy the command and paste it into a terminal for execution. You have to delete the --dry-run parameter to execute the real task.

If Abort is pressed any executing task is aborted.

## Edit and params

The edit enables changing the basic info about the task. The user can add, edit, enable and disable executing shell commands to the synchronize task.

![](/images/RsyncOSX/master/singletask/edit.png)

The params enables access to add and change parameters to rsync. See more info about [default parameters](/post/rsyncparameters) and [user selected parameters](/post/userparameters/).

![](/images/RsyncOSX/master/userparameters/userparameters.png)
