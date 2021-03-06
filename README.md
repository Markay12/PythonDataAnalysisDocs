# Python Data Analysis

## Introduction

What is data analysis?  
- Data analysis involves exploring, representing and understanding data. Whether this is large amounts of data (big data) or small amounts such as a local project, data analysis can be conducted in many forms.

One major use of data analysis comes with *machine learning* which is a 

> subset of data that deals with predictive modeling
- Microsoft 

This uses data we have found to create models that can predict values or future outcomes

Data that is collected from this analysis can be used in many situations that benefit the greater public by finding the best ways to teach and accommodate to others. By learning the best methods of everyday tasks, we can better optimize our lives.


## Data Analysis - First Dive

Analysis of data is usually done in what is called an *iterative* process which allows the scientist to analysis and test hypotheses along the way learning from what they are collecting

Their main concern is with finding ways to explore, visualize and manipulate the data they are given. Finding the best way to represent this data can lead to better results and a stronger understanding

First, we must begin with where to start with understanding the data that we are collecting and where to place it as we are collecting it.  
One of the best tools to use here is **Jupyter Notebooks** and **Python**  

Python is handy due to its flexibility in multiple situations. This is one of the main reasons for its heavy use in any industry, especially data science. 

### NumPy and First Data Set

NumPy is a Python module that allows the user to model and understand the data that they've collected as well as manipulate the data any way they see fit.  

Here we begin with our first representation in Python:  

```Python
{
    data = [50,50,47,97,49,3,53,42,26,74,82,62,37,15,70,27,36,35,48,52,63,64]
    print(data) 
}
```
What we have done here is taken our data and placed it into a basic array. While this is great for manipulation of the data, there are better ways to do this with NumPy.  

```Python
{

    import numpy as np

    grades = np.array(data) #data used from above
    print(grades)

}
```

To see their differences try 

```Python
{

    print (type(data),'x 2:', data * 2)
    print('---')
    print (type(grades),'x 2:', grades * 2)

}
```

The first one in this instance multiplies the length of the array by two creating a new list that is twice the length of the original. Whereas the second multiplication goes through the list just as a vector and results in the same length array with each element being multiplied by two.  

### Multiple Dimension Arrays
```Python
{

    grades.shape

    # This will return the shape of the array being 22 in length with no columns
    # OUTPUT: (22,)

}
```

To access the first element, we would do this in the same way as many other programming languages with the first element beginning at index 0.   

To access use `grades[0]`  

We can also use some of NumPy's awesome integrated features and find the average/mean of our data with a simple operation  

```Python
{

    grades.mean()

}
```

## Second Data Set

Here we will add study hours for the students in our class to compare with their grades  

```Python
{

    # Define an array of study hours
    study_hours = [10.0,11.5,9.0,16.0,9.25,1.0,11.5,9.0,8.5, 14.5,15.5, 13.75,9.0,8.0,15.5,8.0,9.0,6.0,10.0,12.0, 12.5,12.0]

    # Create a 2D array (an array of arrays)
    student_data = np.array([study_hours, grades])

    # display the array
    student_data

}
```

Now we have a two-dimensional array which puts these two data sets right next to each other  

Let's look at the shape of our data set! 

`student_data.shape`  

Output: (2, 22) 

Now, what do these two numbers mean? The first number 2 represents that the data array contains two elements (study_hours, grades) and the 22 represents both arrays containing 22 elements each  

If you're the inquisitive type, like myself... what happens when there are two arrays that aren't the same size?  
- The output will just tell you that there are two elements (2,)
  

So, how do we navigate through this data? Just like when we were navigating the first array, the index begins at 0 and we specify based off how we input the elements initially. `student_data = np.array([study_hours, grades])`

So, let's find the first element of the first data set

```Python
{

    student_data[0][0]

}
```

This will give us the output of 10.0 which is the first input for our *study_hours* data set. So how does the average of the first array compare to the average of the second array?  

```Python
{

    #get average of the study hours
    avg_study = student_data[0].mean()

    #get average of the grades
    avg_grades = student_data[1].mean()

    print('Average study hours: {:.2f}\nAverage grade: {:.2f}'.format(avg_study, avg_grade))

}
```

## Exploring Tabular Data with Pandas

Pandas? Why do we need to worry about these fuzzy animals?  
Pandas is a reference to another import package just like NumPy and gives us more accessibility to our data  

This will all function and run around the **DataFrame**

