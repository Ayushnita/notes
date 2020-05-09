# __GIT Tutorail 1__  

We are going to begin a Git tutorial series where we can initiate learning about how you can use git to improve your productivity. While, in this notes section, we only focus on commands and some special features so that while practicing we will not miss anything.  

If you are referring to this document then you will able to learn which command is suitable for your work and how you can improve your productivity.  

In this tutorial, We learn only five basic git commands, which we will cover 70% of git. yes, only 5 commands. Additional commands are useful for solving complex situations, but first understand git vocabulary.  

* _Repository_ --> your whole project is known as a Repository. Which is hosted on any git supported server like GitHub, Atlassian, GitLab, etc. 
* _Branch_ --> In git branches are like tree branches, they start from one point and then progress moving in separate 	 direction than the mainstream and if, at one point, we need to merge into the mainstream later you can.  
* _HEAD_ --> This is a position where you are currently working, this is like a pointer which moves with your changes.  
* _Origin_ --> this is a thread(URL) which join your hosted repository to your local repository.

All the above mention terms, we discussed in detail once we came on that point.

## Git Commands  

### __1. git clone__   

The first basic command is _git clone_ this command is used to clone any of your repositories from your hosted location to your local system where you do development.


@@@Git
	git clone http://github.com/<username>/<reponame>.git [directory]


Directory is optional if you did not provide any then, it creates a new directory with repository name and copy code in that.

#TODO: Demo for clone

### 2. git add  

Once we clone repo we start developing code and we make some changes and after that, we have to tell git that those file changes will be considered by when I commit. You can omit some changes by not mention them in add command.

@@@Git
	git add <file name >/<foldername>

EG: if you provide __.__ means inside current folder all change.  

#TODO: Demo for add 


### 3. git commit  

Now you are sure those changes are fine and we are looking ahead to make it persist then we use git commit command to make a snapshot and add it in the mainstream. Git commit command must contain a commit message in which you explain whatever change you do in this commit. This will be very helpful while debugging differences so that you can grasp all changes linked to an individual issue.  


@@@Git 
	git commit -m "IssueID: changes reated to user reso not saving projects in propoer syntax"  

As you can see in the message first, I give issue ID and then we mention proper change which I make in that commit.  


#TODO: Demo for commit  

### 4. git push

Your changes are still in your local Repository, Now you require to push them on the hosted repository, so it will we available for others to examine or review by others. Still, you do not merge with the mainstream.  

@@@Git
	git push origin <branch>
	or
	git push

I prefer the first one very much because it makes clear that from where to where this command, pushing your changes on the hosted repository.


#TODO: Demo for git push  

### 5. git pull

You are not the only person who is working on that code, Someone else is also working and that person makes some changes in the hosted repository, now how those differences came to your local repository? By pulling them, They did not come automatically due to merge issues that may occur.

@@@Git 
	git pull  
	
This will bring all changes to your local repository if there is no conflict ( we discuss the latter ).  

#TODO: Demo for pull

Thanks for reading this long, In the next tutorial we learn some useful scenarios.
