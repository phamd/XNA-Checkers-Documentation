Git Tutorial
=============

## What is Git?
 * Git is a distributed revision control and source code management system
 * Unlike other systems like SVN, Git is fundamentally just a peer repository that is synced by an authoritative repository.

#### Step 0 of using Git:
 * We need a git shell, and the easiest way to get one is by installing the GitHub client. (Most of us should already have it!)
 * Download the [GitHub Client](http://windows.github.com/)
 * Open Git Shell (from the shortcut on your desktop)

#### One time setup
 * So git uses a name and an email for tagging your contributions.
 * Note: Name and email can both be fake and you can change them as often as you like.

```
git config --global user.name "your name"
git config --global user.email "your@email"
```

 * Make a directory to hold projects, then enter that directory and clone the project

```
mkdir .\2me3\
cd .\2me3\
git clone http://git.hacked.jp/2me3/checkers.git
cd .\checkers\
```

#### Finding where the git is
 * If you freshly launch Git Shell from now on, you just need to type
    `cd .\2me3\checkers` to find your work
 * You should see the left part of your command-line say something like  `C:\Users\xxx\Documents\GitHub\2me3\checkers`
 * Note: When typng paths, such as `cd 2m...`, you can press tab to auto-complete

#### Adding new files
 * You can just drop files into `My Documents\GitHub\2me3\checkers`
 * Then allow git to see those files with the command `git add *` where you can replace `*` with a filename or leave it as `*` to add all files 

#### Changing existing files
 * Before making changes, make sure you have the latest copy by doing a `git pull`
 * Note: If `git pull` gives you errors, try doing `git pull -u origin master`
 * Modify whatever you want using whatever then when you're done, you commit it.
 * `git commit -m "Write a description of the changes here"`
 * Doing a commit, only queues up a change, so it's literally like creating a breakpoint.

#### Syncing changes to the server
 * Before syncing, check what you've changed with `git status`
 * Once you're done making changes or adding new files, you need to sync these changes with `git push`

#### Looking at recent changes
 * Let's say your code isn't working quite right anymore and you want to see which mthfkr broke it.
 * Type `git log` or `git log --oneline`
 * Read more about [undoing changes](https://www.atlassian.com/git/tutorial/undoing-changes)
 * To compare a local copy of a file with the remote, type `git diff -- myfile.txt`

#### Non-important Final Notes
 * In the real world, instead of pushing commits right to the master branch, you would fork the project into a "feature" branch and do your work, then initate a merge/pull request to the master. This is called the __Fork & Pull Model__.
 * We won't be using that, instead we're just going to all work on the same master branch in a __Shared Repository Model__
 * Further reading: [1](http://scottchacon.com/2011/08/31/github-flow.html), [2](https://help.github.com/articles/using-pull-requests#a-quick-note-on-collaborative-development-models)