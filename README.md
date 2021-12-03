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

