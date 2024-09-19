# Course Hub

Welcome to the **Course Subscription Application**! This boilerplate application is designed to help you get started with building a simple course subscription application on the ServiceNow platform. It provides the foundational data model and basic configurations, allowing you to focus on implementing the required features and enhancing the application.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Application Overview](#application-overview)
- [Navigating the Application](#navigating-the-application)
- [Next Steps](#next-steps)
- [Additional Resources](#additional-resources)
- [Support](#support)

## Introduction

The Course Subscription Application allows learners to view available courses and subscribe to them. This boilerplate provides the essential components to help you implement features such as fetching course lists, subscribing to courses, and displaying subscribed courses.

## Prerequisites

Before you begin, ensure you have the following:

- **ServiceNow Personal Developer Instance (PDI)**
    - Sign up at [developer.servicenow.com](https://developer.servicenow.com/) if you don't have one.
- **ServiceNow Studio Access**
    - You will use Studio to import and manage the application.
- **Git and Remote Repository**
    - The repository is public; you should be able to clone it to your local machine and push it to the desired remote repository of your choice.

## Getting Started

Follow these steps to set up the application in your ServiceNow instance.

### 1. Set Up Your ServiceNow Developer Instance

1. **Sign Up for a PDI**

    - Visit [developer.servicenow.com](https://developer.servicenow.com/) and create an account.
    - Request a Personal Developer Instance (PDI) and follow the instructions to activate it.

2. **Access Your PDI**

    - Once your instance is ready, log in using the credentials provided.

### 2. Clone the Application

1. **Obtain the Repository URL**

    - Get the HTTPS URL of this repository hosting the application.
    - Clone it to your local machine.
    - Create a remote repository on your desired provider (e.g., GitHub, GitLab).
    - Change the remote to point to your new repository, then push the code to it.

2. **Create Git Credentials in ServiceNow**

    - In your PDI, navigate to **Connections & Credentials > Credentials**.
    - Click **New** and select **Credential**.
    - Select **Basic Auth Credentials**.
    - Fill in the following:

        - **Name**: *Git Source Control Credential*
        - **Username**: *Your username*
        - **Password**: *Your app password or account password*

    - Save the credential.

3. **Import the Application via Studio**

    - Use the application navigator to go to **All > Studio**.
    - You can now import the application that you pushed to your remote repository. Follow the guide: [Import App into the PDI](https://developer.servicenow.com/dev.do#!/learn/learning-plans/quebec/new_to_servicenow/app_store_learnv2_devenvironment_quebec_importing_an_application_from_source_control).

4. **Verify the Import**

    - Once the import is complete, you should see the application files in Studio.
    - Ensure there are no errors or conflicts.

## Application Overview

### Data Model

The application consists of three main tables:

1. **Course** (`x_quo_coursehub_course`)
2. **Learner** (`x_quo_coursehub_learner`)
3. **Course Subscription** (`x_quo_coursehub_course_subscription`)

### Tables and Fields

All the tables come with default fields: `sys_id`, `created`, `created_by`, `updated`, `updated_by`.

#### 1. Course Table

- **Label**: Course
- **Name**: `x_quo_coursehub_course`

**Fields**:

- **Title** (`title`): String (Max Length: 100, Mandatory)
- **Description** (`description`): String (Max Length: 500)
- **Type** (`type`): Choice (Options: Online, Offline, Hybrid)
- **Duration** (`duration`): Duration (Days Hours:Minutes:Seconds)

#### 2. Learner Table

- **Label**: Learner
- **Name**: `x_quo_coursehub_learner`

**Fields**:

- **User Account** (`user_account`): Reference to `sys_user` (Mandatory)
- **Admission Date** (`admission_date`): Date/Time

#### 3. Course Subscription Table

- **Label**: Course Subscription
- **Name**: `x_quo_coursehub_course_subscription`

**Fields**:

- **Learner** (`learner`): Reference to `x_quo_coursehub_learner` (Mandatory)
- **Course** (`course`): Reference to `x_quo_coursehub_course` (Mandatory)
- **Subscription Date** (`subscription_date`): Date/Time (Defaults to current date/time)

### Access Permission

The following table outlines the access permissions for the roles **x_quo_coursehub.manager** and **x_quo_coursehub.user** across the application's tables.

#### Roles

- **x_quo_coursehub.manager**
    - Full access (**Create**, **Read**, **Update**, **Delete**) to all tables.
- **x_quo_coursehub.user**
    - **Read** access to all tables.
    - **Create** and **Update** access to **Learner** and **Course Subscription** tables.

#### Access Permissions Table

| **Table**                                           | **Permission** | **x_quo_coursehub.manager** | **x_quo_coursehub.user** |
|-----------------------------------------------------|----------------|------------------------------|--------------------------|
| **Course**<br>`x_quo_coursehub_course`              | **Create**     | Yes                          | No                       |
|                                                     | **Read**       | Yes                          | Yes                      |
|                                                     | **Update**     | Yes                          | No                       |
|                                                     | **Delete**     | Yes                          | No                       |
| **Learner**<br>`x_quo_coursehub_learner`            | **Create**     | Yes                          | Yes                      |
|                                                     | **Read**       | Yes                          | Yes                      |
|                                                     | **Update**     | Yes                          | Yes                      |
|                                                     | **Delete**     | Yes                          | No                       |
| **Course Subscription**<br>`x_quo_coursehub_course_subscription` | **Create** | Yes | Yes |
|                                                     | **Read**       | Yes                          | Yes                      |
|                                                     | **Update**     | Yes                          | Yes                      |
|                                                     | **Delete**     | Yes                          | No                       |

## Navigating the Application

### Accessing the Application

1. **Open the Application Navigator**:

    - In your ServiceNow instance, use the filter navigator on the left. Click the **"All"** menu item on the top navigation bar to open the Application Navigator.
    - You should find the **"CourseHub"** application menu.
    - **Courses** and **Learners** are listed under **"CourseHub"**.

2. **Explore the Tables, Lists, and Forms**

    - Click on **"Course"** or **"Learners"**.
    - Create a few relevant records using the standard UI.

3. **Default REST API**

    - All the existing tables have REST API enabled.
    - You can check the [Table API](https://developer.servicenow.com/dev.do#!/reference/api/quebec/rest/c_TableAPI).
    - You can also explore using the REST API Explorer, which you can navigate to using the Application Navigator: **System Web Services > REST API Explorer**.

## Next Steps

Now that you have the application set up, you can start implementing the required features:

- **Course List**
    - Fetch and display a list of available courses.
    - Show course details: **Title**, **Description**, **Type**, **Duration**.
    - Implement subscription options:
        - **Option 1**: Add a **"Subscribe"** button.
        - **Option 2**: (Optional) Implement drag-and-drop subscription.

- **Subscription Feature**
    - Create functionality to handle course subscriptions.
    - Update the **Course Subscription** table when a learner subscribes.

- **My Courses**
    - Display courses that the current learner is enrolled in.
    - Provide an option to unsubscribe if desired.

## Additional Resources

- **ServiceNow Developer Site**: [developer.servicenow.com](https://developer.servicenow.com/)
- **ServiceNow Documentation**:
    - [Building Applications on the Now Platform](https://docs.servicenow.com/bundle/quebec-application-development/page/build/applications/concept/build-applications.html)
    - [Tables and Data Management](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/table-administration/concept/c_TableAdministration.html)
    - [Pro-Code Development](https://docs.servicenow.com/bundle/quebec-application-development/page/build/applications/concept/building-pro-code-applications.html)
    - [REST API Reference](https://developer.servicenow.com/dev.do#!/reference/api/quebec/rest)

## Support

If you encounter any issues or have questions:

- **Contact**: [Arjun Basnet]
- **Email**: [ab@datacontentmanager.com]
- **Issues**: [Bitbucket Repository Issues Page](https://bitbucket.org/qualdatrix/coursehub/issues)

---

We hope this boilerplate helps you get started quickly. Good luck with your assignment, and we look forward to discussing your work in the interview!

---
