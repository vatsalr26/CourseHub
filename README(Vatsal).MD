<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Course Subscription Application - README</title>
</head>
<body>

<h2>a. Introduction to the Solution</h2>

<p>
    This project was built using <strong>ServiceNow’s UI Builder</strong> as part of a course subscription application. The application base was provided via a Bitbucket repository, which I cloned and imported into my ServiceNow instance.
</p>
<p>
    From there, I worked within the UI Builder to create five pages. The main entry point is the <strong>Home page</strong>, which allows users to navigate to:
</p>
<ul>
    <li>A list of available courses (<strong>Course Master</strong>)</li>
    <li>Their personal enrollments (<strong>My Enrollments</strong>)</li>
    <li>A view of all learners across the platform (<strong>All Learners</strong>)</li>
</ul>
<p>
    Each feature is connected to back-end data via ServiceNow tables, and subscriptions are managed through a subflow that creates records in a dedicated course subscription table.
</p>

<h2>b. Description of Implemented Features</h2>

<p>Below is a breakdown of each feature and how it aligns with the assignment requirements:</p>

<ol>
    <li>
        <strong>Home Page</strong><br />
        Components: Header, text blocks, and three buttons<br />
        Purpose: Serves as the main dashboard<br />
        <ul>
            <li>Course Master navigates to the course listing</li>
            <li>My Enrollments shows the user’s enrolled courses</li>
            <li>All Learners shows a full list of enrolled users</li>
        </ul>
    </li>

    <li>
        <strong>Course Master Page</strong><br />
        Component used: List<br />
        Displays all courses from the Course table<br />
        Clicking a course opens the Course Master Form page
    </li>

    <li>
        <strong>Course Master Form Page</strong><br />
        Components: Form and Button<br />
        Displays course details<br />
        Subscribe button triggers a subflow (Enroll Users) that creates a record in the Course Subscription table
    </li>

    <li>
        <strong>My Enrollments Page</strong><br />
        Component: Table or List<br />
        Shows courses that the currently logged-in user is subscribed to<br />
        Data is filtered based on user ID from the Course Subscription table
    </li>

    <li>
        <strong>All Learners Page</strong><br />
        Component: Table or List<br />
        Displays all learners who have enrolled in any course<br />
        Pulls data from the Course Subscription table
    </li>
</ol>

<h2>c. Step-by-Step User Interaction</h2>

<h3>Home Page</h3>
<p>Users land on the Home page, which has a welcome message and three buttons:</p>
<ul>
    <li>Course Master</li>
    <li>My Enrollments</li>
    <li>All Learners</li>
</ul>
<p><img src="https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/Home%20page.png" alt="Home Page" /></p>

<h3>Course Listing</h3>
<p>Clicking Course Master takes the user to a list of all available courses. Clicking on a course opens a detailed view of that course.</p>
<p><img src="https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/CourseMaster.png" alt="Course Master" /></p>

<h3>Subscribe to Course</h3>
<p>On the Course Form page, users can click the Subscribe button. This action triggers a subflow that creates a new record in the Course Subscription table for that user and course.</p>
<p><img src="https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/Subscribe!.png" alt="Subscribe to Course" /></p>

<h3>View Enrolled Courses</h3>
<p>Clicking My Enrollments shows a filtered list of courses that the logged-in user is currently enrolled in.</p>
<p><img src="https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/SubscribeProof.png" alt="My Enrollments" /></p>

<h3>View All Learners</h3>
<p>Clicking All Learners displays all learners across the system who are subscribed to any course.</p>
<p><img src="https://github.com/vatsalr26/CourseHub/blob/main/Screenshots/SubscribeProof.png" alt="All Learners" /></p>

<h2>d. Features Not Implemented</h2>
<p>The following features were not implemented due to time constraints:</p>
<ul>
    <li><strong>Unsubscribe functionality</strong> – Users currently cannot remove their enrollment.</li>
    <li><strong>Duplicate subscription prevention</strong> – There is no check in place to prevent users from subscribing to the same course multiple times.</li>
    <li><strong>Visual feedback or highlights</strong> – No UI feedback (such as confirmation messages) was implemented after subscribing.</li>
</ul>

<h2>e. Testing Summary</h2>
<p>Testing is still in progress. The expected behavior for each page and interaction has been manually verified to some extent, but the actual test suite is not yet functioning as intended. Once it is working, it will be used to confirm:</p>
<ul>
    <li>Navigation between pages</li>
    <li>Successful triggering of the subflow upon subscribing</li>
    <li>Proper data display on the My Enrollments and All Learners pages</li>
    <li>Visibility of components and data filtering by user</li>
</ul>

</body>
</html>
