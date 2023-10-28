# TOOLS

## Dropbox

## Github

Github is a version control system. To get started, all you need to do is get a free account on their website [Github](https://github.com/). You can probably also get a free account upgrade by requesting an upgrade as a student or researcher. Here are some online resources to help you get started. Please let me know if you find more/better ones.

- [Open Science MOOC - Module 5: Open Research Software and Open Source](https://github.com/OpenScienceMOOC/Module-5-Open-Research-Software-and-Open-Source/blob/ma)
- [GitHub for Portfolios](https://dannguyen.github.io/github-for-portfolios/lessons/clone-github-pages-repo/)
- [YouTube Tutorial: Getting Started with GitHub](https://www.youtube.com/watch?v=cQUApvaiYI0)
- [Programming Historian Lesson: Getting Started with GitHub Desktop](https://programminghistorian.org/lessons/getting-started-with-github-desktop#install-github-desktop)

### Introduction - please read it

To access the most updated version of this introductory material, please click [here](link-to-intro). In “GitHub: a Practical Introduction” I attempted to follow each explanation of Github’s workflow and commands with an example on how to use them. If you want to follow the example and practice the commands, please email me at michaelbest@gmail.com so I can grant you “collaborator access” to the GitHub repository for this introduction. You will need it to perform some of the commands. In the following sections, I will guide you through (i) editing an existing project in Git and (ii) creating a project of your own and transferring it to Git. Although the examples are very simple, the commands are the same that you’ll be using in more complex projects.

### GitHub Basics

#### Distributed Version Control System

As you probably know, GitHub is a Version Control System (VCS) – it stores in repositories (often called repos) all the versions from your project that you saved, so you don’t lose your project’s history. However, a key feature of GitHub that differentiates it from older VCSs is that it is a Distributed VCS. This means that GitHub not only stores a version of your project on its cloud service (called remote repo) but also every user from a project stores the entire history of the project on their computers. So besides storing the current version of the project that you are working on (called the working directory), you also store a Git repository on your computer with the project’s history (called the local repo).
This allows GitHub to work (i) incredibly fast, since it doesn’t have to access the internet to access a project’s history; (ii) independently from your internet connection, for the same reason, and (iii) very safely, since every user serves essentially as a backup of the project’s history. This also explains why most users keep their code in a GitHub folder and their data on a storage system (e.g. Dropbox)–it would be too costly to save multiple versions of your datasets to your computer.

In figure 1 above, the Version Database is what we call the “remote repo.” The Files in Computer A and in Computer B are the “working directories,” and the Version Database in each computer is the “local repos.” Local repos, or .git repos, are by default hidden on your computer, so you’ll only see your working directory. From this point onward, we will see how to create local and remote repos to store your project’s history.

#### Git Setup

1. Install the program. You can find very simple instructions [here](link-to-installation).
2. Create an account on [GitHub](https://github.com).
3. (Optional) set up your identity. Go to your terminal and type the following commands:

   ```bash
   $ git config --global user.name "John Doe"
   $ git config --global user.email johndoe@example.com
Don’t actually copy the `$` symbol, this is standard notation to let you know this command should be run in the terminal. If you need any help to understand a command, you can type the `git help <verb>`. For instance:

```bash
   $ git help config
   ```

Most of this section’s content was a summary from Pro Git - Everything You Need to Know About Git, one should read it for a more detailed understanding.

### Joining a Project: Cloning an Existing Repo
This section guides you through an example on how to join an existing project, probably that your co-author or Professor already began. This will be useful to introduce some concepts and Git commands. It will also be all that RAs will need to know 90% of the times.

#### Clone a repo
To clone a repository means that you are reaching out to a remote repository and copying nearly all data that the server has into a new local repo in your computer. Let’s illustrate this with an example:
1. Access the URL of the remote repo.
2. Open terminal
3. Go to the directory where you want your repo to be:
```bash
   $ cd /Users/username/documents
```

4. Go to the remote repo click on clone or download and copy that link displayed. 
5. Then, on your terminal, clone the repository with git clone <url>
```bash
$ git clone "https://github.com/luigicaloi/GitShortIntro.git"
```
This will create a GitShortIntro directory with a working copy of the latest version of the project. It also stores a .git directory (the local repo) inside it, which is hidden. For more info, see this.
### Modifying Files
If you open the new GitShortIntro directory, you’ll see that there are only two files, “AllRead- ers.tex” and “Test.do,” and one folder “GitHub\_a\_Practical\_Introduction”. Your task is sim- ple: open the “AllReaders.tex” file and include your name at the end of the list of all readers. Now that you have made changes to the working directory, let’s see what is your status in Git. Change the directory in the terminal for the one from your new project. For instance:

```bash
   $ cd "/Users/username/documents/GitShortIntro " 
   $ git status
```
Don’t worry about the branch message yet, we’ll see what that is in section 10.5.1Git Branching. GitHub realizes that your local repo is different from your working directory, it realized that you made changes to the “AllReaders.tex” file and shows it under “Changes to be committed.” Our first goal is to make sure that your local repo also saves those changes (we’ll take care of the remote repo in the next section). You first need to tell GitHub what documents you want to save the changes in the local repo with the following command:
$ git add "AllReaders.tex"
Now run git status again and you’ll see:

### Committing Modified Files
AllReaders.tex is now under the “Changes to be committed.” This basically means you told GitHub you want to save the changes made to it. Next, we need to “commit” those changes. Committing is telling GitHub to take a snapshot of your project in the working directory and save it to your local repository. In other words, you are saving your latest changes to the git repo. See here for more details. The command to commit changes is:

```bash
git commit −m "A message explaining your changes to the project "
```