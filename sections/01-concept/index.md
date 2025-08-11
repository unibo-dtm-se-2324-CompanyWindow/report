---
title: Concept
has_children: false
nav_order: 2
---

# **Concept**

In software development and system design, it is essential to use multiple techniques to ensure a deep understanding of user needs and system behaviour. No single approach can address all aspects of a project, which is why we use a combination of methods.

## **Doing Event Storming**

Brainstorm of the domain events related to the business domain – a ***domain event*** is something interesting that has happened in the business. 

“Happy path scenario” – the flow that describes a successful business scenario:

-	Request for a Company - Company Name Searched
-	API Request Received
-	Data Scraped from many sources
-	New Data Source Added
-	API Response Sent
-	Employer Branding Report Created
-	Sentiment Analysis Result Returned
-	Data Visualization Generated

These events, also known as *"pivotal events"*, define the workflow and effectiveness of the CompanyWindow software.

![Pivotal Events](./imgs/events_storming.png)

In the context of the EventStorming process, identifying ***pain points*** is critical to understanding areas where the process or system may face challenges, inefficiencies or potential failures. Here are a few potential pain points:

1.	Data accuracy and reliability. 
    * Challenge: Scraping data from sources can result in inconsistent or incomplete data, which can affect the accuracy of sentiment analysis and the overall reliability of the employer branding report.
    * Impact: Inaccurate data can lead to incorrect sentiment analysis, leading to false results and ultimately poor decision making by HR or marketing teams.
    * Mitigation: Implement data validation and error handling mechanisms to ensure that only accurate and reliable data is used for analysis.

2.	Complexity of sentiment analysis 
    * Challenge: Sentiment analysis is inherently complex, especially when dealing with nuances such as sarcasm, context or mixed sentiments within a single review.
    * Impact: Inaccurate sentiment classification can lead to incorrect conclusions about a company's reputation, potentially compromising its branding efforts.
    * Mitigation: Continuously improving the sentiment analysis model with machine learning and embedding feedback loops can help improve accuracy over time.

3.	Data Visualization - UI
    * Challenge: Presenting data in a clear and intuitive way can be challenging, especially when dealing with large datasets or complex insights such as sentiment trends over time. Badly designed interfaces can make it hard for users to navigate.
    * Impact: When users cannot easily interpret data or trends, the value of the analysis is compromised, causing misunderstandings or poor decisions by HR teams. A messy interface can discourage users from engaging with the platform at all.
    * Mitigation: Focus on user-centred design principles by creating simple, clean and interactive dashboards. Implement data filtering options, drill-down capabilities, and visual representations (e.g., charts, colour coding) that make complex data easier to digest. Regular user feedback should be incorporated to refine and improve the interface.

</br>

A ***command*** describes what triggered the event or flow of events, describing the system’s operations. In other word, commands represent actions that are executed to trigger domain events. 

![Command Visualization](./imgs/actor_command_events.png)

For example:

1.	*Submit company name for search*
    + Actor: Prospective Employee
    + Event Triggered: Company Name Searched 
2.	*Scrape data from Glassdoor (sources)*
    + Actor: Software  
    + Event Triggered: Request for Data Scraped from Glassdoor
3.	*Analyze sentiment of reviews*
    + Actor: Software or the person behind the software, for example a Data Analysis.
    + Event Triggered: Request Sentiment Analysed Result of data collected
4.	*Request employer branding report*
    + Actor: HR Manager
    + Event Triggered: Employer Branding Report Created

</br>

A particular command is executed by an actor in a specific role. ***Actors***:

-	*HR Manager*. Responsible for monitoring employer branding and analysing employee feedback.
-	*Prospective employee*. A potential candidate looking for real feedback about a company.

</br>

An automation ***policy*** is a scenario in which an event triggers the execution of a command. An automation policy that triggers the “Return sentiment analysis result” command when the “Analysis of the company is completed” event is observed. 
Policy, a command that is automatically executed when a specific domain event occurs. 

![Policy Visualization](./imgs/policy.png)

