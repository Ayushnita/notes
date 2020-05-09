# __GIT Tutorail 1 __

We are going to start a git tutorail series where we can set learn how you can use git to increase your productivity. In this notes section we only pointout commands and some special points so
that while taching we will not miss anything.

If you are refreing this document then you will able to understand which command is usefull for you work and how you can increase you your productivity.  

In this tutorial we learn only five basic git command which we will cover 70% of git, yes only 5 commands. Other commands are usefull for solving complex situations but first understand git
termologies.  

* _repositatory_ --> your whole project is known as a repositatory. which is hosted on any git supported server like github, atlassian, gitlab etc.  
* _branch_ --> In git branches are tree branches they start from a one point and then start moving in seprate direction then main streem and at point we want to merge in main streem then you
  can .  
* _HEAD_ --> This is a location where you are currently working, it is like a pointer which moves with you changes.  
* _origin_ --> this is a thread(url) which join your hosted repo to your local repo.  

All the avobe mention terms we disscussed in detail once we came on that point.  


## __Git Commands__

### __1. git clone__  

First basic command is _git clone_ this command is use to clone any of your repo form your hosted location to your local system where you do devlopment.  

@@@Git
	git clone http://github.com/<username>/<reponame>.git [directory]


Directory is optional if you did not porovicde any then it create a new directory with repo name and copy code in that.

#TODO: Demo for clone

### __2. git add __

Once we clone repo we start changing code and we do some changes and after that we have to tell git that these file changes we want to tell git that these changes now will take care by you and
wehn I commit considder these changes only. you can ommit some changes by not mention them in add command.

@@@Git
	git add <file name >/<foldername>

EG: if you provide __.__ means inside current folder all change.  

#TODO: Demo for add 


### __3. git commit __

Now you are sure these changes are fine and we are looking forward to make it persisit then we use git commit command to make a snapshot and add it in main streem. git commit command must
contain a commit message in which you describe what change you make in this commit. This will be very helpful while debugging changes so that you know all changes related to one issue is inside
one commit and then you work only on that commit.

@@@Git 
	git commit -m "IssueID: changes reated to user reso not saving projects in propoer syntax"  

As you can see in message first I give issueID and then we mention proper change which I make in this commit.  

#TODO: Demo for commit  

### __4. git push __

your changes are still in you local now you want to push them on hosted repo so it will we avialble for others to examin or review by others still you not merge with main streem dissus later.

@@@Git
	git push origin <branch>
	or
	git push

I prefer first one very mush clear from where to where, from this command you push your chnges on hosted repo.

#TODO: Demo for git push  

### __5. git pull__

you are not only person who are working on that code someone else also working and that person make some chnages in hosted repo now how these changes came to you local repo. By pulling them
they did not came automaticaly due to merge issue.

@@@Git 
	git pull  
	
This will take all changes to your local if there is no conflict ( we discuss latter ) .

TODO Demo for pull

Thanks for reading this long in next tutorail we learn some usefull sinarios.
