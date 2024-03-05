# Subversion (SVN) Makefiles
### Contact 2 | March 1, 2024
---
### Revision Controls 

##### Version Control Systems (VCS):
- Store development history of a project
  - As a series of *commits/revisions*
- Allow retrieval of previously committed states
- Report differences between revisions
- multiple parallel lines of development (branches) / merging
  - Beyond course scope
- Subversion is one VCS among many, but it is the only suported one in this course.

---
### SVN Pieces

Repository 
  - Where history is stored
  - Only manipulate via svn commands
  - Located via a URL
  - In this course you each have a repo at [svn] (https://source.eait.uq.edu.au/svn/csse2310-sem1-s???????)
    
    - Don’t point your browser at this URL – this is for SVN clients to use 
  - You can browse it via
    - [svn] (https://source.eait.uq.edu.au/viewvc/csse2310-sem1-s???????)
  - Working copy/copies
    - Where you do your editing / compiling / testing
    - Record “good” states back to the repo with commits
    - Nothing you modify in your working copy affects the repo unless you commit.
    - You can delete your working copy and it will not affect the repo (will lose any uncommitted changes though)
    - There could be multiple working copies checked out

---

### SVN Commands


###### Make a working copy from the repository
> ==svn checkout URL [working_dir]==
 
> e.g. *svn checkout https://source.eait.uq.edu.au/svn/csse2310-sem1-s???????/play 2310play*

  
^ Make a directory called 2310play with a working copy of the play directory in the repo

<br>

###### Tells svn to track changes to this file
> ==svn add *filename*==

> e.g. svn add 2310play.c

Doesn’t take effect until you commit

<br>


###### Rename or move file
> ==svn mv *oldname newname*==

> *e.g. svn mv 2310play.c 2310plays.c*
> *e.g. svn mv 2310play.c ../otherdir/2310play.c*

Need to commit to make the change in repo

<br>

###### Remove file locally and remove it from future repo revisions
> ==svn rm *fname*==

> *e.g. svn rm 2310play.c* 

Can not remove it from past versions

<br>

###### Shows which files have pending changes
> ==svn status==

> M — modified
> A - untracked file to be added
> D -  file to be removed
> ? - Don’t know anything about this file

<br>

###### Show the lines which have changed
> ==svn diff==

<br>

###### Send pending changes from working copy to the repo
> ==svn commit -m "message"==
>  - Can commit only specified files with:
> *svn commit f1 f2 f3*

<br>

###### Show the log messages for filename
> ==svn log *filename*==

<br>

###### Undo any pending changes to *filename*
> ==svn revert *filename*==

Can’t be reversed.

<br>

###### Bring working copy up to date with the latest version in the repo
> ==svn update==

- Generally only needed if you’ve been using multiple working directories.
  - So,only necessary if collaborative work mainly
- Can lead to conflicts

<br>

#### *Putting it back*

###### To put a file back the way it was a few versions ago:

> ==svn update -r *revision* *filename*==

###### Make a copy of that version of the file
> ==cp *filename* backup==

> ==svn update filename==

###### Copy the older version over
> ==cp backup *filename*==
> ==svn commit *filename*==