```Python
{

    import pandas as pd

    df_students = pd.DataFrame({'Name': ['Dan', 'Joann', 'Pedro', 'Rosie', 'Ethan', 'Vicky', 'Frederic',    'Jimmie', 'Rhonda', 'Giovanni', 'Francesca', 'Rajab',  'Naiyana', 'Kian', 'Jenny','Jakeem','Helena','Ismat', 'Anila','Skye','Daniel','Aisha'],
    'StudyHours':student_data[0],
    'Grade':student_data[1]})

    df_students 

}
```

In addition to what we have defined being the columns of students, hours spent studying and grade. Each will be given their own row number which you can specify. Since we did not this will begin at 0 and increment +1


Let's find information for the fifth student within our data set and output everything that we know about them  

`df_students.loc[5]`  
- As shown here the data is found and given an output with the use of data.loc[element]

```
{

    OUTPUT
    Name    Vicky
    StudyHours  1
    Grade       3
    Name: 5, dtype: object

}
```

We can also get a range, say the first name up until Vicky our fifth name

```Python
{

    df_students.loc[0:5]

}
```

To find information regardless of the ordinal position within the data frame we use something called iloc  

```Python
{

    df_students.iloc[0:5]

}
```

There is one major difference between these two. The first `loc` returns 6 rows while `iloc` will return only five since integer ranges don't include upper bound values within iloc.  

iloc identifies data values in our DataFrame by position, which would go past rows and columns

So, how does loc work with columns? **loc** is used to located data items based on index rather than positions. In absence of index the rows in the DataFrame are indexed as integer values

Use loc to locate data items based on index values rather than positions. The rows, as specified before are set by integer values beginning at zero. However, our columns were created by using the time spent studying and grade achieved.

`df_students.loc[0, 'Grade']`  

We can also use the **loc** method to find indexed rows based on filtering an expression reference

```Python
{

    df_students.loc[df_students['Name']=='Aisha']

    # Output
    # 21 Aisha 12.0 64.0

}
```

another method to accomplish this same task would be  
`df_students.query('Name=="Aisha"')`  
`df_students.query('Name=="Aisha"')`  


## Load Data from a file

This is something that is extremely helpful if we have a nice way to collect data but want a way to port this information into our program  

How do we do this?  

```Python
{

    df_students = pd.read_csv('data/grades.csv',delimiter=',',header='infer')
    df_students.head()

}
```

We use our import .read_csv to load data from our text files. You can also specify delimeters as well as the first row which contains the column names

## Handling Missing Values

Just think... you are at the end of your research; you have most of your data but there are some holes that you are missing which cannot be filled by collected data. What do we do?  

The method to specify these missing values are defined by isnull  

```Python
{

    df_students.isnull()

    # if we have a larger data set we would 
    # want to find all of the missing data spots

    df_students.isnull().sum()
        
}
```
When we use the second `df_students.isnull().sum()` we learn that we are missing 1 StudyHours value and two Grade values

But... what if we want to just see these missing values?  

```Python
    df_students[df_students.isnull().any(axis=1)]
```

Here we will just be told where the NULL value is with NaN. How do we fill these values in?...  

We can *impute* these replacement values, and just replace the value with the average amount or the mean of the whole rest of data collected --> `fillna`

```Python
    df_students.StudyHours = df_students.StudyHours.fillna(df_students.StudyHours.mean())
    df_students
```

However, in most cases you don't want to just add data to a set for integrity and accuracy reasons. For this we can just remove that row completely.  

```Python
    df_students = df_students.dropna(axis=0, how='any')
    df_students #display the data set
```

---

# What does our Data Say?

## Statistical Data

Our data is clean and now we can look at all that we have and derive some values  

```Python
    # Get the mean study hours using to column name as an index
    mean_study = df_students['StudyHours'].mean()

    # Get the mean grade using the column name as a property (not because we need to, but just for show)
    mean_grade = df_students.Grade.mean()

    # Print the mean study hours and mean grade
    print('Average weekly study hours: {:.2f}\nAverage grade:   {:.2f}'.format(mean_study, mean_grade))
```

What if we just want to know the students that studied for over the average amount of time?  

```Python
    df_students[df_students.StudyHours > mean_study]
```

So, if we want to find the average grade of those who studied over the average amount of time we can append `.Grade.mean()` at the end  

```Python
    df_students[df_students.StudyHours > mean_study].Grade.mean()
```

So, what if anyone in the class needs a 70 to pass? Well, we can use Panda again to declare whether someone had passed or failed. We can just add this to our list as a new column. 

