# datafun-07-ml
# Starting the New Project

Open your browser and navigate to GitHub.
Create a new repository named datafun-07-ml. Make sure to initialize it with a default README.md.
Clone the Repository
Clone the repository to your local machine:
git clone https://github.com/albertokabore/datafun-07-ml
Open your new project repository folder in the Documents folder of your machine in VS Code (if you haven't already).
In VS Code, add a useful .gitignore file with a line for .vsode/ and .venv/ and whatever else doesn't need to be tracked in the repository.

```.gitignore
       1. .vscode/
       2. .venv/
```

In VS Code, edit your README.md to record your commands, process, and notes so far. 

Use the terminal to git add your files and folders to source control, and git commit your changes with a useful message (e.g. "initial commit"), and git push the changes up to GitHub.

```PowerShell
git add .
git commit -m "Initial commit"
git push origin main
```


# Create and Manage Your Virtual Environment

Create a Virtual Environment
Navigate to the project directory and create a virtual environment in the .venv folder:
py -m venv .venv
Activate the Virtual Environment Activate the virtual environment:
.venv\Scripts\activate
Install Dependencies
Install a Package
py -m pip install requests
Install initial project dependencies:
py -m pip install jupyterlab pandas pyarrow matplotlib seaborn
List Installed Packages
py -m pip list
Freeze Dependencies
Freeze the installed requirements into a requirements.txt file:
py -m pip freeze > requirements.txt
Update .gitignore
Create or update the .gitignore file in the root project folder and add the following entries:
.venv/
.ipynb_checkpoints/
Commit Changes
Add the changes to git and commit them:
git add .
git commit -m "Initial commit"
git push origin main
Working with Jupyter Notebooks
Setting Up Jupyter Notebook:
Ensure that Jupyter is installed within your virtual environment. If not, install it using pip:

py -m pip install jupyter