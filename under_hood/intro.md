# **Introduction to Git and GitHub**

<kbd>echo "# Complete-Git-Guilde" >> README.md</kbd> ~ Creates README using Unix Command Line

<kbd>git init</kbd> ~ Creates repository

<kbd>git add</kbd> README.md ~ Adds file to repository

<kbd>git commit -m "[first commit]"</kbd> ~ Creates commit

<kbd>git branch -M main</kbd> ~ Renames master branch to main

<kbd>git remote add origin [`git@github.com`:12Starlight/Complete-Git-Guilde.git]</kbd> ~ Adds a new remote url in the directory the respository is stored at

<kbd>git push -u origin main</kbd> ~ Add upstream tracking reference and push to origin (default) remote repository

&nbsp;

**`Note`**:

Just like the branch name "master" does not have any special meaning in Git, neither does "origin". While "master" is the default name for a starting branch when you run <kbd>git init</kbd> which is the only reason it is widely used, "origin" is the default name for a remote when you run <kbd>git clone</kbd>. If you run <kbd>git clone -o booyah</kbd> instead, then you will have `booyah/master` as your default remote branch.