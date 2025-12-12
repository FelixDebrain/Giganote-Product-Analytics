# Giganote-Product-Analytics

## A complete end-to-end data analysis project exploring user behavior, feature engagement, device performance, and market insights for a fictional SaaS productivity app.

### Project Overview 
This project analyzes a synthetic dataset representing user activity on GigaNote, a fictional SaaS productivity app that allows users to create notes, export PDFs, sync data across devices, and manage documents. The dataset includes realistic app usage metrics such as session duration, device type, network type, feature usage, subscription status, and user behavior across different countries.
Below are what the columns look like: 

![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/6c8688117d206f0bf06f73ee4bd4a5cecd76b427/Screenshot%202025-12-12%20114607.png)

### Data Preparation and Table Creation Process

To preserve the integrity of the original dataset, my first step was to copy the raw data into a new working table. This allowed me to perform cleaning operations without modifying the source table. I created the new table using a standard CREATE TABLE … AS SELECT approach after copying the dataset to the clipboard and importing it into MySQL.

![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/fdc0cd52b07f8abf508212d37c4e68758f175caa/Screenshot%202025-12-12%20154209.png)

### Duplicate Removal Process 

After the working table was created, I implemented a duplicate-removal process using ROW_NUMBER() with a PARTITION BY clause. This method assigns a sequential row number to records that share the same key fields (such as session_id, user_id, or timestamp). Only rows with ROW_NUMBER() = 1 were retained, ensuring a clean, de-duplicated dataset.

![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/10a6de41a4186e18abe2f03c1de9ad877e8ce6c4/Screenshot%202025-12-12%20154334.png)

I proceeded to standardize the dataset to ensure consistency and analytical accuracy.

![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/017f63af356b6d0866d194f601b12d9ffd0c07d8/Screenshot%202025-12-12%20160250.png)

## Exploratory Data Analysis Question 1: Average Session Duration per Device Type
### The Query
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/0df745560fad8196e127aee73b65c9fc20f0faa5/Screenshot%202025-12-12%20162004.png)
### The Result
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/bd93dfc3861393c14915925c68644fe33d34ae84/Screenshot%202025-12-12%20163553.png)
- Desktop (Windows Laptop) users have the longest average sessions (34 minutes). This means the desktop app is the primary environment for deep productivity work.
- iOS users are the most engaged mobile users, spending more time than Android users.
- Android usage is healthy but more casual, suggesting mobile users prefer quick interactions.
- Smartwatch usage is extremely short, indicating it functions mainly for notifications or quick checks, not heavy interaction.

### Insight
- Invest more in desktop features, because it's the strongest platform for deep work. Enhancing editing tools, offline mode, and workspace organization makes sense.
- Optimize the iOS app. High engagement means a big ROI from improving iOS experience.
- Improve mobile onboarding. Android engagement is lower; better tutorials or reminders can help.
- Keep smartwatch features simple, quick actions only. No need to invest heavily here.


