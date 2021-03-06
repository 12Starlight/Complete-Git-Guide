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
  * <kbd>git cat-file <`folder_name`><`file_name`></kbd> ~ `Reads` Git objects

 &nbsp;
 
## **Creating Trees and Blobs**

To create a `Blob` use <kbd>git hash-object</kbd>

To read a `Blob` use <kbd>git cat-file</kbd>

&nbsp; &nbsp; Options:
  * <kbd>-p</kbd> ~ Prints contents of object
  * <kbd>-s</kbd> ~ Prints size of object
  * <kbd>-t</kbd> ~ Prints type of object

To create a `Tree` use <kbd>git mktree</kbd>

When Git creates an object and stores it in it's file system, Git turns it into a Hash. That hash is then stored inside a folder it also creates.

&nbsp;

![alt txt](./assets/creating.png "Creating Blob")

&nbsp;

![alt txt](./assets/inside_b7.png)

&nbsp;

<kbd>echo [`"Hello, Git"`]</kbd> ~ Echos the input to Standard Output

<kbd>`|`</kbd> ~ Redirects the Standard Output to the next command

<kbd>--stdin</kbd> ~ This options allows <kbd>git hash-object</kbd> to take it's input from Standard Input

<kbd>-w</kbd> ~ Writes the file

&nbsp;

Git creates files and folders based on the hash which is created from the input using the `SHA1 Hash` function. The first two characters of the hash make up the folder name, while the rest of the hash equals the file name. The `Folder name` + `File name` equals the Hash.

&nbsp;

**`Note`**:

The new file or `Blob` was created ONLY in the Git repository, in the ".git/objects" folder.

Our project folder "Git" is still empty, if this was all that we created (not counting the hidden system .DS_Store file and .git folder).

&nbsp;

## **JSON vs. Git Dababase**

&nbsp;

![alt txt](./assets/json.png "JSON Object")

&nbsp;

Similar to `JSON Objects` which store key value pairs, `Git` does the same thing. The keys are the hash which was generated by the value. The value is the actual data. So, the database is actually a set of key value pairs.

&nbsp;

**`Note`**:

The `Git` repository stores files independently in it's own "file system" in the "objects" directory. These files are separate and independent from the files stored on your computer. 

&nbsp;

## **Using Filenames**

In the previous example, we used the following command then used piping to redirect and use the command to create our blob  
  * `echo 'Hello, Git' | git hash-object --stdin -w`

Something to take notice of is that a filename was not required. The reason for this is that the file name is actually based on the `SHA1` hash of the object being stored. The object was created based on the contents of the file. However, if you did want to create an object using a file name, simply use the same command followed by the file name and the <kbd>-w</kbd> write to disk option. 
  * `git hash-object <filename> -w`

Although we are using the filename, it still would not be stored as the value for the key value pair for that object. Instead the `SHA1` hash would be stored which was created based on the contents of that file 😉 &nbsp; In addition, the size and type would be stored inside the blob as well. This causes the contents of the file to be altered and the `SHA1` hash to be changed from had these not been included. 

&nbsp;

## **Contents of Git Object Blob**

&nbsp;

![alt txt](./assets/object_blob.png "Content of Git Object")

&nbsp;

To prove this, recall that when creating our blob using git hash-object we got 

&nbsp;

![alt txt](./assets/creating.png "Creating blob")

&nbsp;

If we type <kbd> echo 'blob 11\0Hello, Git' | shasum </kbd>, we get the same hash!

&nbsp;

![alt txt](./assets/example.png "Recreating SHA1 Hash")

&nbsp;

## **Closer Look at Tree Objects**

&nbsp;

![alt txt](./assets/tree.png "Git Tree Objects")

&nbsp;

Git **`Trees`** contain:
  * Permissions
  * Type
  * Hash
  * File Name

&nbsp;

#### **`Permissions`**:

&nbsp;

| Id | Permission |
|:- |:- |
| **040000** | Directory |  
| **100644** | Regular non-executable file |
| 100664 | Regular non-executable group-writeable file |
| 100755 | Regular executable file |
| 120000 | Symbolic link |
| 160000 | Gitlink |