Other examples:

+   *Automatic Execution*: Once the "Company Name Searched" event occurs, the system automatically triggers data scraping from sources.
+   *Report Generation*: After sentiment analysis is complete, the policy triggers the generation of the Employer Branding Report.

</br>

## **Use Cases Collection**

</br>

A use case can be conceived as a set of scenarios tied together by a common user goal – a scenario is a sequence of steps describing an interaction between a user and a System. So, a use case lists the steps required to achieve a goal from users’ point of view, including the interactions between users and systems. It provides a narrative of how a System is used.
</br> 
We'll outline the primary use cases, actors, and their interactions within the system.


![Use Cases Diagram](./imgs/UseCases.jpg)

#### Use Case 1: Search for a company 

- Primary Actor: User  

- Main Scenario:

    1. The user opens the system

    2. The user enters the company name in the search bar

    3. The user views the page with all the collected data related to the searched company


#### Use Case 2: View sentiment analysis results

- Primary Actors: Prospective Employee, HR Manager

- Description: HR Managers and Prospective Employees review sentiment analysis results to understand the company’s image

- Main Scenario:

    1. The user is on the page of the searched company

    2. The user selects the "Sentiment Analysis" option

    3. The system displays the sentiment analysis results

    4. The user uses the data to understand the company’s image.


#### Use Case 3: Read and filter reviews

- Primary Actor: User

- Main Scenario:

    1. The user accesses the company's page

    2. The user selects the "Reviews" section

    3. The user selects the filter option

    4. The user chooses the desired filters

    5. The user clicks on "Apply"


#### Use Case 4: Login

- Primary Actor: User

- Main Scenario:

    1. The user navigates to the login page

    2. The user enters their username and password

    3. The user clicks on the "Login" button

    4. The system verifies the credentials

    5. The user is logged in and redirected to the main dashboard or homepage

- Extensions: 
    - Invalid credentials are entered

    - The system displays an error message àThe user is prompted to re-enter his credentials


#### Use case 5: saving a company in the library

- Actors: subscribe users

- Main Scenario:

    1. The user opens the application

    2. The user logs in with their credentials

    3. The user types the name of the company in the search bar

    4. The user visualizes the interface with all the data collected

    5. The user clicks on “save in the library”


#### Use case 6: View all the elements saved in the library

- Actors: users

- Description: Users can check all the companies they have saved

- Main scenario:

    1. The user opens the application

    2. The user logs in with their credentials

    3. The user clicks on “library”

    4. The user views all the elements saved

</br>

## **User Stories**

**Related to functions and tools**

- As a user (both company and job seeker), I want to save companies I’m interested in, so that I [can check them all later/I don’t have to search for them again]. 

- As a user, I want to filter and order my library according to different criteria, so that I can view company with features that I’m looking for the most. 

*UI/UX* 
- As a user, I want an easy and intuitive UI so that I won’t have any problems in using the [software/website/app?] 

*Log in and access*
- As a user, I want an option to log in/register so that I can visualize what I saved in every device. 

- As a user, I want to be able to easily sync my app data across multiple devices, so that I can access my information from anywhere. 

</br>

**More related to benefits and necessities** 

- As a user (HR), I want to see the overall rating given by the company’s employees so that I can understand [what to improve/build an employer branding strategy].  

- As a user (HR), I want to see the most used negative words used in reviews so that I can understand how to address the issues.  

- As a user (HR), I want to see the most used positive words used in reviews so that I can understand what employees find favorable about the company.  

- As a user (HR), I want to see similar companies recommended so that I can check out my competitors.  

- As a user (job seeker), I want to see the overall rating given by the company’s employees so that I can choose carefully where to apply. 

- As a user (job seeker), I want to see the most used negative words used in reviews so that I can see the potential drawbacks of joining the company.  

- As a user (job seeker), I want to see the most used positive words used in reviews so that I can evaluate the potential benefits of joining the company.  

- As a user (job seeker), I want to see similar companies recommended so that I can keep my [applying] options open. 