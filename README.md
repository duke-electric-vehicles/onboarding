# Linux Development Environment and Docker Setup

Before you can start contributing to our code repositories, you will need to setup a development environment. This will involve two initial steps: creating a Linux environment, and installing Docker. 

### 1. Creating a Linux Environment

Linux is an operating system, just like macOS or Windows, which is widely favored by programmers due to its flexibility, compatibility, and powerful command line tools. Almost all of our development will occur through a Linux based environment.

#### Mac

Since the macOS is based of Unix (predecessor to Linux), most of the important Linux command line tools we will be using are already natively installed. Later on, you may want to partition your hardrive to run a complete version of Linux, but for now, you can skip directly to the next step.

#### Windows

Unlike macOS, Windows does not support Linux natively. However, Microsoft does provide the Windows Subsystem for Linux (WSL). WSL is essentially a command line only virtual machine the runs a full instance of Ubuntu, a common Linux distribution. Follow the instructions [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10) to install WSL. In step 6, make sure to install **Ubuntu 20.04 LTS** from the Microsoft Store.

### 2. Install Docker

Docker is virtualization software that allows us to create consistent runtime environments through the use of containers. You can think of a container as a virtual machine with only a command line interface. Containers are created through the use of Dockerfiles, which specify exactly what software dependencies, libraries, and configuration files are needed. This allows us to easily create reliable and consistent environments that are seperated from your own computer. If something bad happens in a container, you can always just delete the container and start with a fresh one. The same cannot be said for your host computer.

#### Mac

Installation instructions for Docker Desktop for Mac are [here](https://docs.docker.com/docker-for-mac/install/).

#### Windows

For the Windows installation, we need to make sure that Docker is integrated with the WSL environment. Follow the instructions [here](https://docs.docker.com/docker-for-windows/wsl/) to install Docker Desktop and setup the integration with WSL.

---

### **You have now finished setting up your Linux development environment with Docker! All future tutorials will assume you are working in this environment. For macOS users, that will be your default Terminal, and for Windows, it's your WSL environment.**

# DEV Git Workflow

When contributing to any of our repositories there is a standard workflow you should follow. Since you will not be able to push your changes to the master branch of the repository you should instead make all of your changes in your own branch.

[Here](https://github.com/joshnh/Git-Commands) is a list of useful git commands, however all of the basic ones you need can be found below. If you have any questions don't hesitate to reach out to one of us. 

##### Setting up SSH key
Before you can run any git commands from the command line you need to add an ssh key to your github account. To check if you have a key already enter the following command:
```bash
cat ~/.ssh/id_rsa.pub
```

If you already have a key generated copy it and go [here](https://github.com/settings/keys) to add the new ssh key to your account.

If you need to generate a new ssh key you can use the following command.

```bash
ssh-keygen -t rsa -b 4096
```

Then, to copy the key enter the following cat command again and go [here](https://github.com/settings/keys) to add the new ssh key to your account.

```bash
cat ~/.ssh/id_rsa.pub
```

###### Cloning a repository

You can clone a git repository (like this one) by using the ```git clone``` command. You may need to add an ssh key to your account before you are able to clone the repository. Help on that can be found [Here](https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account).

```bash
git clone git@github.com:duke-electric-vehicles/onboarding.git
```

This will clone the repository into your current directory, which can be seen by typing the ```ls``` command. Navigate into the repository by typing ```cd onboarding```.

###### Branching

Once you have cloned the repository you should be able to view all of the branches in the repository by typing.

```bash
git branch -a
```

Any modifications you make to the code should be made in a branch other than the master branch. To create a new branch for you enter the following command.

```bash
git branch [your_name]
```

Then to swap to your branch:

```bash
git checkout [your_branch]
```

###### Committing Changes

Now you can make changes to the code. You should now open up the ```NAMES.md``` file and add your name.

You can view all of the changes you've made since the last commit by entering the following command.

```bash
git status
```

Here you can select which files you want to commit by typing:
```bash
git add [name_of_file]

or if you want to add all files

git add .
```

Then you can commit your changes using the following command.
```bash
git commit -m "[Short message describing changes you made]"
```

###### Pushing changes to Github and creating pull request

Now you can push your changes back to github by using:

```bash
git push origin [name of your branch]
```

If you go into your repository on github you should be able to see the branch you created and all of your changes. If you are ready for your code to be pulled into the master branch create a pull request on github.