```Python
    passed = pd.Series(df_students['Grades'] >= 70)
    df_students = pd.concat([df_students, passed.rename("Pass")], axis=1)
    df_students
```

We can also group all of the students that passed and all of the students that failed together. 

```Python

    #how many students Passed/Failed
    print(df_students.groupby(df_students.Pass).Name.count())

    #Mean time to pass and mean time to fail
    print(df_students.groupby(df_students.Pass)['StudyHours', 'Grade'].mean())

    #sort by grades 
    df_students = df_students.sort_values('Grade', ascending=False)

    # Show the DataFrame
    df_students

```

---

# Data Visualization

So, just like NumPy and Panda we are going to have to visualize our data using some predefined library  
The one that we are going to use here is Matplotlib  

```Python

    #display the plot within the notebook
    %matplotlib inline

    #import matplotlib
    from matplotlib import pyplot as plt

    #create a bar plot of names vs their corresponding grade
    plt.bar(x=df_students.Name, height=df_students.Grade)

    #display the plot
    plt.show()

}
```

The pyplot class was used here to plot our chart, but there are still some issues that are to be noted. We can now change  

* Color
* Title
* X and Y Axis labels
* Grid
* Rotate Axis

So let's customize our chart  

```Python
{

    plt.title('Student Grades')
    plt.xlabel('Student')
    plt.ylabel('Grade')
    plt.grid(color='ffa4b6', linestyle='--', linewidth=2, axis='y', alpha=0.7)
    plt.xticks(rotation=90)

    #display our plot
    plt.show()


}
```

```Python
{

    # Create a bar plot of name vs grade
    plt.bar(x=df_students.Name, height=df_students.Grade, color='orange')

    # Customize the chart
    plt.title('Student Grades')
    plt.xlabel('Student')
    plt.ylabel('Grade')
    plt.grid(color='#ffa4b6', linestyle='--', linewidth=2,  axis='y', alpha=0.7)
    plt.xticks(rotation=90)

    # Display the plot
    plt.show()

}
```

We can also specify the size of our plot from the beginning by adding this in our constructor 

`fig = plt.figure(figsize=(8, 3))`


In addition to this plot we can also create subplots to visualize what we have done in another manner. In this case we can take both our bar chart as well as a pie chart.  

```Python
{

    # Create a figure for 2 subplots (1 row, 2 columns)
    fig, ax = plt.subplots(1, 2, figsize = (10,4))

    # Create a bar plot of name vs grade on the first axis
    ax[0].bar(x=df_students.Name, height=df_students.Grade, color='orange')
    ax[0].set_title('Grades')
    ax[0].set_xticklabels(df_students.Name, rotation=90)

    # Create a pie chart of pass counts on the second axis
    pass_counts = df_students['Pass'].value_counts()
    ax[1].pie(pass_counts, labels=pass_counts)
    ax[1].set_title('Passing Grades')
    ax[1].legend(pass_counts.keys().tolist())

    # Add a title to the Figure
    fig.suptitle('Student Data')

    # Show the figure
    fig.show()

}
```

Matplotlib is one of the most fundamental libraries that Python offers. Therefore, a lot of other libraries tend to use it within their own methods. Panda is no exception to this and can be used during plotting.

`df_students.plot.bar(x='Name', y-'Students', color='teal', figsize=(6, 4))`

---

# Statistical Analysis

So, now that we see our data visually we can begin to understand it. This comes down to some basic statistical analysis skills. 

How can we use our basic visual understanding here?  

## Data Distribution

One main thing to look at when representing your data is the *distribution* of data. The best place to start would be to see a histogram which allows us to easily visualize the **mode** of our data.

```Python
{

    #variable to examine
    var_data = df_students['Grade']

    #create the figure
    fig = plt.figure(figsize=(10, 4))

    #plot a histogram
    plt.hist(var_data)

    #add titles and labels
    plt.title('Data Dist')
    plt.xlabel('Val')
    plt.ylabel('Freq')

    #plot the figure
    fig.show()

}
```


This will now show the end user a histogram with the most frequent grade being the highest pillar. This is why we chose a histogram (for its simplicity).

It may have been a while since you took a basic class on statistics, or you may be a master of it but we will go over some simple things to refresh.  

* **Mean**: Average of data, the total amount of data divided by how many items that were involved
* **Median**: The middle value within your data when placed in order (least to greatest or greatest to least)
* **Mode**: The most common data point within your set  


