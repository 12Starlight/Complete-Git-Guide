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
commands. `Git` will take this information and attach it to every commit. 
  * <kbd>git config --global user.name <`Name`></kbd> ~ Sets name globaly
  * <kbd>git config --global user.email <`Email`></kbd> ~ Sets email globaly
  * <kbd>git config --list</kbd> ~ Lists authors that worked on portion by reading the configuration of the `Git`

&nbsp;

**`Note`**: If you are using GitHub for hosting your repositories, it is 
*recommended* (but *not required*) to set in your local Git config name and
email same as used at GitHub account.

&nbsp;

## **Creating Commit**

If you want to create a new commit, you must have some changes. Those changes
must be placed into the `Staging Area`. 
  * <kbd>git ls-files -s</kbd> ~ Shows what is in index
  * <kbd>git commit</kbd> ~ Commit changes to working directory
    * <kbd>-m <"something to commit"></kbd> ~ Option allows you attach description for commit  

&nbsp;

**`Note`**: The x, will now disappear after you commit the changes. 

&nbsp;

![alt txt](./assets/x.png "Changes need to be commited")

&nbsp;

## **Commit Structure**

&nbsp;

![alt txt](./assets/commit_structure.png "Commit Structure")