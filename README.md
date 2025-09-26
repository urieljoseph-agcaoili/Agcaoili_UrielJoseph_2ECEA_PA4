# Agcaoili_UrielJoseph_2ECEA_PA4

# ECE2112

The codes made for this project was created using the coding software python.

## Dependencies
For this code to work the file "board2.csv" is needed.

## Installation
This code can only read the needed .csv files when the coding files and .csv file are in one folder.

## ECE BOARD EXAM PROBLEM
Using data wrangling and data visualization technique withstorytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.
Create the following data frames based on the format provided:
a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon
b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?

## Code Process:

This line of code is used to import pandas which is used to create, analyse, and manipulate data.
```python
import pandas as pd   #Imports pandas as pd into the code
```

This line of code is used to read and import a .csv into the code which will be analyzed and manipulated. The code used to read and import a .csv file is "pd.read_csv()", in this case the file to be read is "board2.csv".
```python
boardexams = pd.read_csv('board2.csv')   #Finds and reads file "board2.cs" then stores it into data frame "boardexams"
boardexams    #Displays the data frame "boardexams"
```

This line of code functions to locate elements "Instrumentation", "Luzon", and grades from "electronics" higher than 70 which were located from the columns "Track", "Hometown", and "Electronics". The code then takes the columns "Name", "GEAS", and "Electronics" from the data frame and store it into a new data frame named "Instru". The code used to accomplish this task is "boardexams.loc[]", while the statements inside the brackets are for locating the different elements in the data frame. The data frame is then displayed to be seen by the user.
```python
Instru = boardexams.loc[(boardexams['Track'] == 'Instrumentation') & (boardexams['Hometown'] == 'Luzon') & (boardexams['Electronics'] > 70), ['Name', 'GEAS', 'Electronics']]   #Locates variables whose track is "Intrumentation", hometown is in "Luzon" and grade in "Electronics" is higher then 70, then takes the name, grade in "GEAS" and "Electronics" and was then stored in "Instru" as a new data frame

Instru   #Displays data frame "Instru"
```

For this line of code a the average grade of the students would be taken and a new column called "Average" is created to store this new data into the data frame. To get the average of the grades the code "boardexams[].mean(axis=1)" was used, wehere we put the columns "Math", "Electronics", "GEAS", and "Communication" inside the bracket so we can take the elements from each columns and take their mean. The average taken was then put into a new column in the data frame which was created using the code "boardexams['Average']".
```python
boardexams['Average'] = boardexams[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)   #Takes the mean of all grades then stores it in a new column in the data frame.
```

In this line of code we locate the elements "Female", "Mindanao", and average grades that are equal to or higher than 55, these elements are located from their respective columns "Gender", "Hometown", and "Average". The code then takes the columns "Name", "Track", "Electronics", and "Average" then stores it into a new data frame named "Mindy". For the code to do this task we use the code "boardexams.loc[]", while the statements inside the brackets are used to locate the different elements needed for the data frame. The new data frame is then displayed for the user to see.
```python
Mindy = boardexams.loc[(boardexams['Gender'] == 'Female') & (boardexams['Average'] >= 55), ['Name', 'Track', 'Electronics', 'Average']]   ##Locates variables whose gender is "Female", average is equal or greater than 55 then takes the name, track, grade in "Electronics" and their average and was then stored in "Mindy" as a new data frame

Mindy   #Displays data frame "Mindy"
```

This line of code is used to import matplotlib which is used to create and customize graphs for data frames.
```python
import matplotlib.pyplot as plt   #Imports matplotlib as plt into the code
```

This line of code takes the mean of the columns "Track" and "Average" in the data frame using code "boardexams.groupby" amd ".mean", which groups the two columns then takes their mean. The result is then stored in "track_avg".
```python
track_avg = boardexams.groupby('Track')['Average'].mean()   #Groups "Track" and "Average" and takes their mean, then stores the data into "track_avg"
```

