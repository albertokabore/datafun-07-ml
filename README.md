# datafun-07-ml
# Starting the New Project

1. In your browser, create a GitHub project repository with a default README.md. Name your repository  datafun-07-ml or datafun-07-applied.


2. Clone your new repository down to your machine into your Documents folder. 

git clone https://github.com/albertokabore/datafun-07-ml

3. Open your new project repository folder in the Documents folder of your machine in VS Code (if you haven't already).

4. In VS Code, add a useful .gitignore file with a line for .vsode/ and .venv/ and whatever else doesn't need to be tracked in the repository.

```.gitignore
       1. .vscode/
       2. .venv/
       3. .ipynb_checkpoints/

```

5. In VS Code, edit your README.md to record your commands, process, and notes so far.

6. In VS Code, open a terminal - PowerShell if Windows, zsh or bash if Mac/Linux. 
 
 7. Use the terminal to git add your files and folders to source control, and git commit your changes with a useful message (e.g. "initial commit"), and git push the changes up to GitHub.

```PowerShell
git add .
git commit -m "Initial commit"
git push origin main
```

8. Verify your GitHub repository.

# Create and Manage Your Virtual Environment

1. Open Project Folder in VS Code

2. Open a terminal window in VS Code (PowerShell for Windows, zsh or bash for Mac/Linux).

3. Git Pull

In the terminal, run git pull to fetch any changes that might have been made to the GitHub version. There may not be any changes, but it's good practice to pull every time you start work on a git project.

```
git pull
```

4. Create Project Virtual Environment (One-Time Only)

In the terminal, run the command `py -m venv .venv` to create a new .venv environment in the project repo. 

```
py -m venv .venv
```

5. Activate the Project Virtual Environment (Every time you open a terminal)
In the terminal, activate your environment using the command for your operating system. 

```
.venv\Scripts\Activate
.\.venv\Scripts\Activate.ps1
```

Verify you see the virtual environment name (.venv) in your terminal prompt.

6. Install Packages into Active Environment (One-Time, As Needed)
Verify your project virtual environment located in .venv is active. If not, activate it. You should see .venv in your terminal prompt. Use your favorite method to install the necessary packages.

In the terminal, use `py -m pip install` command(s) to install necessary packages into your active project virtual environment.

```
py -m pip install jupyterlab numpy pandas pyarrow matplotlib seaborn scipy
```

7. Edit README.md
In VS Code, edit your README.md file to record your commands, process, and notes.

8. Set VS Code Interpreter
In VS Code, from the menu, select View. From the dropdown menu, select Command Palette....

Alternatively, you can use the shortcut Ctrl+Shift+P (Windows/Linux) or Cmd+Shift+P (Mac) to open the Command Palette.

In the Command Palette, start typing Python: Select Interpreter.

When you see Python: Select Interpreter in the list of options, click on it. A list of available Python interpreters will appear.

Locate and select your project's virtual environment, typically named .venv (or similar).

Confirm your selection. VS Code will now use the selected interpreter for your project.

9. Git Add / Commit / Push to GitHub
Use your terminal to add your files to source control, commit your changes to git, and push them up to GitHub.

Git add any new files.

```PowerShell
git add .
```

Git commit changes.

```
git commit -m "after .venv setup"
```
Git push to GitHub.

```
git push -u origin main
```

10. Verify
Verify your README.md and .gitignore (and optionally, requirements.txt if used) appear correctly in your GitHub repo. Since you added .venv/ to your .gitignore, your .venv folder should NOT appear in GitHub. This is good - it saves space and allows us to track just the progress of our project files.

