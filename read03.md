Read: 03 - Revisions and the Cloud

Git Tutorial: A Comprehensive Guide

Version Control
Version Control is a system that allows you to revisit various versions of a file or set of files by recording changes. Through version control, one can revert a file or project to a previous version, track modifications and modifying individuals, and compare changes. By utilizing a Version Control System (VCS), mistakes with files can easily be rectified.

Local Version Control
Many years ago, programmers created Local Version Control systems. A Local VCS entails one database on your hard disk that stores changes to files.

Centralized Version Control
The need for collaboration within a developer team on a single file or set of files led to the advent of the Centralized Version Control System (CVCS). This system entails a single server storing all changes and file versions, which can be accessed by various clients. This streamlined the collaboration process (by eliminating the need to involve all local databases), allowed programmers to have more knowledge of team members’ activities with certain files, and gave administrators much more control over divvying up revision privileges.

Distributed Version Control
A Distributed Version Control systems (DVCS) addresses the major vulnerability of the CVS: the server as a single point of failure. If a CVS goes down, collaborators cannot work with each other on a file or save changes and new versions. Also, in the event of corruption of a central database’s hard disk — with the absence of backups — all work will be lost, except for any portions on local machines.

To prevent this type of catastrophic loss, a DVCS allows clients to create mirrored repositories. These data backups can be easily be placed on the server to replace any lost information.

Because the DVCS allows for multiple mirrored repositories, programmers working in teams can collaborate with each other in various ways to complete a joint project, which enables the use of various simultaneous workflows.

So, what is Git?
Snapshots

Git is a DVCS that stores data in a file system made up of snapshots. Each time you save a changed version of your project — called commit — Git creates a snapshot of the file and stores a reference to it. If the file has not changed, Git only stores a reference to the already-stored identical version of it.

Local Operations

Git mostly relies on local operations because most necessary information can be found in local resources. This allows for process expediency because a project’s history resides on the local disk, eliminating the need to fetch history information from the server, and allowing one to continue work on a project even when not online or on a VPN.

Tracking Changes

Every single change applied to any file or directory is tracked by Git. And, as the gatekeeper, Git will always detect file corruption or loss of information in transit.

Loss of Data

Git is set up to greatly minimize the possibility of irreversible damage to files, such as accidentally lost data. Git makes it extremely difficult for a snapshot of your file that is committed to be lost.

States

Files in Git can reside in three main states: committed, modified and staged.

Committed

Data is securely stored in a local database

Modified

File has been changed but not committed to the database

Staged

Flagged a file’s changed version to be committed in the next snapshot

image06

Setting up a Git Repository
Importing
To import an existing project or directory into Git, follow these steps using the Terminal or Command Line:

Switch to the target project’s directory
Example:

$ cd test (cd = change directory)
Use the git init command
$ git init
Note: At this stage, you have created a new subdirectory named .git that has the repository files. Tracking has not commenced.

To start tracking these repository files, perform an initial commit by typing the following:
$ git add *.c
$ git add LICENSE
$ git commit -m “any message here”
Now, your files are tracked and there’s an initial commit. We will discuss the particular commands in detail soon.

Cloning
You can also create a copy of an existing Git repository from a particular server by using the clone command with a repository’s URL:

$ git clone https://github.com/test
By cloning the file, you have copied all versions of all files for a project. This command leads to the creation of a directory called “test,” with an initialized .git directory inside it, which has copies of all versions of all files for the specified project. The command also automatically checks out — or retrieves for editing — a copy of the newest version of the project.

To clone a repository into a directory with another name of your choosing, use the following command format:

$ git clone https://github.com/test mydirectory
The command above makes a copy of the target repository in a directory named “mydirectory.”

Workflow
Local Repository Structure
The local Git repository has three components:

Working Directory: The actual files reside here.
Index: The area used for staging
Head: Points to the most recent commit
image03

Saving Changes
All files in a checked out (or working) copy of a project file are either in a tracked or untracked state.

Tracked

Tracked files can be modified, unmodified, or staged; they were part of the most recent file snapshot.

Untracked

Untracked files were not in the last snapshot and do not currently reside in the staging area.

*After cloning a repository, files have tracked status and are unmodified because they have been checked out but not edited.

he Life Cycle of File Status
After you edit a file, Git flags it as modified because of changes made after the previous commit.
You stage the modified file.
Then, you commit staged changes.
image00

Check File Status
To determine the state of files, utilize the git status command:

$ git status
On branch master

nothing to commit, working directory clean

*This information indicates which branch you’re on (we will cover branches in a later section) and states “working directory clean,” which means that files have tracked or modified status at the moment. Also, no untracked files are present because Git has not listed any.