```Python
{

    # Get the variable to examine
    var = df_students['Grade']

    # Get statistics
    min_val = var.min()
    max_val = var.max()
    mean_val = var.mean()
    med_val = var.median()
    mod_val = var.mode()[0]

    print('Minimum:{:.2f}\nMean:{:.2f}\nMedian:{:.2f}\nMode:{:.2f}\nMaximum:{:.2f}\n'.format(min_val, mean_val, med_val, mod_val, max_val))

    # Create a Figure
    fig = plt.figure(figsize=(10,4))

    # Plot a histogram
    plt.hist(var)

    # Add lines for the statistics
    plt.axvline(x=min_val, color = 'gray',  linestyle='dashed', linewidth = 2)
    plt.axvline(x=mean_val, color = 'cyan',     linestyle='dashed', linewidth = 2)
    plt.axvline(x=med_val, color = 'red', linestyle='dashed',   linewidth = 2)
    plt.axvline(x=mod_val, color = 'yellow',    linestyle='dashed', linewidth = 2)
    plt.axvline(x=max_val, color = 'gray',  linestyle='dashed', linewidth = 2)

    # Add titles and labels
    plt.title('Data Distribution')
    plt.xlabel('Value')
    plt.ylabel('Frequency')

    # Show the figure
    fig.show()

}
```

We can also visualize our data through what is usually referenced as a *box and whiskers plot* and can show us our outliers as well as better distribution of our variables

```Python
{

    #gather vars to examine
    var = df_students['Grade']

    #create the figure
    fig = plt.figure(figsize=(10, 4))

    #plot histogram
    plt.boxplot(var)

    #add title
    plt.title('Data Dist')

    #show the figure
    fig.show()

}
```

It's often useful to combine histograms and box plots, with the box plot's orientation changed to align it with the histogram (in some ways, it can be helpful to think of the histogram as a "front elevation" view of the distribution, and the box plot as a "plan" view of the distribution from above.)


```Python
{

    # Create a function that we can re-use
    def show_distribution(var_data):
        from matplotlib import pyplot as plt

        # Get statistics
        min_val = var_data.min()
        max_val = var_data.max()
        mean_val = var_data.mean()
        med_val = var_data.median()
        mod_val = var_data.mode()[0]

        print('Minimum:{:.2f}\nMean:{:.2f}\nMedian:{:.2f} \nMode:{:.2f}\nMaximum:{:.2f}\n'.format(min_val, mean_val, med_val, mod_val, max_val))


        # Create a figure for 2 subplots (2 rows, 1 column)
        fig, ax = plt.subplots(2, 1, figsize = (10,4))

        # Plot the histogram   
        ax[0].hist(var_data)
        ax[0].set_ylabel('Frequency')

        # Add lines for the mean, median, and mode
        ax[0].axvline(x=min_val, color = 'gray',    linestyle='dashed', linewidth = 2)
        ax[0].axvline(x=mean_val, color = 'cyan',   linestyle='dashed', linewidth = 2)
        ax[0].axvline(x=med_val, color = 'red',     linestyle='dashed', linewidth = 2)
        ax[0].axvline(x=mod_val, color = 'yellow',  linestyle='dashed', linewidth = 2)
        ax[0].axvline(x=max_val, color = 'gray',    linestyle='dashed', linewidth = 2)

        # Plot the boxplot   
        ax[1].boxplot(var_data, vert=False)
        ax[1].set_xlabel('Value')

        # Add a title to the Figure
        fig.suptitle('Data Distribution')

        # Show the figure
        fig.show()

    # Get the variable to examine
    col = df_students['Grade']
    # Call the function
    show_distribution(col)

}
```

The descriptive statistics we've used to understand the distribution of the student data variables are the basis of statistical analysis; and because they're such an important part of exploring your data, there's a built-in **Describe** method of the DataFrame object that returns the main descriptive statistics for all numeric columns.

`df_students.describe()`


---

# Comparing Data

Now that we can see our data, we need to know how to find relationships between different data points within our analysis. 

We want to remove outliers within our data points and from beginning analysis we already know where they are. So, we can go back to what we know from **Panda** and remove them  

```Python
df_sample = df_students[df_students['StudyHours']>1]
df_sample #display data set
```

## Comparing Numerical and Categorical Values

Here we want to compare the amount of time studied to grade, while also knowing the name of the student as well as if whether or not they passed.  

To make this we need to create our first boxplot  

