# **Git Objects**

Git has it's own file system which stores `objects` in the `obects directory`. There are several types of objects that Git can store. 

There are four main object types `Git` stores in order to store all necessary data required for file tracking and for tracking changes of files. They are:
  * Blob ~ Stores files with any extension which can be pictures, videos, text, etc.
  * Tree ~ Stores directories which can be empty or contain blobs and or other trees/directories
  * Commit ~ Allows us to store different versions of our project
  * Annotated Tag ~ Persistent text pointer to specific commit