Tracking and Staging a New File
Single File

Track one file only by using the following format:

git add filename
All Files

Track all files in a repository by using the following command:

$ git add *
*After using these commands, files are tracked and staged for committing.

After adding a new file called EXAMPLE, you would see information regarding changes to be committed when using the git status command:

$ git status

On branch master

Changes to be committed:

  (use "git reset HEAD ..." to unstage)
new file: EXAMPLE
This information tells us that there are changes to be committed and that the file has been staged.

Committing a File
After staging one or multiple files, you should commit the changes and record what you did within the commit message:

$ git commit -m “made change x,y,z”
*This step has committed changes for the file or files (you can have one commit message for multiple files, if applicable) to the HEAD.

Committing All Changes
$ git commit -a
*This command commits a snapshot of all modifications to tracked files in the working directory.

Pushing Changes
Next, you would push changes to a remote repository. We will discuss remote repositories in more depth in the next section. For now, we will look at a general overview of pushing changes to remotes.

Example:

$ git push origin master
*This command pushes changes from the local “master” branch to the remote repository named “origin”.

*For cloned repositories, Git will automatically give the name “origin” to the server from which you cloned and the name “master” to your local repository. However, these names can be changed by the user.

Git students also learn

Stashing Changes
When you are not ready to commit changes but do not want to lose them either, git stash is a great option. This command temporarily removes changes and hides them, giving you a clean working directory. When you are ready to continue working on the changes, simply use the git stash apply command to retrieve the hidden changes.

Remote Repositories
In order to collaborate on Git projects, you must interact with remote repositories, versions of a project residing online or on a network. You can work with multiple repositories, for which you can have read/write or read-only privileges. Teams can use remote repositories to push information to and pull data from.

Cloned Repositories
As mentioned earlier, for cloned repositories, Git will automatically give the name “origin” to the server from which you cloned and the name “master” to your local branch.

Seeing Your Remotes
By running the git remote command, you can view the short names, such as “origin,” of all specified remote handles.

By using git remote -v, you can view all the remote URLs next to their corresponding short names.

$ cd example

$ git remote -v

remote1 https://github.com/remote1/example (fetch)

remote1 https://github.com/remote1/example (push)

remote2 https://github.com/remote2/example (fetch)

remote2 https://github.com/remote2/example (push)

remote3 https://github.com/remote3/example (fetch)

remote3 https://github.com/remote3/example (push)
Adding Remotes
To create a new remote Git repository with a short name, use the following format:

git remote add shortname url
Example:

$ git remote

origin

$ git remote add js https://github.com/janesmith/project1

$ git remote -v

origin https://github.com/johndoe/project1 (fetch)

origin https://github.com/johndoe/project1 (push)

js     https://github.com/janesmith/project1 (fetch)

js     https://github.com/janesmith/project1 (push)
This addition of these remote and short names allows you to use shortnames for Git collaboration.

Fetching
Fetching entails pulling data that you don’t have from a remote project.

Here is the command format:

git fetch [remote-name]
*Now, you should also possess the references to all branches for that remote (more on branching later).

Cloned Repositories

For cloned repositories, use the command git fetch origin to pull down any new changes that were pushed to the server since you cloned or last fetched from it.

Note: git fetch solely pulls new data to a local repository; it does not merge changes with or modify your local work. We will discuss merging in a later section. Later, we will also discuss git pull , which allows for fetching and automatic merging.

Pushing
To push your changes “upstream” for sharing, you would use the following git push command format:

git push [remote-name][branch-name]
Example:

$ git push origin master
*This command pushes committed changes from your local “master” branch upstream to the “origin” server.

Note: You can only successfully push changes upstream if you have write access for the server from which you cloned, and if someone else has not pushed changes upstream that you haven’t pulled yet. If a collaborator pushed changes upstream after you had cloned, your push will not be successful. You will have to pull new changes and merge them with your branch before you can successfully push your changes upstream.

Renaming/Removing Remotes
Rename

To rename a remote’s short name, use the git remote rename command.

Example:

$ git remote rename js jane

$ git remote

origin

jane
*In the example above, we can see that the remote’s short name has been changed from js to Jane. The command git remote lists our existing remotes, which jane is now one of. The rename action also alters names of remote branches: js/master would change to jane/master.

Remove

To remove a remote for whatever reason (e.g., a contributor has left the team, the server has moved), simply use the git remote rm command:

Example:

$ git remote rm jane

$ git remote

origin
NOTE: Reminder: “origin” is simply the default remote name when you use the git clone command.