`df_sample.boxplot(column='StudyHours', by='Pass', figsize(8, 5))`

Comparing the data that we find within this graph it shows that the students who studied more tended to do a lot better on their exam (which would confirm most suspicion)

## Compare Numeric Data

Let's compare the grades and StudyHours together to really see how the the students did and learn how much our students should study for our exams to pass.  

```Python
#create bar plot of name vs grade and study hours
df_sample.plot(x='Name', y=['Grade','StudyHours'], kind='bar', figsize(8, 5))
```

The chart shows bars for both grade and study hours for each student; but it's not easy to compare because the values are on different scales. Grades are measured in grade points, and range from 3 to 97; while study time is measured in hours and ranges from 1 to 16.

A common technique when dealing with numeric data in different scales is to *normalize* the data so that the values retain their proportional distribution, but are measured on the same scale. To accomplish this, we'll use a technique called *MinMax* scaling that distributes the values proportionally on a scale of 0 to 1. You could write the code to apply this transformation; but the **Scikit-Learn** library provides a scaler to do it for you.

```Python
{

    from sklearn.preprocessing import MinMaxScaler

    # Get a scaler object
    scaler = MinMaxScaler()

    # Create a new dataframe for the scaled values
    df_normalized = df_sample[['Name', 'Grade', 'StudyHours']].copy()

    # Normalize the numeric columns
    df_normalized[['Grade','StudyHours']] = scaler.fit_transform(df_normalized[['Grade','StudyHours']])

    # Plot the normalized values
    df_normalized.plot(x='Name', y=['Grade','StudyHours'], kind='bar', figsize=(8,5))

}
```

Though it is not totally clear and representative of grade being 100% controlled by the amount of time spent studying. Their relationship is clearly apparent.  

We can use another method to quantify this relationship between the two  

`df_normalize.Grade.corr(df_normalized.StudyHours)`

The value that we get here will show a correlation that is between the values of -1 and 1. A value just above zero or at zero would show a small positive correlation. here we achieve a correlation of 0.9117 which is a strong correlation between the two data points.  

Remember the difference between correlation and causation. Just because these two are similar and very much correlated does not mean that studying more will increase a students score (in this case it does).


## Scatter Plot

`df_sample.plot.scatter(title='Study Time vs Grade', x='StudyHours', y='Grades')`

Here we will also see this positive correlation as we reach the greater amount of time spent studying increased the overall achieved score of the students.

By finding the line of best fit from this data and regression analysis we can locate which function correlated with the grades. From this we can determine what your average score would be from any time spent studying.  


Fortunately, you don't need to code the regression calculation yourself - the **SciPy** package includes a **stats** class that provides a **linregress** method to do the hard work for you. This returns (among other things) the coefficients you need for the slope equation - slope (*m*) and intercept (*b*) based on a given pair of variable samples you want to compare.

```Python

from scipy import stats

#
df_regression = df_sample[['Grade', 'StudyHours']].copy()

# Get the regression slope and intercept
m, b, r, p, se = stats.linregress(df_regression['StudyHours'], df_regression['Grade'])
print('slope: {:.4f}\ny-intercept: {:.4f}'.format(m,b))
print('so...\n f(x) = {:.4f}x + {:.4f}'.format(m,b))

# Use the function (mx + b) to calculate f(x) for each x (StudyHours) value
df_regression['fx'] = (m * df_regression['StudyHours']) + b

# Calculate the error between f(x) and the actual y (Grade) value
df_regression['error'] = df_regression['fx'] - df_regression['Grade']

# Create a scatter plot of Grade vs Salary
df_regression.plot.scatter(x='StudyHours', y='Grade')

# Plot the regression line
plt.plot(df_regression['StudyHours'],df_regression['fx'], color='cyan')

# Display the plot
plt.show()
    
```

## Predictions

Now that regression co-effecients have been established, we can take time to understand them and place them within a function for given amount of study time.

```Python
# Define a function based on our regression coefficients
def f(x):
    m = 6.3134
    b = -17.9164
    return m*x + b

study_time = 14

# Get f(x) for study time
prediction = f(study_time)

# Grade can't be less than 0 or more than 100
expected_grade = max(0,min(100,prediction))

#Print the estimated grade
print ('Studying for {} hours per week may result in a grade of {:.0f}'.format(study_time, expected_grade))

```

This is a basic example of machine learning where we can take this sample set of data and learn how to use it and analyze it within our whole function giving the end user plenty of features to work with and understand.


