Git is a *Version Control System* used within tech fields to manage a project's files. It is especially important as it comes to remote collaboration on projects. Git will save past versions and makes it easy to roll back problematic changes. GitHub is a cloud-based platform built on top of git that is used to host and share projects.

https://git-scm.com/docs
[[git_cheat_sheet.pdf]]

---
#### Git Repository Pipeline
A Git Repository is a directory where git monitors and saves records of a projects files. The git repository pipeline can be broken up into 4 parts:
1. **Working Directory (sometimes called Working Tree)** 
	- The Working Directory is the directory you interact with. This is the directory where the engineer directly updates the project files. 
2. **Staging Area (sometimes called Index)**
	- The Staging Area is an intermediary stage between the working directory and the repository. The changes are *added* to the Staging Area before they are *committed* to the repository. This can be useful for code reviews, to catch problems before they are *committed*.
3. **Local Repository**
	- The Local Repository is the .git folder that git creates in the Working Directory. This is a local copy of the Central Repository. Changes are first *committed* here, the they are *pushed* to the Central repository. 
4. **Central Repository**
	- The Central Repository serves as the heart of the project. This is where the main project files are stored on a central server.