Undoing Actions
Git has mechanisms for undoing certain actions.

Commit Mistakes
You can use the –amend command when you need to alter a commit message or forgot to add some files.

$ git commit --amend
In the example above, you can use this command to easily change your commit message, if no changes were made since the newest commit.

$ git commit -m “my first commit”

$ git add example_file

$ git commit --amend
In the above example, a forgotten file is added to a commit.

Unstaging a File
$ git reset HEAD index.html

Unstaged changes after reset:

M index.html
Above, we see that the git reset HEAD command unstaged the index.html file.

NOTE: When git reset --hard is used, Git overwrites all changes in the working directory, permanently destroying any uncommitted changes.

Undo a Committed Snapshot
To undo changes resulting from a particular commit, use the git revert command. This command appends a new commit that undoes changes introduced by a specific commit. This prevents Git from losing history.

$ git commit -m "Example Commit"

$ git revert HEAD
*In the example above, a new commit gets appended and rolls back changes from a specific commit.

Unmodifying a File
To have a file return to its state when you last committed, utilize the git checkout command.

Example:

$ git checkout -- index.html
NOTE: git checkout -- file erases any changes made to the file because you are copying another file over it. Almost all committed information in Git can be recovered; however, any uncommitted information can be lost forever.

Branching
Almost every type of Version Control System incorporates branching. By creating branches of a central repository, collaborators are able to work on a project simultaneously via multiple branches, without affecting this main repository.

A collaborator can create a branch, work on it and save commit snapshots within it, switch between various branches, and merge changes. A Git branch is basically a movable pointer that always points to the most recent commit, or snapshot. Git uses the default local branch name “master,” which can be changed. Just because the default name is “master” does not imply that it is higher in importance or has more functionality than other branches. The head is a special pointer which indicates which branch you are currently working within.

image01

Creating a New Branch
To create a new branch, use the git branch name format:

$ git branch test
*The above command creates a new branch named “test” that points toward your most recent commit. However, this command does not switch you over to this new branch.

image02

Switching Branches
To switch to another branch, use the git checkout command.

$ git checkout test

*This command moves the HEAD pointer to the test branch

image08

If you make a commit while on the test branch, only this branch will point to the most recent commit. The master branch will still point at the commit it was pointing to when you checked out to the test branch. So, if you switch back to the master branch, none of your recent changes made on the test branch will exist on the master branch.

Create a Branch and Checkout
To simultaneously create a new branch and switch to it, use the -b switch with the git checkout command:

$ git checkout -b test2
*The command above creates a new branch “test2” and switches you to it.

List Branches
You can list available branches by using the git branch command.

$ git branch

*master
Above, we see that we have one local branch, named “master”.

Merging
When you want to merge changes from one branch into your current one, you can use the git merge command.

Fast-Forward Merging
With a fast-forward merge, your current branch’s pointer moves forward to the most recent commit for the branch being merged in – there is no divergent work to merge together because the latter branch is directly upstream in relation to the former one.

Example:

$ git checkout master (switches you to the master branch)

$ git merge test (merges in changes from test branch)

Updating c58d775 .. 8b9205d

Fast-forward

index.html| 4 ++

1 file changed, 4 insertions(+)
image05

In the diagram above, the Master branch, which previously pointed at Commit 3, now points at Commit 4, after fast forwarding and merging in changes from the Test branch – made possible by the fact that Master had not diverged from the latter.

No Fast-forward
When you use the git merge --no-ff <branch> command, instead of a branch simply moving its pointer forward, a new commit object is created. The –no-ff flag is often used to prevent the loss of historical information regarding a merged-in branch.

$ git merge test --no-ff
Three-way Merge
In cases of branches diverging, fast-forward merges are not an option. A three-way merge can be used, however. This type of merge involves the two latest commit snapshots pointed to by both branches, and their common ancestor. Here is an example of creating a three-way merge:

$ git checkout master

$ git merge test
image07

Instead of just moving the branch pointer forward, Git creates a new snapshot that results from this three-way merge and automatically creates a new commit that points to it. This is referred to as a merge commit, which is special because it has more than one parent.

Fetch and Merge
To easily fetch and merge remote changes, use the git pull command in your working directory.

Deleting Branches
After you’ve merged branches, and they’re no longer needed, you can easily delete them with the -d flag.

Example:

$ git branch -d test
*This deletes the “test” branch.

Merge Conflicts
When the two files being merged both have changes in identical sections of a file, Git will not be able to complete the merge cleanly. These conflicts must be dealt with manually. Portions of files with unresolved merge conflicts will be labeled “unmerged”.

