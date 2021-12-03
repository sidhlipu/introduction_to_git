# Introduction to Version Control System

Version control is a system that records
changes to a file or set of files over time so that you can recall specific versions later.

For example if you are a graphic or web designer and want to keep every version of an image or layout (which
you would most certainly want to), a Version Control System (VCS) is a very wise thing to use. It
allows you to revert selected files back to a previous state, revert the entire project back to a
previous state, compare changes over time, see who last modified something that might be causing
a problem, who introduced an issue and when, and more. Using a VCS also generally means that if
you screw things up or lose files, you can easily recover. In addition, you get all this for very little
overhead.

# Local Version Control Systems

Many people’s version-control method of choice is to copy files into another directory (perhaps a
time-stamped directory, if they’re clever). This approach is very common because it is so simple, but
it is also incredibly error prone. It is easy to forget which directory you’re in and accidentally write
to the wrong file or copy over files you don’t mean to.


# Centralized Version Control Systems

The next major issue that people encounter is that they need to collaborate with developers on
other systems. To deal with this problem, Centralized Version Control Systems (CVCSs) were
developed. These systems (such as CVS, Subversion, and Perforce) have a single server that contains
all the versioned files, and a number of clients that check out files from that central place. For
many years, this has been the standard for version control.

The next major issue that people encounter is that they need to collaborate with developers on
other systems. To deal with this problem, Centralized Version Control Systems (CVCSs) were
developed. These systems (such as CVS, Subversion, and Perforce) have a single server that contains
all the versioned files, and a number of clients that check out files from that central place. For
many years, this has been the standard for version control.

The next major issue that people encounter is that they need to collaborate with developers on
other systems. To deal with this problem, Centralized Version Control Systems (CVCSs) were
developed. These systems (such as CVS, Subversion, and Perforce) have a single server that contains
all the versioned files, and a number of clients that check out files from that central place. For
many years, this has been the standard for version control.


<img width="710" alt="Screenshot 2021-12-03 at 5 34 57 PM" src="https://user-images.githubusercontent.com/20242622/144599810-6dea81a1-061a-4d2e-83fe-f76c8c17bd3d.png">


This setup offers many advantages, especially over local VCSs. For example, everyone knows to a
certain degree what everyone else on the project is doing. Administrators have fine-grained control
over who can do what, and it’s far easier to administer a CVCS than it is to deal with local databases
on every client.

However, this setup also has some serious downsides. The most obvious is the single point of failure
that the centralized server represents

# Distributed Version Control Systems

This is where Distributed Version Control Systems (DVCSs) step in. In a DVCS (such as Git, Mercurial,
Bazaar or Darcs), clients don’t just check out the latest snapshot of the files; rather, they fully
mirror the repository, including its full history. Thus, if any server dies, and these systems were
collaborating via that server, any of the client repositories can be copied back up to the server to
restore it. Every clone is really a full backup of all the data.

<img width="587" alt="Screenshot 2021-12-03 at 5 38 35 PM" src="https://user-images.githubusercontent.com/20242622/144600173-ac95f5f2-4751-4486-b2a1-f94634fa4d63.png">


# What is Git?

## Snapshots, Not Differences
> The major difference between Git and any other VCS (Subversion and friends included) is the way
Git thinks about its data. Conceptually, most other systems store information as a list of file-based
changes.
> These other systems (CVS, Subversion, Perforce, Bazaar, and so on) think of the
information they store as a set of files and the changes made to each file over time (this is
commonly described as delta-based version control).

<img width="782" alt="Screenshot 2021-12-03 at 5 50 14 PM" src="https://user-images.githubusercontent.com/20242622/144601614-4014855f-0663-40c1-ae35-ff8f98d2220f.png">


> Git doesn’t think of or store its data this way. Instead, Git thinks of its data more like a series of
snapshots of a miniature filesystem. 
> With Git, every time you commit, or save the state of your
project, Git basically takes a picture of what all your files look like at that moment and stores a
reference to that snapshot. 
> To be efficient, if files have not changed, Git doesn’t store the file again,
just a link to the previous identical file it has already stored. Git thinks about its data more like a
stream of snapshots.

<img width="782" alt="Screenshot 2021-12-03 at 5 51 57 PM" src="https://user-images.githubusercontent.com/20242622/144601814-7e572f2f-e851-4f8c-a2af-167880dfef23.png">


> This is an important distinction between Git and nearly all other VCSs. It makes Git reconsider
almost every aspect of version control that most other systems copied from the previous
generation. This makes Git more like a mini filesystem with some incredibly powerful tools built on
top of it, rather than simply a VCS.

#### Nearly Every Operation Is Local
> Most operations in Git need only local files and resources to operate — generally no information is
needed from another computer on your network.
#### Git Has Integrity
Everything in Git is checksummed before it is stored and is then referred to by that checksum. This
means it’s impossible to change the contents of any file or directory without Git knowing about it. 

**The mechanism that Git uses for this checksumming is called a SHA-1 hash. This is a 40-character
string composed of hexadecimal characters (0–9 and a–f) and calculated based on the contents of a
file or directory structure in Git.A SHA-1 hash looks something like this:**

<img width="754" alt="Screenshot 2021-12-03 at 5 57 55 PM" src="https://user-images.githubusercontent.com/20242622/144602549-438b0b10-619a-44a6-84a5-4dd73153383c.png">

#### Git Generally Only Adds Data
> When you do actions in Git, nearly all of them only add data to the Git database. It is hard to get the
system to do anything that is not undoable or to make it erase data in any way. As with any VCS, you
can lose or mess up changes you haven’t committed yet, but after you commit a snapshot into Git, it
is very difficult to lose, especially if you regularly push your database to another repository.

