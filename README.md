# datafun-07-ml

## Starting the New Project

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

## Create and Manage Your Virtual Environment

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

Verify your project virtual environment located in .venv is active. If not, activate it. You should see .venv in your terminal prompt. 

In the terminal, use `py -m pip install` command(s) to install necessary packages into your active project virtual environment.

```
py -m pip install jupyterlab numpy pandas pyarrow matplotlib seaborn scipy
```

7. Edit README.md
In VS Code, edit your README.md file to record your commands, process, and notes.

8. Set VS Code Interpreter

Set your VS Code Python Interpreter so your installed packages will be available for import.

9. Git Add / Commit / Push to GitHub

Use your terminal to add your files to source control, commit your changes to git, and push them up to GitHub.

Git add any new files.

```PowerShell
git add .
```

Git commit changes.

```
git commit -m "initial commit"
```
Git push to GitHub.

```
git push -u origin main
```

10. Part 1 - Chart a Straight Line
Follow instructions from text Intro to Python for Computer Science and Data Science on page 414, Chapter 10.16. Utilize markdown cells to create section headings as you work.

11. Part 2 - Prediction
Follow instructions from text Intro to Python for Computer Science and Data Science on page 416, Chapter 10.16. Utilize markdown cells to create section headings as you work. You will create seven section while working through the data:

```Python
#Import Dependencies 
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
from scipy import stats
import sklearn
from sklearn import metrics
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.linear_model import ElasticNet, Lasso, Ridge 
from sklearn.model_selection import KFold, cross_val_score
```

Section 1 - Data Acquisition

```Python
# Load the dataset into a pandas DataFrame
nyc = pd.read_csv('ave_hi_nyc_jan_1895-2018.csv')
```

Section 2 - Data Inspection

```Python
# let's view the first 5 rows of the data
nyc.head()
# let's view the last 5 rows of the data
nyc.tail()
```
Section 3 - Data Cleaning

```Python
# Improve the column names and clean up the date series. 
nyc.columns = ['Date', 'Temperature', 'Anomaly']
# Verify transformations
nyc.head(3)
#checking column type
nyc.Date.dtype
# Lets truncate last two digits
nyc.Date = nyc.Date.floordiv(100)
nyc.head(3)

```


Section 4 - Descriptive Statistics

```Python
## Set the display precision to 2 decimal places. Use 'display.precision' instead of 'precision' as shown in the text.
pd.set_option('display.precision', 2)
```

```Python
# let's view the statistical summary
nyc.Temperature.describe()
```

Section 5 - Build the Model

```Python
# Lets use the SciPy stats module linregress function 
linear_regression = stats.linregress(x=nyc.Date,
                                     y=nyc.Temperature)
```

```Python
# calculate slope and intercept for the best fit line through the data.
linear_regression.slope
```

```Python
# calculate intercept for the best fit line through the data.
linear_regression.intercept
```

```Python
## Lets calculate intercept for the best fit line through the data.
linear_regression.slope * 2019 + linear_regression.intercept
```

```Python
# let calculate the intercept for the best fit line through the data.
linear_regression.slope * 1850 + linear_regression.intercept
```

Section 6 - Predict

```Python
# Let Use our model to predict the "average high temp in Jan" for the year 2024 (just like they did for 2019).
temp_2024 = linear_regression.slope*2024+linear_regression.intercept
print(f'the predicted average high temp for the year 2024 is {temp_2024}')
```

Section 7 - Visualizations It may be helpful to outline these headings in markdown cells, with code cells in between.


```Python
# Let Use Seaborn to generate a scatter plot with a best fit line
sns.set_style('whitegrid')
axes = sns.regplot(x=nyc.Date, y=nyc.Temperature)

axes.set_ylim(10, 70)
```

12. Part 3 - Prediction
Follow instructions from text Intro to Python for Computer Science and Data Science on page 620, Chapter 15.4. Utilize markdown cells to create section headings as you work. From Part 2, you have already aquired, inspected, cleaned, and ran descriptive statistics on the data. You will do the following with the data in Part 3:

13. Section 1 - Build the Model


```Python
Splitting data into training and test set:

X_train, X_test, y_train, y_test = train_test_split(nyc.Date.values.reshape(-1,1), nyc.Temperature.values,random_state = 11)
```

```Python
#check the shape of the training set

X_train.shape
```

```Python
#check the shape of the testing set

X_test.shape
```

```Python
# Lets train the model using Linear Regression Fit

linear_regression = LinearRegression()
linear_regression.fit(X=X_train, y=y_train)
```

```Python
## Determining the coefficient 
m = linear_regression.coef_
print(m)
```

```Python
# Determining  the intercept
b = linear_regression.intercept_
print(b)
```

```Python
print(f'The linear regression equation is y = {m}x + {b}.') 
```





Section 2 - Test the Model

```Python
predicted = linear_regression.predict(X_test)
expected = y_test
for p, e in zip(predicted[::5], expected[::5]):
    print(f'Predicted: {p:.2f}, Expected: {e:.2f}')
```

Section 3 - Predict

```Python
predicted = linear_regression.predict(X_test)
expected = y_test
for p, e in zip(predicted[::5], expected[::5]):
    print(f'predicted: {p:.2f}, expected: {e:.2f}')
```

```Python
#The expected temperature according to the model in the year 2024. 
predict = (lambda x: m * x + b)
predict(2024)
```

Section 3 - Visualizations It may be helpful to outline these headings in markdown cells, with code cells in between.

```Python
# Lets use Seaborn to generate a scatter plot with a best fit line.
axes = sns.scatterplot(data=nyc, x ='Date', y='Temperature', hue='Temperature', palette = 'winter', legend =False)
x = np.array([min(nyc.Date.values), max(nyc.Date.values)])
y = predict(x)
line = plt.plot(x, y)
```
14. Part 4 - Insights

Part 4 is a discussion of the two different methods use in this project to visualize data and find the linear regression line.

15. Part 5 - Bonus
Part 5 is continued practice of using machine learning, but with multiple linear regression. Follow instructions from text Intro to Python for Computer Science and Data Science on page 624, Chapter 15.5. Utilize markdown cells to create section headings as you work. You will create seven section while working through the data:

Section 1 - Loading Data
Section 2 - Displaying Data
Section 3 - Exploring Data with Pandas
Section 4 - Descriptive Statistics
Section 5 - Visualizing the Features
Section 6 - Splitting the Data for Training and Testing
Section 7 - Training the Model
Section 8 - Testing the Model
Section 9 - Visualizing the Expected vs Predicted Prices
Section 10 - Regression Model Metrics
Section 11 - Choosing the Best Model It may be helpful to outline these headings in markdown cells, with code cells in between.

Save your project and push back to your repository.

Final insight
Conclusion


```
git add .
git commit -m "final commit"                         
git push origin main
```
