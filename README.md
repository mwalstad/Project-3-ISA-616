# "Staying the Course: Factors Influencing Business Analytics Retention"

## Overview of Repository

The purpose of this repository is to interact with GitHub to access the files for Project 3. 

## Contributors

Max Lippman, Marti Walstad, Jenna Sayle, Alaina Edwards

## Research Questions

There is difficulty forecasting the number of students in a Business Analytics program resulting in challenges with class size planning. We look to answer these questions: 
	(1) Historically, what characteristics define students who stay with a Business Analytics program? 
	(2) Is there a pattern to the number of students staying or leaving a Business Analytics program?
	(3) What courses have a significant impact on whether students stay with the business analytics major?

## Business Value Proposition

Client:

-   Skip Benamati Professor and chair of the Information Systems &
    Analytics along with his staff including Alan Clift (Data and
    planning Analyst) and Professor, Alison Jones-Farmer. 

Jobs:

-   Accurately predict demand for classes

-   Understand the flow of students in and out of Business Analytics
    major

Pains:

-   Before:

    -   Abundance of BA majors who end up dropping

-   During:

    -   Student retention -- understanding characteristics of students
        who stay and do not stay with the BA major

    -   Understanding what students are switching to the BA major

    -   If BA courses have an impact on whether students stay in
        business analytics

-   After:

    -   Over offering classes (results in too many small sized classes)

Solution:

-   Time series analysis and prediction of future enrollment for the next two semesters. A predictive model to determine is a student will drop or stay in their program. 

Pain Killers:

-   Identify key characteristics of students who leave the major

-   Identify classes that may need curriculum change in order to retain
    my students

-   Understand why students switch to the BA major and what majors they
    come from

Gains:

-   Confidence promoting program

-   Pipeline of students from advising

-   Use for other majors (ISA)

Gain Creators:

-   Advice tailored to the results on how to better market the BA
    program

-   Resources for advising that help identify prospective BA students


## Overview of Analysis

In this document, we analyzed data from Miami University’s Farmer School of Business student data from fall 2018 to fall 2023 school years, provided by clients Alan Clift and Skip Benamati. This data included students who were enrolled in any Business Analytics program during their time at Miami. Programs include the Business Analytics Major, Minor, and ISA2 thematic sequence. We used a random forest model to predict whether a student enrolled in the Business Analytics program would eventually drop based on the features of our model. We used a binary “flagging” target variable (column with 1 or 0) to denote if they left their program or not (1= leave, 0 = stay) at any time. Furthermore, we utilized portions of the student data, organized by program type, to conduct descriptive analysis on trends related to enrollment to support our analysis of answering the research questions above.


## Data Sources

### Files Used
* Attributes.csv: renamed to studentinfo, this file identifies an individual student in a business analytics program by a Student.ID and columns include student information including their gender, first generation status, cumulative GPA, and term code. Each student has a row for every term they have been enrolled. We dropped the index column called X.

