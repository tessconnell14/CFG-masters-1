# CFG-masters-1
This repo contains the group data analysis of Fran, Tess and Rumbie.

### Problem: 
How do educational backgrounds and learning paths influence the career outcomes and success of software developers globally?

### Aims:
To find out the routes different people take into software development.
To find out the success rates of taking other routes into software development.
To compare compensation packages for people entering the industry from different routes.
To compare compensation packages for developers working in different industry areas.

### Background:
The question remains whether people are capable of getting into software development through different learning paths and the general success rate of becoming one without a degree. Based on research conducted by Nick Larsen (2016), he conducted a developer survey which found that 56% of developers in fact do not have a college degree in computer science or related fields. And that the most popular and common way for developers to get into the software developer industry was through “Self-teaching”.  69% of respondents told us they were partially self-taught (which includes doing bootcamp courses), whereas 13% stated that they had entirely taught themselves. To further support this…

According to research by Statista (2024), the global developer population was expected to reach 28.7 million people by the end of 2024, an increase of 3.2 million from the number seen in 2020. Although a number of people still enter this career via traditional university routes, it seems a growing number of people are now entering the profession via alternative routes. But how easy is a transition into tech and are these career changers being fairly compensated?

This project aims to gain insights into the different learning paths that software developers take into the industry and compare outcomes of professionals from different backgrounds to see just how easy this transition is. Experienced professionals from other industries may also find they are not fairly compensated or have to take a pay cut. This project will also analyse trends in compensation and attempt to establish what ‘fair’ compensation looks like at different points in a person’s career. Compensation packages in different industry areas will also be analysed.

### Stakeholders/audience:
- Aspiring Software Developers: Gain insights into effective learning paths and strategies for career success.
- Career Changers: Gain understanding of routes in and fair compensation.
- Educational Institutions: Tailor programs to better prepare students for careers in software development.
- Employers: Identify key educational and experiential factors that predict successful hires.

### Potential problems with datasets:
- Finding a sufficient amount of data, particularly salary/financial data about individuals
- Accuracy and reliability of survey data
- Errors in text data, e.g. typos
- Missing data if fields in survey are not required
- Data may not be fully representative of the whole software development population which makes it difficult to verify its validity.
- A large amount of categorical data - will need to be encoded if performing any machine learning

### Dataset: Stack Overflow Developer Survey (2023)
Reason for choosing:
- This is an annual survey of developers carried out by Stack Overflow
- Survey results date back to 2011 which will enable us to look at trends over time later in the project
- This data will be representative of individuals across the industry rather than just from one company, so should give a broad overview of different experiences
- There were a large number of respondents to the most recent survey (almost 90,000), meaning that even with some missing data, results from analysis will still be significant
- The survey gives details of experience, educational background, age, job role and salary so will help us the answer our aims
- The survey also gives detailed information about how people have learnt to code, and tools they use within their work

### EDA (Please see the file named developer_survey_analysis.ipynb)
Challenges: 
- The survey contains a large amount of categorical data and very little numerical data making some comparisons more challenging, e.g. education level
- Many columns contain multiple responses, e.g. some people are ‘Employed’ but also ‘Student’ and all information is currently stored in the same place. We may need to separate the data into separate columns later in the project, e.g. for machine learning and encoding
- Data contains a mixture of full-time/part-time, hobbyists etc so will need to filter out
- Some columns have a mixture of data types, e.g. YearCoding is mainly numerical but then has some strings, e.g. ‘less than 1 year’ making calculations more difficult

Data quality:
- Most columns have missing data as the survey was very long and did not require responses for all questions (please see developer_survey_analysis.ipynb to see how we dealt with missing data in different columns)
- Due to the lack of text input opportunities in the survey there are no formatting or spelling errors in the data
- There are some very high outliers in the data, particularly in the ‘ConvertedCompYearly’ column which have skewed the mean 

### Data Cleaning (Please see the file named developer_survey_analysis.ipynb)

Data cleaning steps that we took:
- Remove unwanted columns
- Handle missing values
- Handle outliers
- Handle duplicates

Remove unwanted columns:
- There were a number of columns that were not relevant to our data and which contained very high amounts of missing values
- Unwanted columns and columns with more that 50% missing data were removed 

Handle missing values:
- There was a vast amount of data missing in the employed dataframe
- Missing data in each column was handled differently as they were different data types/ had different purposes

Most relevant columns to our study:
YearsCode: filled with the median
YearsCodePro: filled with YearsCode - av_difference_years (see code)
WorkExp: filled with the 'YearsCodePro' data as, on examination, the answers for these questions were predominantly similar (with the exception of career changers)
ConvertedCompYearly: filled with the median, but machine learning may be used to get better estimates later

Other columns:
Other columns where data is categorical (e.g. organisation size, industry etc), missing vals were filled with the mode

Handle outliers:
We removed any observations where the salary data was more that 3 standard deviations from the mean

Handle duplicates:
We checked for duplicates but there were none present in the data


**Assignment requirements:**
1. Identify a real-world problem you are interested in solving using data analytics
2. Based on the problem identified, research and find a dataset that can help address this problem
3. Conduct an in-depth Exploratory Data Analysis (EDA) on your dataset(s), identify key features, any interesting patterns or anomalies, and potential challenges in the data
4. Perform and document the data cleaning process
