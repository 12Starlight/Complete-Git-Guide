# **Git Operations**

## **Git Commits**

Commits have same structure as Object Blob and Tree in that it has:
  * Content
  * Object Type
  * Object Length

&nbsp;

The content of a `commit` have the following inside:
  * It own SHA1 hash
  * Author name and email
  * Commit description
  * Parent (optional)

&nbsp;

Commits allow us to store different versions (snapshots) of our project in the 
database. This gives us the ability to move to any version of the project by 
checking out the specific commit. This is done using a `pointer` to s specific 
Tree object in the `Git database`. 

The commit is just a "wrapper" for the Tree object. You can have multiple 
commits/pointers and multiple trees. Then you can "check out" these commits and
take files out of the `Git Repository` and put them into the `Working Directory`.

Previously, we used low level commands <kbd>git read-tree `<hash>`</kbd> and 
<kbd>git checkout index</kbd> to accomplish the same thing. This put files in
the root directory. However, with <kbd>git commit -m `<"Something here">`</kbd>
this can be accomplished with just one step. 

&nbsp;

![alt txt](./assets/commit_pointer.png "Commit Pointer")

&nbsp;

**`Note`**: Git `commit` is an object, every object must have a `SHA1` hash

&nbsp;

## **Configuring Author Name and Email**

`Git` is a distributed version controll system which allows many people to be
be working on a project. Before using `commit`, <kbd>author_name</kbd> and 
<kbd>email</kbd> need to be configured. This is done using the following 
commands. 
  * <kbd>git config --global user.name <`Name`></kbd> ~ Sets name globaly
  * <kbd>git config --global user.email <`Email`></kbd> ~ Sets email globaly
  * <kbd>git config --list</kbd> ~ Lists authors that worked on portion

&nbsp;