This lines of codes are written to create a bar graph with the data from "track_avg". For the first line of code we create a base figure for the graph that is 8 by 5. The next code inputs the data from the "track_avg" and sets the color of the bars in the bar graph to "lightgreen". For codes "plt.title", "plt.xlabel", and "plt.ylabel" we put a title on the bar graph and labels for the x and y axis of the graph. The code "plt.xticks" rotates the labels in the x-axis to 45 degrees, this was done for this bra graph so the lables would be readable. For the next line of code it simply makes the sub plots in the graph fit. In the next line of code grid lines are added in the y-axis of the bar graph. The completed bar graph is then shown to the user.
```python
plt.figure(figsize=(8, 5))   #Creates a figure that has a size of 8 by 5
plt.bar(track_avg.index, track_avg.values, color='lightgreen')   #Sets the figure into a bar graph where the bars in in the graph is colored "lightgreen" and uses the data from "track_avg"
plt.title('Average Grades by Track')   #Sets the title of the graph into "Average Grades by Track"
plt.xlabel('Track')   #Labels the x-axis of the graph as "Track"
plt.ylabel('Average Grade')   #Labels the y-axis of the graph as "Average Grade"
plt.xticks(rotation=45)   #Rotates the label for the x-axis by 45 degrees
plt.tight_layout()   #Makes sure the sub plots fits in the graph
plt.grid(axis='y', linestyle='--', alpha=0.5)   #Puts grid lines in the y-axis with a linestyle "--" and line thickness of 0.5
plt.show()   #Displays the graph "track_avg"
```

This line of code takes the mean of the columns "Gender" and "Average" in the data frame using code "boardexams.groupby" amd ".mean", which groups the two columns then takes their mean. The result is then stored in "gender_avg".
```python
gender_avg = boardexams.groupby('Gender')['Average'].mean()   #Groups "Gender" and "Average" and takes their mean, then stores the data into "gender_avg"
```

This lines of codes are written to create a bar graph with the data from "gender_avg". For the first line of code we create a base figure for the graph that is 6 by 4. The next code inputs the data from the "gender_avg" and sets the color of the bars in the bar graph to "salmon". For codes "plt.title", "plt.xlabel", and "plt.ylabel" we put a title on the bar graph and labels for the x and y axis of the graph. In the next line of code grid lines are added in the y-axis of the bar graph For the next line of code it simply makes the sub plots in the graph fit. The completed bar graph is then shown to the user.
```python
plt.figure(figsize=(6, 4))   #Creates a figure that has a size of 6 by 4
plt.bar(gender_avg.index, gender_avg.values, color='salmon')   #Sets the figure into a bar graph where the bars in in the graph is colored "salmon" and uses the data from "gender_avg"
plt.title('Average Grades by Gender')   #Sets the title of the graph into "Average Grades by Gender"
plt.xlabel('Gender')   #Labels the x-axis of the graph as "Gender"
plt.ylabel('Average Grade')   #Labels the y-axis of the graph as "Average Grade"
plt.grid(axis='y', linestyle='--', alpha=0.5)   #Puts grid lines in the y-axis with a linestyle "--" and line thickness of 0.5
plt.tight_layout()   #Makes sure the sub plots fits in the graph
plt.show()   #Displays the graph "gender_avg"
```

This line of code takes the mean of the columns "Hometown" and "Average" in the data frame using code "boardexams.groupby" amd ".mean", which groups the two columns then takes their mean. The result is then stored in "home_avg".
```python
home_avg = boardexams.groupby('Hometown')['Average'].mean()   #Groups "Hometown" and "Average" and takes their mean, then stores the data into "track_avg"
```

This lines of codes are written to create a bar graph with the data from "home_avg". For the first line of code we create a base figure for the graph that is 6 by 4. The next code inputs the data from the "home_avg" and sets the color of the bars in the bar graph to "skyblue". For codes "plt.title", "plt.xlabel", and "plt.ylabel" we put a title on the bar graph and labels for the x and y axis of the graph. In the next line of code grid lines are added in the y-axis of the bar graph. For the next line of code it simply makes the sub plots in the graph fit. The completed bar graph is then shown to the user.
```python
plt.figure(figsize=(6, 4))   #Creates a figure that has a size of 6 by 4
plt.bar(home_avg.index, home_avg.values, color='skyblue')   #Sets the figure into a bar graph where the bars in in the graph is colored "salmon" and uses the data from "home_avg"
plt.title('Average Grades by Hometown')   #Sets the title of the graph into "Average Grades by Hometown"
plt.xlabel('Hometown')   #Labels the x-axis of the graph as "Hometown"
plt.ylabel('Average Grade')   #Labels the y-axis of the graph as "Average Grade"
plt.grid(axis='y', linestyle='--', alpha=0.5)    #Puts grid lines in the y-axis with a linestyle "--" and line thickness of 0.5
plt.tight_layout()   #Makes sure the sub plots fits in the graph
plt.show()   #Displays the graph "track_avg"
```

## Version:
* 0.2 - readme file format was editted.
* 0.1 - initial code and readme file.

## Author
Uriel Joseph T. Agcaoili
