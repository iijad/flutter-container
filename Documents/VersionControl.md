## Source Code Version Control Tools
### Introduction
Version Control is very critical for maintaining code integrity, tracking changes to the code over time, and enabling collaboration among members of a team. It ensures the stability of the codebase by allowing developers to revert to previous versions if needed, maintains a detailed history of changes for reference and auditing purposes, and facilitates collaboration through features like branching and merging.

### **Version Control System Used**
Git was chosen as the version control system for this project, as there is a familiarity with the system, making it more comfortable to use as navigating and utilizing Github is a smoother process. 

### **Repository Setup**
The Repository is composed of four folders with a ***README.md***:
1. `.devcontainer`- This folder contains the main files used to create the ***flutter container environment***. When the user reopens the repo in the container, it would be the `devcontainer.json` and `Dockerfile` files that download the flutter sdk and create the tools necessary in order to run the environment.
2. `github`- This folder contains the files needed to keep dependencies up-to-date in software projects, which is the file`dependabot.yml`, and to configure the ***CI/CD pipeline***, which is in another folder called `workflows`. In this folder contains the `build.yml` file, which helps automatically build the flutter app whenever changes are made to the repository. 
3. `Documents`- This folder contains the documentaion of this conatainer, which is currently separated into 2 main files.
		 - `Devcontainer.md` - Describes the process of a Devcontainer, including how talking about its importance, its use, and how it was set up.
		 - `VersionControl.md`- Describes the importance of version control, which includes which version control system is being used, the structure of the repository, and how it is being used
		- ***Note***: There are two other miscellaneous files in the folder but they serve no purpose.  
4. `app`- This is the folder which contains all the information about the flutter app, including what type of app it is and the configuration of the app.

### **Common Commands and Usage**
Here are some of the version control commands and their use:
1.  `git init`: Initializes a new Git repository in the current directory.
    
2.  `git clone <repository_url>`: Copies an existing Git repository from a remote server to your local machine. 
	- `git clone https://github.com/iijad/flutter-container` to clone the repo used here.
    
3.  `git add <file>`: Adds changes in a specific file to the staging area, preparing them to be committed.	
	- `git add VersionControl.md` to add this file to the staging area.
    
4.  `git commit -m "<commit_message>"`: Records changes staged in the staging area to the repository along with a commit message describing the changes.
	- `git commit -m "File for Version Control"` to describe the changes that are staged to be commited. 
    
5.  `git status`: Displays the current state of the repository, including files that have been modified, staged, or not tracked.
    
6.  `git diff`: Shows the differences between the working directory and the staging area or the differences between different commits.
    
7.  `git pull`: Fetches changes from a remote repository and merges them into the current branch.
    
8.  `git push`: Sends local commits to a remote repository.
    
9.  `git branch`: Lists all local branches in the repository.
    
10.  `git checkout <branch_name>`: Switches to the specified branch.
    
11.  `git merge <branch_name>`: Merges changes from the specified branch into the current branch.
    
12.  `git log`: Displays a history of commits in the repository.
    
13.  `git remote -v`: Lists all remote repositories associated with the local repository.
    
14.  `git reset <file>`: Unstages changes in a specific file from the staging area.
    
15.  `git revert <commit_hash>`: Reverts a specific commit, creating a new commit that undoes the changes introduced by the specified commit.
	- `git revert goback` to revert back to a previous commit. 

### **Collaboration Features**
Version control tools enable collaboration among team members by providing a centralized repository for the codebase and allowing developers to work on separate branches simultaneously. Pull requests serve as a means to propose changes, which undergo code reviews by peers to ensure quality and adherence to standards before merging into the main branch. Conflict resolution mechanisms help address conflicts that arise when merging changes made by different team members. Additionally, version control systems maintain a comprehensive history of changes, aiding in understanding the codebase's evolution and facilitating bug tracking. Overall, version control tools streamline collaboration, improve code quality, and ensure the integrity of the codebase in software development projects.

### **Challenges and Solutions:**
- ***Transferring to another  control system*** - The initial VCS used was Gitlab, however there were complications in trying to get the ***build phase*** to work properly, so a switch was made to GitHub, which works much better at handling that aspect.
- ***Synching repo to Visual Studio Code*** - This problem was part of the former VCS, but VS Code wanted verification when anyone tries to commit for the first time from a non GitHub source, so all that was needed was to input these two commands:
		- `git config --global user.name "Name Here"`
		- `git config --global user.email "Email here"`
		- With replacing what is in quotes with the users name and email. 

### **Conclusion:**
  
Integrating version control into the project has brought numerous benefits. By leveraging our chosen version control system, we've streamlined collaboration among team members, ensuring everyone has access to the latest codebase and enabling concurrent development through branching. The use of pull requests and code reviews has significantly improved code quality and facilitated knowledge sharing within the team. Additionally, version control has provided valuable insights into the development workflow, allowing anyone to track changes effectively, resolve conflicts efficiently, and maintain a clear history of the project's evolution. Overall, the adoption of version control has proven instrumental in enhancing productivity, coordination, and code management in the project of building a CI/CD Pipeline. 
