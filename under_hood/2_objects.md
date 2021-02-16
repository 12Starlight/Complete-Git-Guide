# **Git Objects**

Git has it's own file system which stores `objects` in the `obects directory`. There are several types of objects that Git can store. 

There are four main object types `Git` stores in order to store all necessary data required for file tracking and for tracking changes of files. They are:
  * Blob ~ Stores files with any extension which can be pictures, videos, text, etc.
  * Tree ~ Stores directories which can be empty or contain blobs and or other trees/directories
  * Commit ~ Allows us to store different versions of our project
  * Annotated Tag ~ Persistent text pointer to specific commit

&nbsp;

For management of `blobs` and `trees` use low level git commands:
  * <kbd>git hash-object</kbd> ~ `Creates` new object in Git structure
  * <kbd>git cat-file</kbd> ~ `Reads` Git objects

 &nbsp;
 
## **Creating Trees and Blobs**

To create a `Blob` use <kbd>git hash-object</kbd>

To read a `Blob` use <kbd>git cat-file</kbd>

To create a `Tree` use <kbd>git mktree</kbd>

When Git creates an object and stores it in it's file system, Git turns it into a Hash. That hash is then stored inside a folder it also creates.

![alt txt](./assets/creating.png "Creating Blob")

&nbsp;

![alt txt](./assets/inside_b7.png)

&nbsp;

<kbd>echo [`"Hello, Git"`]</kbd> ~ Echos the input to Standard Output

<kbd>`|`</kbd> ~ Redirects the Standard Output to the next command

<kbd>--stdin</kbd> ~ This options allows <kbd>git hash-object</kbd> to take it's input from Standard Input

<kbd>-w</kbd> ~ Writes the file

&nbsp;

The `Folder name` + `File name` equals the Hash.

&nbsp;

**`Note`**:

The new file or `Blob` was created ONLY in the Git repository, in the ".git/objects" folder.

Our project folder "Git" is still empty, if this was all that we created (not counting hidden system .DS_Store file and .git folder)