You can easily locate areas of merge conflict via Git’s conflict resolution markers, which appear in applicable files.

Example:

My name is

 <<<<<<< HEAD

 Jane

 =======

 Mary

 >>>>>>> branch-test
Here, HEAD indicates the branch you checked out before running the merge command. The content above the ======= resides within this branch, while everything below it is within the test branch. As you can see, the conflict is that Jane and Mary conflict with each other. After fixing this conflict and removing the ======= and >>>>>>> lines, run the git add command on fixed files to mark them as resolved.

To view unmerged files, use the git status command.

$ git status
# On branch master

# Unmerged paths:

# (use “git add/rm …” as appropriate to mark resolution)

#

# both modified: index.html

#

*Here, we see that there is a merge conflict in index.html.

Preview Changes
To preview changes for merging, use the git diff command in the following format:

git diff <source_branch> <target_branch>
Listing Branches
To list local branches, use the git branch command. The branch currently being worked on will have an asterisk next to its name.
Example:

$ git branch

*master

test
See Latest Commits
To see the newest commits for each branch, use the git branch-v command.

$ git branch -v

*master 51g222e updated html file

test 52c667a updated JavaScript file
The useful --merged and --no-merged options can filter this list to branches that you have or have not yet merged into the branch you’re currently on. To see which branches are already merged into the branch you’re on, you can run git branch --merged:

$ git branch --merged

test

 * master
Because you already merged in test earlier, you see it in your list. Branches on this list without the * in front of them are generally fine to delete with git branch -d; you’ve already incorporated their work into another branch, so you’re not going to lose anything.

To see all the branches that contain work you haven’t yet merged in, you can run git branch --no-merged:

$ git branch --no-merged

testing
Rebasing
A popular alternative to merging is rebasing.

The Basics
Rebasing starts with the common ancestor of two branches: the one you’re on and the one you’re rebasing onto. Then, the diffs resulting from each commit of your current branch are saved to temporary files, and the current branch gets reset to the same commit as that of the branch you are rebasing onto. Last but not least, all changes get applied to the branch you are rebasing onto.

This process essentially rewrites a project’s history by replaying all changes committed on one branch to another one, leading to cleaner application of commits on a remote branch and a linear history.

Example:

$ git checkout test

$ git rebase master
image04

In this example, changes committed on commit 4 are replayed onto commit 3, allowing a fast-forward merge of master and the creation of a clean, linear history.

Rebase Caveat: Avoid rebasing commits that are not within your repository; this could lead to confusion and inefficiency.

Rebase vs. Merge
There are opposing viewpoints regarding merging and rebasing.

Pro-merge argument

The true commit history of a repository should not be altered because it’s a record of occurrences.

Pro-rebase argument


Commit histories should be polished and well edited.

Log
You can utilize the git log command to view committed snapshots. You can use the command to see a project’s history, use a filter, and find specific modifications. Here are example uses of the git log command:

$ git log
This command lists the exhaustive commit history in default formatting.

$ git log -n 3
This command line only allows for 3 displayed commits.

$ git log --stat
This command results in the display of regular git log information, as well as information on which files underwent modification and the relative numbers of line deletions and additions from each of them.

$ git log -p
This command shows the full diff of each commit.

$ git log --grep="updated"
With this command, one can search for commits containing the string “updated.”

$ git log --author="smith"
The command above allows for a specific search for commits by an author whose name includes the string “smith.”

$ git log index.html
The command above will display only those commits including the index.html file.

$ git log --oneline
This command presents repository information in a single line, so you can get a high-level overview.

*Additional git log commands can be accessed via git log --help.

Tagging
With the use of tags, Git can flag certain points in a project’s history as being significant.

To list available Git tags, use the git tag command:

Example:

git tag

 v1.0

 v2.0

 v3.0
To list only particular types of tags, use the git tag -l command:

Example:

git tag -l “v1.2.9”

 v1.2.9

 v.1.2.9.1

 v.1.2.9.2

 v.1.2.9.3
Create a Tag
There are two main categories of tags in Git: lightweight and annotated.

Lightweight

A lightweight tag is a pointer to a particular commit – like a branch.

Annotated

An annotated tag is stored in the Git database as a full object, containing a tagging message, tagger name and email, and tag date. Annotated Tags can also undergo signing and verification with GNU Privacy Guard (GPG). The best practice is to use annotated tags when possible, to allow for storage of valuable information and privacy safeguards.

Create Annotated Tags

To create an annotated tag, use -a with the git tag command.

Example:

$ git tag -a v2.0 -m “my version 2.0”

$ git tag

v1.0

v1.5

