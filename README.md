# Git-Commands-line-Practice 
 https://levelup.gitconnected.com/10-must-know-git-commands-for-software-engineers-ffc6687d6dfd
# 10 Must-Know Git Commands for Software Engineers

# Git Commands that are a Must-Know

Git and GitHub are the most fundamental things that every Software Engineer must know. These tools are integral to a developer’s daily routine,
as we interact with them daily. Proficiency in Git not only simplifies your life but also enhances productivity significantly. 
In this blog post, we’ll explore a set of commands that will supercharge your productivity. As you become more proficient with these commands, 
you’ll save valuable time and become a more effective software engineer.

# Git Vocabulary
Now, before we dive into exploring Git commands one by one, let’s familiarize ourselves with some essential Git terms. 
This will not only help you better understand the commands but also prevent confusion down the road when these terms are used in the later part of this blog.

# HEAD
In Git, HEAD is a special pointer/reference that always points to the latest commit in the current branch. When you make a new commit, 
HEAD move forward to point to that new commit. For example, if you’re on the main branch and you make a new commit, 
HEAD will now point to that new commit, indicating that it's the most recent one in the main branch.

# ^ (Caret Symbol):
The ^ symbol in Git serves as a means to navigate through your project’s historical timeline. When you employ HEAD^, 
it references the commit immediately preceding your current one. If you append a number following ^, such as HEAD^2, it references the second 
commit preceding your current commit. In short, the ^ symbol allows you to traverse backwards in your project’s history, while the numerical value allows 
you to precisely determine the number of commits you wish to go back.

# Staging
Staging is where you assemble the changes you want to include in your next commit. Staging allows you to carefully curate your commits, 
making it easy to review, organize, and refine your modifications. With staging, you have control over what gets included in your commit. 
To stage changes, you use the git add command, which is akin to declaring, "I want these changes to be part of my next commit."



# Now let’s explore the 10 Git commands one by one.


# Let’s get started

# 1-Adding and Committing Files Together

Typically, in Git, we use the git add * command to stage all modified files for a subsequent commit. Afterwards, we utilize the git commit -m "commitMessage" command to commit these changes. 
However, there exists a more streamlined command that accomplishes both tasks in a single step:

# git commit -am "commitMessage"
The -am flag allows us to not only stage these changes but also commit them in one efficient operation.

# 2-Creating and Switching to a Git Branch
Similar to the previous scenario, there’s another command that combines the functionality of the two commands. Instead of using two separate commands, 
git branch branchName to create a branch and then git checkout branchName to switch to it, you can achieve both tasks in a single step with the following command:

# git checkout -b branchName
The -b flag with the git checkout command allows us to not only create a new branch but also immediately switch you to it.

# 3-Delete a Git Branch
To delete a branch in Git, you can use the git branch -d or git branch -D command. The -d option is for a safe deletion, 
which will only delete the branch if it has been fully merged into the current branch. The -D option is for a forceful deletion, 
which will delete the branch regardless of whether it's fully merged or not. Here are the commands:

Safe deletion (checks for merge):

# git branch -d branchName
Forceful deletion (doesn’t check for merge):

# git branch -D branchName


# 4-Renaming a Git Branch
To rename a branch, you can use the git branch -m command followed by the current branch name and the new desired branch name. For example, if you want to rename a 
branch called oldBranch to newBranch, you would run:

# git branch -m oldBranch newBranch
However, if you want to rename the current branch where you are working right now, without specifying the old name explicitly, you can use the following command:

# git branch -m newBranchName
Here, you don’t need to specify the old branch name because Git will assume that you want to rename the current branch to the new name.

# 5-Unstaging a Specific File
Sometimes, you may want to remove a particular file from the staging area, allowing you to make additional modifications before committing. Use:

# git reset filename
This will un-stage that file while keeping your changes intact.

# 6-Discarding Changes to a Specific File
If you want to completely discard the changes made to a specific file and revert it to its last committed state, utilize:

# git checkout -- filename
This command ensures that the file returns to its previous state, undoing any recent modifications. It’s a helpful way to start fresh on a 
particular file without affecting the rest of your changes.

# 7-Updating Your Last Git Commit
Imagine you’ve just made a commit in your Git repository, but then you realize that you forgot to include a change in that commit, or perhaps you want 
to fix the commit message itself. You don’t want to create a whole new commit for this small change. Instead, you want to add it to the previous commit. 
This is where you can use the command:

# git commit --amend -m 'message'
This command modifies the most recent commit you made. It combines any staged changes (ones you’ve added with git add) with your new comment to create an updated commit.

A thing to remember is that if you have already pushed the commit to a remote repository, you will need to force push the changes using git push --force to update the remote branch. 
Because a standard git push operation appends a new commit to your remote repository rather than modifying the last commit.

# 8-Stashing Changes
Imagine you’re working on two different branches, A and B. While making changes in branch A, your team asks you to fix a bug in branch B. When you attempt to 
switch to branch B using git checkout B, Git prevents it, displaying an error:


" Unable to change branch
We can commit our changes as suggested by the error message. But committing is more like a fixed point in time, not an ongoing work in progress. 
This is where we can apply the error message’s second suggestion and use the stash feature. We can use this command for stashing our changes:"

# git stash

git stash temporarily saves changes that you're not ready to commit, allowing you to switch branches or work on other tasks without committing incomplete work.
To reapply stashed changes in our branch, you can use git stash apply or git stash pop. Both commands restore the latest stashed changes. 
Stash applying simply restores the changes, while popping restores the changes and removes them from the stash. You can read more about stashing over here.

# 9-Reverting Git Commits
Imagine you’re working on a Git project, and you discover that a particular commit, introduced some undesirable changes. 
You need to reverse those changes without erasing the commit from history. You can use the following command to undo that particular commit:

# git revert commitHash
It’s a safe and non-destructive way to correct errors or unwanted alterations in your project.

For instance, let’s say you have a series of commits:

Commit A
Commit B (undesirable changes introduced here)
Commit C
Commit D
To reverse the effects of Commit B, you would run:

# git revert commitHashOfB

Git will create a new commit, let’s call it Commit E, which negates the changes introduced by Commit B. 
Commit E becomes the latest commit in your branch, and the project now reflects the state it would have been in if Commit B had never happened.
If you’re wondering how to retrieve a commit hash, it’s straightforward using git reflog. In the screenshot below, 
the highlighted portions represent the commit hashes that you can easily copy:



# 10-Resetting Git Commits
Let’s assume you’ve made a commit to your project. However, upon inspection, you realize that you need to adjust or completely undo your last commit. 
For such a scenario, Git provides these powerful commands:

-- Soft reset

# git reset --soft HEAD^

When you use git reset --soft HEAD^, you are performing a soft reset. This command allows you to backtrack on your last commit while preserving all your changes in the staging area. 
In simple words, you can easily uncommit while retaining your code changes, using this command. It is handy when you need to revise the last commit, perhaps 
to add more changes before committing again.

-- Mixed reset

# git reset --mixed HEAD^

This is the default behaviour when you use git reset HEAD^ without specifying --soft or --hard. 
It un-commits the last commit and removes its changes from the staging area. However, it keeps 
these changes in your working directory. It is helpful when you want to un-commit the last commit and make changes 
from scratch while keeping the changes in your working directory before re-committing.

-- Hard reset

# git reset --hard HEAD^
Now, let’s talk about git reset --hard HEAD^. It completely erases the last commit along with all 
the associated changes from your Git history. When you use --hard flag, there's no going back. 
So use this with extreme caution when you want to discard the last commit and all its changes permanently.

Thank you for reading. I hope this post is helpful and you learned some new commands. If you have any further questions, 
don’t hesitate to reach out. Feel free to share any Git commands you tend to use in your daily routine and find super handy. :)

Let’s connect:
LinkedIn
Twitter