* BA_Majors.csv: renamed to studentlist is similar to Attributes in which it identifies the student by Student.ID with a row for every term they have been enrolled at Miami. It also includes their cohort, and major (with a column for 3 potential majors. We dropped the index column called X and the Enrolled Student Count column because they were not important to our analysis.

* BA Major Students - Minors.xlsx: This file was renamed to minors and includes a table of students who were classified as Business Analytics minors along with a row for each term they were enrolled at Miami. It was given to us as in the raw data folder and we had to unmerge and populate cells to use it as a table in our analysis. The file included the count of enrolled students by term which we displayed as a bar graph.The table also includes a column for their cohort which is their freshman semester at Miami. We renamed columns to match the other tables with the same columns and dropped unnecessary columns like Enrolled Student Count. 

* BA Major Students - Thematic Sequence ISA2.xlsx: Renamed to thematic, this table represents all of the students who had at one point been enrolled in the business analytics thematic sequence titled "ISA2 Applied Business Statistics".  It was given to us as in the raw data folder and we had to unmerge and populate cells to use it as a table in our analysis. Like the other tables, this one includes Student.ID, Term.Code as well as the thematic sequence title.

* Grades.xlsx - This includes a row for each the class the student took along with their StudentID, Term.Code, and grade result. Unimportant columns were dropped, and other columns renamed to match previous tables. The grade data was merged into thefile that was created by combining the previous four files. 

* Thematic Sequence.csv - This file was used in our time series analysis to graph the number of students enrolled in the ISA2 Applied Business Statistics Thematic Sequence. The file included the count of enrolled students by term which we displayed as a bar graph.

* BA Minors.xlsx - This file was used in our time series analysis to graph the number of students enrolled in the Business Analytics Minor over time. It was given to us as in the raw data folder. The file included the count of enrolled students by term which we displayed as a bar graph.

### Variables in cleaned dataset, "StudentData_withFlag"

- "Student.ID" = unique identifier for students
- "Term.Code" = Term denoted as the Year + Semester(10=Fall, 20=Spring)
- "Gender" = Student gender noted as Male (M) or Female (F)
- "First.Generation.Indicator" = Student is a first generation student
- "Cum.UG.Crs.GPA" = Studnet's cumulative GPA as of that Term
- "Cohort.Term" = The student's first semester of enrollment
- "Major.1" = The major that the student declared first
- "Major.2" = The major that the student declared second
- "Major.3" = The major that the student declared third
- "Minor" = Student's declared minor
- "Thematic.Sequence.Title" = Student's declared Thematic Sequence
- "Flag" = Did the student drop their Business Analytics Program at any point in their academic career
- "Course" = Couse names including: CSE148, BUS104, ACC221 ISA235, ISA225, ECO201, MGT291, FIN301, ISA125, MTH141, MGT295, MTH151
- "Final Letter Grade Group" = Final Letter Grade for each course as a standard letter, A B C D. 

## Contents of Folder

1. README: contains BVP, research question, updated data source with variables, explanation of files. 
2. Attributes.csv: input file- cleaned, used for merged data
3. BA_Majors.csv: input file- cleaned, used for merged data
4. BA Major Students - Minors.xlsx: input file- raw data, cleaned, used for merged data
5. BA Major Students - Thematic Sequence ISA2.xlsx: input file- raw data, cleaned, used for merged data
6. Grades.xlsx: input file- cleaned, used for merged data
7. Thematic Sequence.csv: input file for descriptive analysis- raw data
8. BA Minors.xlsx: input file for descriptive analysis- raw data
9. StudentData_withGrades: Cleaned data file created by combining input files. Used for the predicitve model
10. StudentData_noFlag: Cleaned data file created by combining input files without the Flag variable. Used to test the predicitve model. 
11. Project3-Final.rmd: Complete R-markdown file including Introduction, Research Questions, BVP, Cleaning Process, Descriptive Analysis, and Links to Predictive Model file. 
12. Project3-Final.html: RMD file converted to HTML
13. 616Model.ipynb: Created in Google Colab and exported to HTML. Links from Project3-Final connect here. Trains the predictive model. 
14. 616Model.html: File converted from .ipynb to HTML
15. 616Implementation.ipynb: Created in Google Colab and exported to HTML. Links from Project3-Final connect here. Implements the predictive model. 
16. 616Implementation.html: File converted from .ipynb to HTML
17. BVPgroup8.png: business value proposition diagram 
18. model_ROC_curve_AUC_score.png: ROC cuve image from trained model results
19. Model_confusion_matrix.png: Confusion Matrix image from trained model results
20. model_classifiction_report.png: Classification Report image from trained model results
21. model_feature_importance.png: image of feature importances as a bar chart. 


## Final Deliverable
The Project3-Final HTML file includes our entire research process including cleaning process and research products. This is our primary deliverable document. The two delivered products include a decriptive analysis with three bar charts and a predictive model to predict is students drop a business analytics program. The file links to a HTML file that can be used to imput data and project if a student will drop. 

