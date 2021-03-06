# Final Project Proposal

**GitHub Repo URL**: **[https://github.com/CMU-IDS-2022/final-project-the-evaluators](https://github.com/CMU-IDS-2022/final-project-the-evaluators)**

## Team Name: The Evaluators 



* Jingyi (Jenny) Song
* Tadpol Rachatasumrit
* Princy Sasapara
* Urvish Thakker


---


## **Description**

**Domain**: University Course Evaluations

**Stakeholders**: Students, Course Instructors, Department Heads


## **Research Question**:



* How to equip students with all the required knowledge to make an informed decision while selecting university courses and planning their semester? 
* How to help them compare different courses based on different criterias like course goals, instructor’s feedback, student reviews, courseload etc?
* How to equip instructors and university department heads to easily view, analyze and understand the course quality, and criterias to improve?


## **Ideas：**



* Search and filter the courses.
* Compare courses.
    * Overall data visualization of the selected courses.
    * Head to head courses comparison.
    * The data can be compared by: _Hrs per week, Interest in student learning, clearly explain course requirements, clear learning objectives goals, instructor provides feedback to students to improve, explains subject matter of course, show respect for all students _
* Visualize the progress of each course through years. 
    * Many courses have been offered for many years, some of them are getting better score, some of them might get worse. By visualizing the progress of the course, we can see the trend of the course, and how well each professor does.



## **Data**

The data will be exported from CMU’s Faculty Course Evaluations (FCE) website.  

Link to FCE website: **[https://mwfo3.smartevals.com/Reporting/Students/Wizard.aspx?Type=Sections&FiveYearsOnly=True](https://mwfo3.smartevals.com/Reporting/Students/Wizard.aspx?Type=Sections&FiveYearsOnly=True)**

## **Data Exploration**

Do you have to do substantial data cleanup? What quantities do you plan to derive from your data? How will data processing be implemented?  Show some screenshots of your data to demonstrate you have explored it.

We downloaded our data from CMU Smartevals Website. The data was available for download in CSV Format and the data was quite structured. It did not require significant cleaning effort.

We did some exploratory data analysis on the data such as plotting features and their descriptions. Also, calculating some basic statistics about all the numerical features. Moreover, we plotted some interesting graphs such as course rating v/s instructor rating. We plotted graphs about overall course rating vs their count in the overall dataset. It was surprising to see that the majority of the ratings are 5 like perfect ratings. 

We are planning to derive metrics such as response percentage based on the total no of students and no of students responded to the survey. Also, derive top 5 departments having average highest rating for their courses. Also derive trends such as top 5 instructors and top courses. We are looking to adapt metrics such as course_load percentage such as if a course units is 12 units and it requires 20 hr/week of work, its course_load percentage would be 20/12 = 1.67

We Converted our CSV File into Pandas Dataframe and printed it.

![excel_df](https://user-images.githubusercontent.com/91555752/163653427-03306515-9d98-4310-b772-9fe50e5f3023.png)

![unnamed](https://user-images.githubusercontent.com/91555752/163653602-35a62fbc-09cc-45f1-93f0-d78645625bf2.png)

We printed the shape of our dataframe, information about our dataframe in order to get an idea about how the dataset is and how it is distributed. 

![EDA_Basic_Statistics](https://user-images.githubusercontent.com/91555752/163653569-81710f67-7d41-4b2b-aa24-f2c18ef27669.jpg)

![unnamed (1)](https://user-images.githubusercontent.com/91555752/163653662-65b2a147-3dbf-4b58-a213-94409a65d204.png)

Apart from understanding our data parameters and variables in our data frame, we try to grasp an idea of how our data features are and what type they are stored as in the dataframe.

We also plot some intuitive exploratory data analysis graph and visualization to get a hang of our data.

![EDA_Bar_graph](https://user-images.githubusercontent.com/91555752/163653684-e68ee5a2-4365-4570-9609-baedc9dc91a8.jpg)

![Figure 2022-04-15 182856](https://user-images.githubusercontent.com/91555752/163653691-102763f8-4642-4f69-8899-7f7eeced02b2.png)

![unnamed (2)](https://user-images.githubusercontent.com/91555752/163653704-8b1c8b01-9317-4979-9978-6444800c0064.png)


## **System Design and Visualizations**


<img width="517" alt="Screen Shot 2022-04-15 at 7 20 24 PM" src="https://user-images.githubusercontent.com/51781106/163651920-3aa0fe7b-fcf5-4fb3-a513-51d2c5e616d9.png">

### Compare Course Rating

The goal of these visualizations is to help users decide which courses to take among the courses they are interested in. There will be three components for this part:

1. Search Panel
   Users can search for the courses they want to compare in these visualizations.
2. Latest Year Compare - Compare only the latest year ratings of each course.
   * Type: Bar chart
   * Encoding:
      * x-axis: rating type
      * y-axis: rating value
      * color: course
   * Interaction:
      * Users can select the ratings they want to compare from the list aside from the graph.
3. Rating Over Time - Compare one rating over time.
   * Type: Line graph
   * Encoding:
      * x-axis: date
      * y-axis: rating value
      * color: course
      * line type: instructor
   *Interaction:
      * Users can select a rating they want to compare from the dropdown menu.

<img width="506" alt="Screen Shot 2022-04-15 at 7 37 42 PM" src="https://user-images.githubusercontent.com/51781106/163652788-160689f5-5bc0-4d13-9831-11a6b63f0aed.png">



### Course Rating vs Teacher Rating
These visualizations aim to give an overview of CMU course ratings. There will be 2 visualizations:

1. Overall Teacher Rate X Overall Course Rate 
   * Type: Scatter plot
   * Encoding:
      * x-axis: Overall Course Rating
      * y-axis: Overall Teacher Rating
      * color: Department
      * size: Hrs per week
      * circle: Course
    * Interaction:
      * Filter courses by department - users can filter to see only the list of departments they want by checking the checkboxes on the side.

2. Hrs. Per Week
   * Type: 1-axis scatter plot
   * Encoding:
      * x-axis: Hrs per week
      * color: department (same as the first visualization)
   * Interaction
      * Brush filter - users can brush the graph to filter only the range “hrs per week” they want to focus on. The filter will be applied to the first 
<img width="486" alt="Screen Shot 2022-04-15 at 7 38 17 PM" src="https://user-images.githubusercontent.com/51781106/163652791-bd509da3-fae9-4b4e-80bd-0fbd53e36af3.png">

3. Hrs per Week panel
This visualization will show the sum amount of “hrs per week of the selected courses”. The goal of this visualization is to show the commitment (hrs per week) they will have to give if they decide to register for all the selected courses. This visualization will be on the fixed panel so that the users will always see it.
   * Type: 1-axis bar chart.
   * Encoding:
      * x-axis: sum of “hrs per week”
      * color: Courses


<img width="347" alt="Screen Shot 2022-04-15 at 7 38 37 PM" src="https://user-images.githubusercontent.com/51781106/163653257-4bac3b44-940c-47c5-ad0e-4c5505aaae9a.png">




