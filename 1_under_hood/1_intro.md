# **Introduction to Git and GitHub**

<kbd>mkdir [git_directory]</kbd> ~ Create directory to store git

<kbd>cd [git_directory]</kbd> ~ Navigate to inside git_directory

<kbd>echo "# Complete-Git-Guilde" >> README.md</kbd> ~ Creates README using Unix Command Line

<kbd>git init</kbd> ~ Creates and sets property to a new empty repository
  * Creates and initializes a new `.git` hidden folder which you can add files too

<kbd>git add</kbd> README.md ~ Adds README to repository

<kbd>git commit -m `"<first commit>"`</kbd> ~ Creates commit

<kbd>git branch -M main</kbd> ~ Renames master branch to main

<kbd>git remote add origin</kbd> `<git@github.com:12Starlight/Complete-Git-Guilde.git>` ~ Adds a new remote url in the directory the respository is stored at

<kbd>git push -u origin main</kbd> ~ Add upstream tracking reference and push to origin (default) remote repository

&nbsp;

**`Note`**:

Just like the branch name "master" does not have any special meaning in Git, neither does "origin". While "master" is the default name for a starting branch when you run <kbd>git init</kbd> which is the only reason it is widely used, "origin" is the default name for a remote when you run <kbd>git clone</kbd>. If you run <kbd>git clone -o booyah</kbd> instead, then you will have `booyah/master` as your default remote branch.

&nbsp;

## **Exploring the `.git` Hidden Folder**

In the git directory, type <kbd>open .</kbd>, which open the directory the `.git` hidden folder is located using the GUI. 

Then type <kbd>cmd + shft .</kbd> in order to view hidden folders and or files. Using the command line, after navigating to inside the directory holding the hidden `.git` folder, type <kbd>ls -a</kbd> to see the same hidden folders and files.

Now type <kbd>cd .git</kbd> to navigate inside the `.git` hidden folder. There you will see the following:
  * COMMIT_EDITMSG ~ File
  * HEAD ~ File
    * ref: refs/heads/main (explained more later)
  * config ~ File
    * Configuration of your git repository where you will see some default settings
  * description ~ File
    * Description of your git repository
  * hooks ~ Directory
  * index ~ File
  * info ~ Directory
  * logs ~ Directory
  * objects ~ Directory
  * refs ~ Directory 

&nbsp;

To read any of the files type <kbd>cat `<file_name>`</kbd>. For larger files you can pipe <kbd>| less</kbd> into the less command for a more readable format. Then type <kbd>:q</kbd> to exit. 