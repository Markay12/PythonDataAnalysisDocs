# Python Data Analysis

## Introduction

What is data analysis?  
- Data analysis involves exploring, representing and understanding data. Whether this is large amounts of data (big data) or small amounts such as a local project, data anaylsis can be conducted in many forms.

One major use of data analysis comes with *machine learning* which is a 

> subset of data that deals with predictive modeling
- Microsoft 

This uses data we have found to create models that can predict values or future outcomes

Data that is collected from this analysis can be used in many situations that benefit the greater public by finding the best ways to teach and accomodate to others. By learning the best methods of everyday tasks we can better optimize our lives.


## Data Analysis - First Dive

Analysis of data is usually done in what is called an *iterative* process which allows the scientist to analysis and test hypotheses along the way learning from what they are collecting

Their main concern is with finding ways to explore, visualize and manipulate the data they are given. Finding the best way to represent this data can lead to better results and a stronger understanding

First we must begin with where to start with understanding the data that we are collecting and where to place it as we are collecting it.  
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
What we have done here is taken our data and placed it into a basic array. While this is greate for manipulation of the data, there are better ways to do this with NumPy.  

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

The first one in this instance multiplies the length of the array by two creating a new list that is twice the length of the original. Where as the second multiplication goes through the list just as a vector and results in the same length array with each element being multiplied by two.  

### Multiple Dimension Arrays
```Python
{

    grades.shape

    # This will return the shape of the array being 22 in length with no columns
    # OUTPUT: (22,)

}
```

To access the first element we would do this in the same way as many other programming languages with the first element beginning at index 0.   

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

Now we have a two dimensional array which puts these two data sets right next to each other  

Let's take a look at the shape of our data set! 

`student_data.shape`  

Output: (2, 22) 

Now, what do these two numbers mean? The first number 2 represents that the data array contains two elements (study_hours, grades) and the 22 represents both arrays containing 22 elements each  

If you're the inquisitive type, like myself... what happens when there are two arrays that aren't the same size?  
- The output will just tell you that there are two elements (2,)
  

So, how do we navigate through this data? Just like when we were navigating the first array, the index begins at 0 and we specify based off how we input the elements initially. `student_data = np.array([study_hours, grades])`

So lets find the first element of the first data set

```Python
{

    student_data[0][0]

}
```

This will give us the output of 10.0 which is the first input for our *study_hours* data set. So how does the avereage of the first array compare to the average of the second array?  

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

So, how does loc work with columns? **loc** is used to located data items vased on index rather than positions. In absence of index the rows in the DataFrame are indexed as integer values

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

Just think... you are at the end of your research, you have most of your data but there are some holes that you are missing which cannot be filled by collected data. What do we do?  

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


# So what does our Data Say?

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

So what if anyone in the class needs a 70 to pass? Well, we can use Panda again to declare whether someone had passed or failed. We can just add this to our list as a new column. 

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














