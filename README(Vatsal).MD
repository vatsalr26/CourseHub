a. Introduction to the Solution
This project was built using ServiceNow’s UI Builder as part of a course subscription application. The application base was provided via a Bitbucket repository, which I cloned and imported into my ServiceNow instance.
From there, I worked within the UI Builder to create five pages. The main entry point is the Home page, which allows users to navigate to:
A list of available courses (Course Master)

Their personal enrollments (My Enrollments)

A view of all learners across the platform (All Learners)

Each feature is connected to back-end data via ServiceNow tables, and subscriptions are managed through a subflow that creates records in a dedicated course subscription table.

b. Description of Implemented Features
Below is a breakdown of each feature and how it aligns with the assignment requirements:
1. Home Page
![image alt](https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/Home%20page.png)
Components: Header, text blocks, and three buttons

Purpose: Serves as the main dashboard

Course Master navigates to the course listing

My Enrollments shows the user’s enrolled courses

All Learners shows a full list of enrolled users

2. Course Master Page

Component used: List

Displays all courses from the Course table

Clicking a course opens the Course Master Form page

3. Course Master Form Page

Components: Form and Button

Displays course details

Subscribe button triggers a subflow (Enroll Users) that creates a record in the Course Subscription table

4. My Enrollments Page

Component: Table or List

Shows courses that the currently logged-in user is subscribed to

Data is filtered based on user ID from the Course Subscription table

5. All Learners Page

Component: Table or List

Displays all learners who have enrolled in any course

Pulls data from the Course Subscription table


c. Step-by-Step User Interaction
Home Page
 Users land on the Home page, which has a welcome message and three buttons:

Course Master

My Enrollments

All Learners

Course Listing
 Clicking Course Master takes the user to a list of all available courses. Clicking on a course opens a detailed view of that course.
![image alt](https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/CourseMaster.png)

Subscribe to Course
 On the Course Form page, users can click the Subscribe button. This action triggers a subflow that creates a new record in the Course Subscription table for that user and course.
![image alt](https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/CourseForm.png)

View Enrolled Courses
 Clicking My Enrollments shows a filtered list of courses that the logged-in user is currently enrolled in.
![image alt](https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/SubscribeProof.png)

View All Learners
 Clicking All Learners displays all learners across the system who are subscribed to any course.
![image alt](https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/SubscribeProof.png)

d. Features Not Implemented
The following features were not implemented due to time constraints:
Unsubscribe functionality – Users currently cannot remove their enrollment.

Duplicate subscription prevention – There is no check in place to prevent users from subscribing to the same course multiple times.

Visual feedback or highlights – No UI feedback (such as confirmation messages) was implemented after subscribing.


e. Testing Summary
Testing is still in progress. The expected behavior for each page and interaction has been manually verified to some extent, but the actual test suite is not yet functioning as intended. Once it is working, it will be used to confirm:
Navigation between pages

Successful triggering of the subflow upon subscribing

Proper data display on the My Enrollments and All Learners pages

Visibility of components and data filtering by user



