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

![Pivotal Events](https://github.com/unibo-dtm-se-2324-CompanyWindow/report/blob/main/pictures/EventStorming_PivotalEvents.PNG)

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


A ***command*** describes what triggered the event or flow of events, describing the system’s operations. In other word, commands represent actions that are executed to trigger domain events. 

![Command Visualization](https://github.com/unibo-dtm-se-2324-CompanyWindow/report/blob/main/pictures/EventStorming_CommandVisualization.PNG)

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


A particular command is executed by an actor in a specific role. ***Actors***:

-	*HR Manager*. Responsible for monitoring employer branding and analysing employee feedback.
-	*Prospective employee*. A potential candidate looking for real feedback about a company.


An automation ***policy*** is a scenario in which an event triggers the execution of a command. An automation policy that triggers the “Return sentiment analysis result” command when the “Analysis of the company is completed” event is observed. 
Policy, a command that is automatically executed when a specific domain event occurs. 

![Policy Visualization](https://github.com/unibo-dtm-se-2324-CompanyWindow/report/blob/main/pictures/EventStorming_PolicyVisualization.PNG)

Other examples:

+   *Automatic Execution*: Once the "Company Name Searched" event occurs, the system automatically triggers data scraping from sources.
+   *Report Generation*: After sentiment analysis is complete, the policy triggers the generation of the Employer Branding Report.

________________________________________________________________________________

## **Use Cases Collection**