> This makes using Git a joy because we know we can experiment without the danger of severely
screwing things up.


#### The Three States
**Git has three main states that your files can reside in: _modified_,
_staged_, and _committed_:**

> Modified means that you have changed the file but have not committed it to your database yet.

> Staged means that you have marked a modified file in its current version to go into your next
commit snapshot.

> Committed means that the data is safely stored in your local database.

<img width="745" alt="Screenshot 2021-12-03 at 6 04 17 PM" src="https://user-images.githubusercontent.com/20242622/144603412-7444dbeb-3acc-4d51-a112-62ce947dcde4.png">


The working tree is a single checkout of one version of the project. 

> These files are pulled out of the
compressed database in the Git directory and placed on disk for you to use or modify.

> The staging area is a file, generally contained in your Git directory, that stores information about
what will go into your next commit. Its technical name in Git parlance is the **“index”**, but the phrase
“staging area” works just as well.

> The Git directory is where Git stores the metadata and object database for your project. This is the
most important part of Git, and it is what is copied when you clone a repository from another
computer.


#### The basic Git workflow goes something like this:

**1. You modify files in your working tree.**<br /><br />
**2. You selectively stage just those changes you want to be part of your next commit, which adds
only those changes to the staging area.**<br /><br />
**3. You do a commit, which takes the files as they are in the staging area and stores that snapshot
permanently to your Git directory.**<br /><br />


## Installing on Linux

If you’re on Fedora (or
any closely-related RPM-based distribution, such as RHEL or CentOS), you can use dnf:

#### Debian/Ubuntu
**For the latest stable version for your release of Debian/Ubuntu**
> \# apt-get install git

#### Fedora
> \# yum install git (up to Fedora 21)*<br />
> \# dnf install git (Fedora 22 and later)

_For more platforms_ https://git-scm.com/download/linux

#### Windows 
For windows, click on this link https://git-scm.com/download/win and a executable file will be downloaded. Follow the on-screen steps to install it. 



# First-Time Git Setup

> **git config**<br />

This lets you get and set configuration variables that control
all aspects of how Git looks and operates.

Generally this is stored in **~/.gitconfig** but there are other places like **[path]/etc/gitconfig** or **config**

_On Windows systems, Git looks for the .gitconfig file in the $HOME directory (C:\Users\$USER for
most people)._

**You can view all of your settings and where they are coming from using:**
> **$ git config --list --show-origin**

<br />
<br />


**Let set our Identity**
> **$ git config --global user.name "Sidharth Mohapatra"**<br />
> **$ git config --global user.email "sidharth.mohapatra@devopskill.com"**

_If you want to set this permanent for all your future git repositories, you can pass **--global** option along with the above commands._ <br />
_If you want to override this with a
different name or email address for specific projects, you can run the command without the
**--global** option when you’re in that project._

<br />
<br />



**Lets set our Editor**<br />
For Linux based systems use:
> **$ git config --global core.editor vi**

_On a Windows system, if you want to use a different text editor, you must specify the full path to its
executable file. This can be different depending on how your editor is packaged._

<br />
<br />

> **$ git config --global core.editor \"'C:/Program Files/Notepad++/notepad++.exe'
-multiInst -notabbar -nosession -noPlugin\"**
<br />
<br />
<br />
**Your default branch name**
Branching we shall cover a little later but by default Git will create a branch called master when you create a new repository with **git init**.<br />
From Git version 2.28 onwards, you can set a different name for the initial branch.

> **git config --global init.defaultBranch main**

<br />
<br />


**Checking Your Settings**
> **$ git config --list** <br />
> credential.helper=osxkeychain <br />
user.name=Sidharth Mohapatra <br />
user.email=sidharth.mohapatra@devopskill.com <br />
core.editor=vi <br />
init.defaultbranch=main <br />

**You can also check what Git thinks a specific key’s value is by typing git config <key>:**
> **$git config user.name** <br />
Sidharth Mohapatra
  
<br />
  <br />
  
**Getting Help**
 
>**$ git help <verb>**<br />
**$ git <verb> --help**<br />
**$ man git-<verb>**<br />
  
  
# Getting a Git Repository
You typically obtain a Git repository in one of two ways:<br />
1. You can take a local directory that is currently not under version control, and turn it into a Git
repository, or <br />
2. You can clone an existing Git repository from elsewhere. <br />
  
## Initializing a Repository in an Existing Directory
> **$ mkdir /home/\<user name\>/git_practice**<br />
> **$ git init**<br />
_This creates a new subdirectory named .git that contains all of your necessary repository files — a
Git repository skeleton. At this point, nothing in your project is tracked yet._
  
# Cloning an Existing Repository
> **$ git clone https://github.com/libgit2/libgit2** <br />
  
  _That creates a directory named libgit2, initializes a .git directory inside it, pulls down all the data
for that repository, and checks out a working copy of the latest version. If you go into the new
libgit2 directory that was just created, you’ll see the project files in there, ready to be worked on or
used._<br />
  

_If you want to clone the repository into a directory named something other than libgit2, you can
specify the new directory name as an additional argument:_  
> **$ git clone https://github.com/libgit2/libgit2 mylibgit**
  
  
# Recording Changes to the Repository
Each file in your working directory can be in one of two states: <br />**tracked** or<br />
**untracked.** <br /><br />
  **Tracked files** are files that were in the last snapshot, as well as any newly staged files;
they can be unmodified, modified, or staged. <br />In short, tracked files are files that Git knows about.<br /><br />
**Untracked files** are everything else — any files in your working directory that were not in your last
snapshot and are not in your staging area. As you edit files, Git sees them as modified, because you’ve changed them since your last commit.<br />
As you work, you selectively stage these modified files and then commit all those staged changes,
and the cycle repeats.<br /><br />
