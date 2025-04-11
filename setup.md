# Working environment setup

## What you will need

1. A rudimentary understanding of the terminal. The **terminal** is just an interface to execute commands in an operating system (most often, your local one).
2. (Optional but recommended) A rudimentary understanding of git and GitHub. **git** is a program to version code, i.e. it allows you to keep track of different versions of your code. See here for a [tutorial](https://git-scm.com/docs/gittutorial). **GitHub** is instead an online service provided by a company, now part of Microsoft, which allows you to have multiple code repositories and interact with them via git. 
3. (Optional but recommended) **conda**. Conda is a cross platform package and environment manager that installs and manages conda packages from the Anaconda repository as well as from the Anaconda Cloud. Which means you will be able to a) create Python environments and b) install packages into them. Some packages we will use might not be in the Anaconda Cloud, in that case you can rollback to using `pip install`. You can use your main Python installation if you like, but I recommend using conda to keep experiments separated from the OS.
4. **Jupyter notebooks**, a package which allows you to run a web server and have interactive notebooks in it.
5. A **text editor** to write code when not using notebooks. If you don't already have a preferred one, check [Sublime Text](https://www.sublimetext.com/) or [Atom](https://atom.io/).

## How to get there

### Basic terminal

For Mac OS and Linux (mostly):

* `ls` list folder contents
* `cd PATH` move current working directory to the PATH location. `cd ~` for your home folder
* `cd ..` goes up one level in the folder structure
* `touch fun.py` creates an empty file named `fun.py`
* `mv fun.py stuff/` moves `fun/py` to the `stuff` folder, if it exists. If it doesn, `mkdir stuff`

For more, see [here](https://www.makeuseof.com/tag/mac-terminal-commands-cheat-sheet/).

For Windows, see [here](https://www.thomas-krenn.com/en/wiki/Cmd_commands_under_Windows).

### Getting class code and working on your own

#### The best way - Cloud

1. The first time, make a Github account and fork the repository to your Github account: go to https://github.com/bloemj/AUC_TM_2025 and click Fork
2. Get updates to the code before every lab: In your fork on the Github website, click "Fetch upstream"
3. Launch notebooks by going to your Google Colab: https://colab.research.google.com/ and loading them using the "Open Notebook" window. Enter the GitHub URL of the fork of the course materials in your own GitHub account to be able to save your changes. 

#### The best way - Offline

1. The first time, clone the repository locally using `git clone git@github.com:bloemj/AUC_TM_2025.git`.
2. Keep getting updates to the code before every lab by going to your local repository directory (e.g., `cd PATH_TO_REPO`) and `git pull`. This will pull all remote changes to local, and update your repository.

#### The easy way - 1

You might want to use the [GitHub Desktop app](https://desktop.github.com) to keep track of your repositories. If you have it installed, instead of cloning the repo you can use the Open in Desktop option.

#### The easy way - 2

Just download the repository code before every lab, by clicking on `Clone or download`, and then `Download ZIP`. You will then need to unzip the downloaded file and open it either in Google Colab or locally.

**IMPORTANT**: Cloning or downloading a copy of the course repo will conflict with any change you made yourself to the files in there. This is especially the case if you do not work in your own fork of the repository: if you pull, then you edit, then I edit, then you pull again, there will likely be a conflict if we both changed the same files. I recommend to fork the repository to your own Github account to have version control for your own edits (see The best way - Cloud, but you can fork locally too). Alternatively, when working locally, I recommend that you put your edited copies of the repository contents in a separate folder to keep your changes.

### Running Python on your own machine: Conda

1. Install conda using the [Anaconda distribution](https://www.anaconda.com/distribution/), remember to pick Python 3.8 and the OS you need. Get the graphical installer.
2. After installation, you will have an app called **Anaconda Navigator** installed. You can create and manage enviromnents and use jupyter notebooks from it, without using the terminal, mostly.
3. If you use the terminal, remember to relunch all your terminal windows after the installation of conda. Then refer to [this guide](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html). The msot basic commands are:
    - `conda create -n myenv python=3.8 anaconda` which will create an environment named `myenv` and install the libraries in the anaconda distribution into it (handy to have most of the popular stuff at the ready).
    - `conda activate myenv`.
    - `conda deactivate`.
    - `conda remove --name myenv --all` to remove an environment and all its packages.

Some other ways to have an easier life:
* Try **Spider** from the Anaconda Navigator, which is a nice programming GUI similar to R Studio, if you are familiar with it. 

#### Backup option: Binder

Just click on lunch Binder in the repo. Remember to download any file you edited and want to preserve.

### Jupyter 

This should be pretty straightforward if you have the Anaconda Navigator or have an environment created as detailed above. More info [here](https://medium.com/codingthesmartway-com-blog/getting-started-with-jupyter-notebook-for-python-4e7082bd5d46).


## Managing the fork

Pull in updates from the professor’s repo

When the professor adds new material, fetch and merge (or rebase) them:

```
# Go back to your main branch
git checkout main

# Fetch and merge the professor's changes into your main
git fetch upstream
git merge upstream/main

# Now, rebase your work branch onto the updated main (to include the latest updates)
git checkout notebooks
git rebase main

```
Or use `git pull --rebase upstream main` if you're comfortable with rebase in one step
