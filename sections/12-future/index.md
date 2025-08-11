---
title: Future work
has_children: false
nav_order: 13
---

# Future Work


 



 

This section outlines known issues and planned enhancements for the CompanyWindow application, demonstrating a roadmap for its continued improvement. 

 

## Known Issues 

 

The current implementation has some limitations that will be addressed in future versions: 

 

- **Non-deterministic Scraping:**   

  The web scraping process is inherently fragile. Minor changes to the HTML structure of external websites like Indeed and Glassdoor could break the scraping scripts. The current solution relies on mock data testing but requires continuous monitoring and updates. 

 

- **API Rate Limits:**   

  The application's reliance on external APIs, such as Scrapfly and Gemini, introduces a dependency on their respective rate limits. High user traffic could potentially exceed these limits, leading to service interruptions. It will also increase the costs of maintaining CompanyWindow since the APIs have a cost-per-use. 

 

- **Limited Data Sources:**   

  The current version scrapes data from only two websites. While this is sufficient for a proof of concept, a broader analysis would require integrating more data sources. 

 

## Future Developments 

 

The following features are planned to enhance the application's functionality, performance, and robustness: 

 

### Optimization and Scalability 

 

- **Scraping Result Caching:**   

  To reduce dependency on API tokens and improve performance, a caching mechanism will be implemented. When a user requests an analysis for a company that has been recently scraped (e.g., within the last 24 hours), the application will retrieve the saved data from the cache instead of performing a new scrape. This will drastically reduce response times and minimize token usage. 

 

- **Integration with New Data Sources:**   

  To provide a more comprehensive overview of a company's reputation, the system will be expanded to include new platforms such as LinkedIn, industry-specific forums, and news websites. The scraping logic will be updated to also extract some of the main articles from these news sites. 

 

- **Country Selection:**   

  Users will be able to specify a country of interest when searching for reviews, allowing for more targeted and localized sentiment analysis for each company. 

 

### User Interface Enhancements 

 

- **Interactive Data Visualization:**   

  The user interface will be enriched with dynamic dashboards and interactive charts. These tools will enable users to visualize sentiment trends over time, compare different companies side-by-side, and monitor key metrics (e.g., number of positive/negative reviews) for a more intuitive analysis. 

 

- **Longitudinal Sentiment Analysis:**   

  An advanced sentiment analysis feature will be developed to analyze reviews over time. This will allow users to track whether sentiment has improved or worsened and identify specific periods of significant change, providing a deeper understanding of trends and shifts in public perception. 

 

- **Transition to a Web Application:**   

  The application, currently a prototype, will be developed as a full-fledged Web Application to make it accessible from any device and to simplify user management and advanced feature implementation. 

 

### Security and Advanced Features 

 

- **HR Notification System:**   

  A push or email notification system will be implemented to alert HR managers in real-time about significant changes in the company's overall sentiment, allowing them to react promptly. 

 

- **Enhanced User Management:**   

  The account management system will be improved to include advanced security features like a password recovery flow with email verification and multi-factor authentication (MFA).