v2.0
Above, we see that the v2.0 tag has been created. We used -m for a specific tagging message.

To see the tag data and corresponding commit, use the git show command.

Example:

$ git show v2.0

  tag v2.0

Tagger: Jane Smith

Date: Tues Aug 25 18:16:00 2015 -0700

my version 2.0

commit ka93a8dfg718ce54f00342227218580a92764449

Author: John Doe

Date: Wed Mar 19 20:38:12 2008 -0700
Note: After the word “commit,” we see a checksum – a hash value containing 40 characters – which is stored in a file.

Create Lightweight Tags

A lightweight tag for commits only holds a checksum. To create a lightweight tag, simply utilize the git tag command without using -a, -s, or -m.

Example:

$ git tag v2.5

$ git tag

v1.0

v1.5

v2.0

v2.5

For the lightweight tag above, git show would only display the commit:

$ git show v2.5

commit p641d7dff657pc77f33442017208880k91563822

Author: John Doe

Date: Wed Mar 19 20:33:05 2008 -0700

changed the version number
Tag Sharing
Users must push tags to shared servers after creation because, by default, the git push command does not send tags to remote servers.

To push tags to shared servers, use the git push origin [tagname] command.

To push all of your tags at once, use the --tags option for the git push command.

Example:

git push origin --tags
Note: Anyone who pulls from your repository or clones it will also receive all of your tags.

Tag Checkout
Because you cannot move tags around, they cannot be checked out in Git. However, you can create a new branch at a specific tag with the git checkout -b [branchname][tagname] command.

Aliases
Aliases allow users to navigate Git in an easier fashion. To save time and effort, one can create aliases for Git commands, which eliminates the need to type out an entire default Git command.

You can set up aliases using the git config command.

Example:

$ git config --global alias.br branch

$ git config --global alias.st status

$ git config --global alias.co commit
The above commands allow the user to simply type git br, git st, or git co, instead of git branch, git status, or git commit.

You can also create new commands with an alias.

Example:

$ git config --global alias.stage “add”
The above command makes git stage equivalent to git add.

Many people create a last command for viewing the most recent commit.

Example:

$ git config –global alias.last “log -1 HEAD”

Ignoring Files
Usually, untracked files consist of uncommitted files recently added to a project or compiled binaries with extensions such as .exe and .obj. Compiled binaries can make it difficult to clearly monitor your repository. Git allows users to avoid this situation by ignoring certain files by sending them to a special file with the name .gitignore.

Note: It’s always wise to check your repository before committing anything, to avoid accidentally committing certain files.

Files that all developers should disregard go into a .gitignore file.
Every line within a gitignore file indicates a pattern.
Additional information regarding gitignore files can be found here.

Distributed Workflows
As we mentioned earlier, distributed workflows allow developers collaborating on projects much more flexibility. Every developer using Git can be both a node and a hub; this means he/she can own a main repository which collaborators contribute to and base their work off of while also contributing code to other repositories. This opens up the possibilities for workflows immensely.

For now, we are only going to discuss a couple of the most common distributed workflows.

Centralized Workflow
The centralized workflow entails the existence of one main hub, which can accept code. In this type of structure, many developers synchronize to this central repository, pushing and merging changes to it.

Integration-Manager Workflow
This workflow structure involves multiple remote repositories. In this scenario, there is often one main project repository, and developers can have read access to others’ repositories and write access to their own. Those involved in the Integration-Manager Workflow create clones of the main project repository, push any changes to it, and ask the repository maintainer to pull in the pushed changes. The maintainer can add someone’s repository as a remote, test changes locally, merge them into their branch, and push back to their repository.

This workflow is commonly found with hub-centered resources, such as GitHub (we’ll talk about GitHub in the next section).

GitHub
As previously mentioned, GitHub is a hub-focused tool which facilitates Integration-Manager Workflow. It is the largest existing host for Git repositories and is used by millions of developers worldwide. A high percentage of Git repositories reside on GitHub, and this resource is used by many open source projects.

Getting Started
First, in order to use GitHub, you must set up a free user account. You can easily do this by visiting https://github.com.

Contributing to Projects
To contribute to a project which you do not have push privileges for, you can “fork” a project, which means you will have your own copy of it, which you can freely push to. To complete a “fork,” look for the Fork button at the top right of the project page.

General Workflow
GitHub’s collaboration workflow revolves around Pull Requests.

Here are the main steps of the GitHub collaboration workflow:

Create a topic branch from master.
Commit changes for the project.
Push the topic branch to the GitHub project.
Open a Pull Request.
Confer with team and perform additional commits, if applicable.
The project owner closes or merges the Pull Request.

