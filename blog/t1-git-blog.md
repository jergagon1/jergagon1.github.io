A Crash Course from a Crash Course Newbie

Version Control, Git and GitHub

November 22, 2014

Welcome to my blog! I'm writing on the verge of completing my first week of Phase 0 at Devbootcamp. It's been awesome and I am excited to share some of the great things I've learned.

This week focused on version control, Git and Github. These sound great, right? Except...you might not know what any of these are! Don't worry, you will in a few paragraphs - that's where the crash course comes in.

Version control is simply a mechanism to track and record changes to files over time. As you work on code (or any other type of document), you have to make constant decisions about how to proceed: should I turn left or right? Should I use an array or a hash? Version control systems record the state of your files at key points so you can revert to those points if things go wrong.

Using a version control system (VCS) also provides you with a level of backup for your project. Generally, you can recover lost or deleted files.

The odds are pretty good that on a large development project, you won't be writing every line of code by yourself. Version control systems allow developers to collaborate on big projects by keeping track of who is working on what or if two people are working on different parts of the same thing.

VCSs allow developers to experiment with ideas while not destroying the main repository of project code. The developer can save out a version (branch) of the source files (the tree) to try things out. If they work, the version control system can merge them back into the tree.  If not, no harm, no foul. You simply abandon the branch.

Okay, so what's Git?

Git is a popular free version control system developed originally by Linus Torvalds of Linux fame.

Git is a distributed version control system which means that you download and run the software locally on your computer. Each collaborator has a full copy of all of the files and file history, so if one computer or server crashes, nothing is lost. Essentially, everyone has the master set of files. Awesome, right?

Git tracks folders and detects when you make changes in them. If you add a file or change a comma in a document, Git knows. It will tell you if you type "git status" in your command line.

There's a temporary staging area where you can hold files before you save them to Git. You can group a set of similar files together by adding them to the staging area with the command "git add my_awesome_file.rb" or better yet "git add ." to add all the files at once.

Now that you have all of your files in the staging area, it's time to save them out. You do this with a "commit". A commit does a couple of things: it saves out a snapshot of the current state of the files, it allows you to add a message to describe what changed and it lets your collaborators know that you've saved stuff out and that they should get the latest files.

What's GitHub?

What if there was a place on the internet where you could put your awesome Git folder and all of your collaborators could upload and download changes whenever they were online? What if there was a place where you could post your code and brilliant people would help you fix bugs, suggest improvements and even write code for you? GitHub is that place.

GitHub allows developers to post code in open repositories that other developers can view, tweak and use in their own projects. It's a collaborative hub for developers to share their expertise.

For a fee, individuals or organizations can have private repositories, but the free accounts are open to everyone.

Varying types of open source licenses can be included with your project repository on GitHub to offer some control over redistribution and use of your code, but generally open source licenses favor less restriction and encourage code reuse.

On to week 2!!!