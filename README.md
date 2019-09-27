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
