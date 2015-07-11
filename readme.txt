d on remote-tracking branches

If you want to create a local branch based on a remote-tracking branch (i.e. in order to actually work on it) you can do that with git branch –track or git checkout –track -b, which is similar but it also switches your working tree to the newly created local branch. For example, if you see in git branch -r that there’s a remote-tracking branch called origin/refactored that you want, you would use the command:
GITHUB LINE: v1
    git checkout --track -b refactored origin/refactored
In this example “refactored” is the name of the new branch and “origin/refactored” is the name of existing remote-tracking branch to base it on. (In recent versions of git the “–track” option is actually unnecessary since it’s implied when the final parameter is a remote-tracking branch, as in this example.)

The “–track” option sets up some configuration variables that associate the local branch with the remote-tracking branch. These are useful chiefly for two things:
LOCAL LINE: v2
They allow git pull to know what to merge after fetching new remote-tracking branches.
If you do git checkout to a local branch which has been set up in this way, it will give you a helpful message such as:
    Your branch and the tracked remote branch 'origin/master'
    have diverged, and respectively have 3 and 384 different
    commit(s) each.
… or:

    Your branch is behind the tracked remote branch
    'origin/master' by 3 commits, and can be fast-forwarded.
The configuration variables that allow this are called “branch.<local-branch-name>.merge” and “branch.<local-branch-name>.remote”, but you probably don’t need to worry about them.

You have probably noticed that after cloning from an established remote repository git branch -r lists many remote-tracking branches, but you only have one local branch. In that case, a variation of the command above is what you need to set up local branches that track those remote-tracking branches.

You might care to note some confusing terminology here: the word “track” in “–track” means tracking of a remote-tracking branch by a local branch, whereas in “remote-tracking branch” it means the tracking of a branch in a remote repository by the remote-tracking branch. Somewhat confusing…

Now, let’s look at an example of how to update from a remote repository, and then how to push changes to a new repository.
