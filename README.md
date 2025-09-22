# Agcaoili_UrielJoseph_2ECEA_PA4

# ECE2112

ECE BOARD EXAM PROBLEM

```python
import pandas as pd   #Imports pandas as pd into the code

boardexams = pd.read_csv('board2.csv')   #Finds and reads file "board2.cs" then stores it into data frame "boardexams"
boardexams    #Displays the data frame "boardexams"

Instru = boardexams.loc[(boardexams['Track'] == 'Instrumentation') & (boardexams['Hometown'] == 'Luzon') & (boardexams['Electronics'] > 70), ['Name', 'GEAS', 'Electronics']]   #Locates variables whose track is "Intrumentation", hometown is in "Luzon" and grade in "Electronics" is higher then 70, then takes the name, grade in "GEAS" and "Electronics" and was then stored in "Instru" as a new data frame

Instru   #Displays data frame "Instru"

boardexams['Average'] = boardexams[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)   #Takes the mean of all grades then stores it in a new column in the data frame.

Mindy = boardexams.loc[(boardexams['Gender'] == 'Female') & (boardexams['Average'] >= 55), ['Name', 'Track', 'Electronics', 'Average']]   ##Locates variables whose gender is "Female", average is equal or greater than 55 then takes the name, track, grade in "Electronics" and their average and was then stored in "Mindy" as a new data frame

Mindy   #Displays data frame "Mindy"

import matplotlib.pyplot as plt   #Imports matplotlib as plt into the code

track_avg = boardexams.groupby('Track')['Average'].mean()   #Groups "Track" and "Average" and takes their mean, then stores the data into "track_avg"

plt.figure(figsize=(8, 5))   #Creates a figure that has a size of 8 by 5
plt.bar(track_avg.index, track_avg.values, color='lightgreen')   #Sets the figure into a bar graph where the bars in in the graph is colored "lightgreen" and uses the data from "track_avg"
plt.title('Average Grades by Track')   #Sets the title of the graph into "Average Grades by Track"
plt.xlabel('Track')   #Labels the x-axis of the graph as "Track"
plt.ylabel('Average Grade')   #Labels the y-axis of the graph as "Average Grade"
plt.xticks(rotation=45)   #Rotates the label for the x-axis by 45 degrees
plt.tight_layout()   #Makes sure the sub plots fits in the graph
plt.grid(axis='y', linestyle='--', alpha=0.5)   #Puts grid lines in the y-axis with a linestyle "--" and line thickness of 0.5
plt.show()   #Displays the graph "track_avg"

gender_avg = boardexams.groupby('Gender')['Average'].mean()   #Groups "Gender" and "Average" and takes their mean, then stores the data into "gender_avg"

plt.figure(figsize=(6, 4))   #Creates a figure that has a size of 6 by 4
plt.bar(gender_avg.index, gender_avg.values, color='salmon')   #Sets the figure into a bar graph where the bars in in the graph is colored "salmon" and uses the data from "gender_avg"
plt.title('Average Grades by Gender')   #Sets the title of the graph into "Average Grades by Gender"
plt.xlabel('Gender')   #Labels the x-axis of the graph as "Gender"
plt.ylabel('Average Grade')   #Labels the y-axis of the graph as "Average Grade"
plt.grid(axis='y', linestyle='--', alpha=0.5)   #Puts grid lines in the y-axis with a linestyle "--" and line thickness of 0.5
plt.tight_layout()   #Makes sure the sub plots fits in the graph
plt.show()   #Displays the graph "gender_avg"

home_avg = boardexams.groupby('Hometown')['Average'].mean()   #Groups "Hometown" and "Average" and takes their mean, then stores the data into "track_avg"

plt.figure(figsize=(6, 4))   #Creates a figure that has a size of 6 by 4
plt.bar(home_avg.index, home_avg.values, color='skyblue')   #Sets the figure into a bar graph where the bars in in the graph is colored "salmon" and uses the data from "home_avg"
plt.title('Average Grades by Hometown')   #Sets the title of the graph into "Average Grades by Hometown"
plt.xlabel('Hometown')   #Labels the x-axis of the graph as "Hometown"
plt.ylabel('Average Grade')   #Labels the y-axis of the graph as "Average Grade"
plt.grid(axis='y', linestyle='--', alpha=0.5)    #Puts grid lines in the y-axis with a linestyle "--" and line thickness of 0.5
plt.tight_layout()   #Makes sure the sub plots fits in the graph
plt.show()   #Displays the graph "track_avg"
```