&nbsp;

#### **`Current Tree Example`**:

&nbsp;

![alt txt](./assets/git_tree.png "Current Tree Example")

&nbsp;

Now we want to create a git tree and two pointers to our blobs. To find the files you want to store in the tree, navigate to the directory your `.git` folder is stored and type <kbd>find .git/objects -type f</kbd>. Our tree object is going to have file permissions that are **100644** with type **blob** and names as **file1.txt** and **file2.txt**. 
  * **`Note`**: Type <kbd>find .git/objects/{44,b7} -type f</kbd> to get the specific blobs mentioned, due to our git object directory having more files than the above example
  
&nbsp;
  
To Create Tree Object:
  * <kbd>nano ~/Desktop/temp-tree.txt</kbd>, then list:
    * 100644 blob b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e	file1.txt
    * 100644 blob 4400aae52a27341314f423095846b1f215a7cf08	file2.txt  
  
  * Type: <kbd> cat ~/Desktop/temp-tree.txt  </kbd> `|` <kbd> git mktree </kbd> ~ To create a tree
    * <kbd>--help</kbd> ~ Option help: To see `Git Manual` for <kbd>git mktree</kbd>

&nbsp;

You should see a `SHA1` hash of tree object!

&nbsp;

![alt txt](./assets/mktree.png "Mktree Example")

&nbsp;

To read information about this specific object:
  * Type <kbd>git cat-file -p <3b95df0ac6365c72e9b0ff6c449645c87e6e1159></kbd>
  * You can type the first **four** characters of hash to get same result

&nbsp;

![alt txt](./assets/reading.png "Reading Tree")

&nbsp;

## **Staging Area**

&nbsp;

![alt txt](./assets/staging_area.png "Diagram of Staging")

&nbsp;

So far everything has been about how to work with files directly in the `Git Repository` by hashing objects. However, in order for files to go from a `Working Directory` to be written into the `Git Repository` or reading them from the `Git Repository`, there first needs to be a `Staging Area` that prepares the files. This area is often called the **index** area and it is a manditory step.

&nbsp;

In our `Git Repository` of our above example tree, we do see our hidden `.git` directory. However, the `Working Directory` is currently empty. Now let us look at the staging area.
  * <kbd>git ls-files -s</kbd> ~ List all files currently in the staging area or **index**

&nbsp;

In our above example the `Staging Area` is empty, the `Working Directory` is empty, and `Git Repository` has two files. So our project looks like this:

&nbsp;

![alt txt](./assets/project.png "Project Example")

&nbsp;

Now bc we created the tree which is the root tree which points to two blobs, we want to put the two blobs into the `Staging Area`. 
  * Root trees do not get added
  * <kbd>git read-tree `<hash>`</kbd>

&nbsp;

![alt txt](./assets/read_example.png "Read Tree Example")

&nbsp;

![alt txt](./assets/read_tree.png "Staging Area Example")

&nbsp;

At the moment we have `file1.txt` and `file2.txt` in the `Staging Area` using the <kbd>git read-tree</kbd> command which put them from the `Git Repository` into the `Staging Area`. Now it is time to put these file into the `Working Directory` which is currently empty. 
  * <kbd>git checkout-index -a</kbd> ~ Puts all files from `Staging Area` into `Working Directory`
  * Currently all files in the `Git Repository` are the same as those in the `Staging Area` which is annotated by the `0` next to the hash

&nbsp;

![alt txt](./assets/files.png "Files Added To Working Directory")

&nbsp;

![alt txt](./assets/working_directory.png "Files Added To Working Directory Diagram")

&nbsp;

Finally, we have completed the entire process of retrieving the files from the `Git Repository` and putting them into the `Working Directory`. 

**`Note`**: We have manualy inserted files into the `Git Repository`. Then retrieved them to put into the `Staging Area`. After, we took the files and read them from the `Staging Area`, and put them into the `Working Directory`.