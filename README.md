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









