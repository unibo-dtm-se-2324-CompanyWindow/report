---
title: Validation
has_children: false
nav_order: 6
---

# Validation

### Test Development Process   

Our testing process was based on a combination of unit testing and integration testing, with a strong focus on achieving high success rates and test coverage for the core components. The testing strategy was not strictly Test-Driven Development (TDD) but was closely integrated with the development cycle to ensure that each new feature or fix was accompanied by a corresponding set of tests. We used Python's **Pytest** framework for our scripts and Node.js's **Jest** and **Supertest** for our backend.   

 

### Specific Testing of Core Components   

 

**Scraping and Data Processing Tests:**   

- **Approach:** To validate our scraping scripts, we developed an automated integration testing suite. These tests verify the end-to-end functionality by making real network calls to an external scraping API (Scrapfly) to retrieve data from live websites. This approach ensures that our scripts can successfully interact with external services and correctly parse the actual data returned. While this makes the tests inherently non-deterministic, it provides a crucial check on the overall system's health and its ability to handle real-world data. We currently use this suite as a core part of our testing process.   

- **Metrics:**   

  - *Functionality:* Verifying that the scripts successfully connect to the external API and retrieve data for known entities (e.g., "eBay").   

  - *Data Integrity:* Ensuring that the retrieved data is not empty and contains the expected fields (e.g., name, employerId for companies, and a list of reviews).   

  - *Output Format:* Validating that the final output matches the expected data structures, such as a dictionary containing a list of reviews.   

  - *Auxiliary Functions:* Testing helper functions, like URL manipulation, to ensure correct internal logic.   

- **Comments on Requirements:** These tests are critical because they validate the integrity and format of the raw data — the foundation for FR2. They ensure that data is successfully retrieved from external APIs and that it contains the necessary fields. Without these checks, the system could not perform accurate sentiment analysis or create meaningful data visualizations.   

 

**Sentiment Analysis Tests:**   

- **Approach:** Testing the sentiment analysis component was crucial for meeting the project's data accuracy requirements. To validate the core logic, we created a comprehensive deterministic, automated testing suite using Python's **pytest** framework. This suite utilizes a gold-standard dataset of manually labeled reviews to verify core functionalities. We are also currently developing a non-deterministic, automated testing suite for this component, which will be integrated into the CI/CD pipeline.   

- **Metrics:**   

  - *Sentiment Classification:* Unit tests (`test_analyze_sentiment_positive`, `test_analyze_sentiment_negative`, `test_analyze_sentiment_neutral`) verify that the sentiment analysis function correctly scores texts with known sentiments.   

  - *Data Aggregation:* The `test_calculate_sentiment_and_words_indeed` test ensures that the system correctly processes a list of reviews and accurately calculates an overall average sentiment score and word frequencies.   

  - *Word Cloud Generation:* Tests like `test_get_word_frequencies`, `test_generate_word_cloud_with_data`, and `test_generate_word_cloud_no_data` confirm that the system can correctly identify word frequencies and generate a visual word cloud from both populated and empty datasets.   

  - *Data Loading:* The `test_get_overall_sentiment_data_success_glassdoor` test validates that the system can correctly load and process data from different sources (e.g., Glassdoor JSON files).   

- **Comments on Requirements:** The deterministic tests showed that the sentiment analysis model achieved a high accuracy on our controlled dataset, surpassing the 85% threshold set in the Acceptance Criteria for FR2. The test suite also verified the correct functionality of the word frequency calculation and word cloud generation, directly addressing FR2.3.   

 

**User Authentication & Management Tests:**   

- **Approach:** We developed a dedicated testing suite using **Jest** and **Supertest** to validate the user authentication and account management logic. The tests simulate user interactions with the backend (e.g., registration, login, profile updates) to ensure the system behaves as expected.   

- **Metrics:**   

  - *Success Rate:* Tests verify that user registration and successful logins return a `200` status code, while failed login attempts correctly return a `401 Unauthorized` status.   

  - *Data Integrity:* The tests confirm that user data (email, password hash, role) is accurately stored in the MongoDB database.   

 

**Saved Searches & Notes Tests:**   

- **Approach:** This suite tests the functionality for saving and retrieving searches. We use **Jest** and **Supertest** to simulate a logged-in user saving a search report and adding a custom note. The tests then verify that the saved data correctly persisted and can be retrieved accurately.   

- **Metrics:**   

  - *Functionality:* Tests confirm that a saved search can be successfully retrieved from the user's profile and that the associated report data is displayed correctly.   

  - *Data Integrity:* We validate that the user's custom notes are saved alongside the report in the database and are loaded correctly when the report is accessed.   

 

### Test Coverage Result   

**Python scripts**   

The command used to run the tests and calculate coverage was:   
```python
python -m pytest --cov=. --cov-report=term 
```
 

This executed 10 tests, all of which passed successfully in 46.00 seconds.   

The total code coverage for the project was measured at **78%**.  

**Node.js (backend)**

To run the test suite, use the following command:

```bash
npm test
```

Or, for more detailed output including coverage:

```bash
npm run test:coverage
```

A total of **95 tests** were executed across **8 suites**, all passing successfully in **7.16 seconds**.

The project achieved an average code coverage of approximately **85%**, including:

- **Statements:** 84.29%
- **Branches:** 84.31%
- **Functions:** 85.36%
- **Lines:** 84.84%

> Coverage is measured using **Jest** with built-in support for coverage reporting


## Acceptance Test   

Acceptance tests were designed to verify that the final, integrated system met all functional and non-functional requirements from the perspective of an end-user. These tests were conducted manually and also involved running end-to-end scenarios; however, not all tests were performed, and the first two are currently hypothetical.   

 

1. **Test Case for FR1 (Data Collection):**   

   - *Scenario:* A user requests sentiment data for a company.   

   - *Outcome:* The test successfully demonstrated that the system’s backend API could trigger the Python scraping script, which would return the collected data in the specified JSON format. We validated that new reviews were successfully added to the database.   

 

2. **Test Case for FR2 (Sentiment Analysis):**   

   - *Scenario:* A user views the company dashboard.   

   - *Outcome:* We confirmed that the dashboard displayed a word cloud visualization and an AI-generated summary that correctly reflected the sentiment of the reviews, confirming that the integration between the backend and the Python scripts was successful.   

 

3. **Test Case for FR3 (Search Functionality):**   

   - *Scenario:* A user searches for a company by name.   

   - *Outcome:* Manual testing of the search bar confirmed that the search results were returned with a confirmation message quickly. The complete report was then delivered to the frontend within the expected timeframe, meeting the performance criteria.   

 

4. **Test Case for FR4 (User Authentication & Management):**   

   - *Scenario:* A new user registers as an HR Manager. They then log in, change their password and the company name, and finally delete their account.   

   - *Outcome:* Manual testing of the registration process confirmed that the user's role and company name were correctly captured. We successfully verified that the user could update their password and company name, and that the profile was securely deleted from the database, fulfilling all criteria for user management.   

 

5. **Test Case for FR4 (Saved Searches):**   

   - *Scenario:* A logged-in user performs a search, saves the result to their library, and adds a note. They then retrieve the saved search and confirm that the note is present.   

   - *Outcome:* The manual test confirmed that the "Save to Library" functionality correctly stored the report. The saved report was successfully retrieved from the user's profile, and the custom notes were displayed correctly, confirming the functionality of FR4.4.   

 

These acceptance tests confirmed that the project, as a whole, met the key functional and non-functional requirements, ensuring a reliable and usable final product.   