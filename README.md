# Giganote-Product-Analytics

## A complete end-to-end data analysis project exploring user behavior, feature engagement, device performance, and market insights for a fictional SaaS productivity app.

### Project Overview 
This project analyzes a synthetic dataset representing user activity on GigaNote, a fictional SaaS productivity app that allows users to create notes, export PDFs, sync data across devices, and manage documents. The dataset includes realistic app usage metrics such as session duration, device type, network type, feature usage, subscription status, and user behavior across different countries.
Below are what the columns look like: 

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

## Exploratory Data Analysis Question 2: Country with the highest engagement (actions per session)?
### The Query
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/22c2b96e8d9d3d485a4ea4489a89d7dfc47ca695/Screenshot%202025-12-12%20164009.png)
### The Result
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/d9c0015819b6902541422da8efdfa8ccef3c6f88/Screenshot%202025-12-12%20165351.png)
- India and Germany show the highest engagement, but limited data means we should treat them as emerging high-value segments.
- The United Kingdom is the most reliable high-engagement market, showing strong usage depth across multiple sessions.
- The United States of America has moderate engagement but consistent activity, making it a good target for feature improvements and retention campaigns.
- Nigeria has the highest session volume, showing strong adoption, but lower engagement per session indicates onboarding or usability improvements may be needed.

### Insight
- Prioritize deeper engagement features for the UK and USA. These countries show repeat usage and will respond well to improvements.
- Target Nigeria for onboarding improvements. High traffic but lower engagement suggests new users need better guidance.
- Explore India and Germany as high-value early markets, even with low sample size, actions/session is extremely strong.
- Localize content or notifications by region, to increase engagement where it’s low.

## Exploratory Data Analysis Question 3: The network type that produces the highest engagement?
### The Query
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/690c8a9c01a33a9b44a0e1fefee494f3ed260bbf/Screenshot%202025-12-17%20153624.png)
### The Result
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/6d2daebeee323728449f552f96231c3e9a36c6dc/Screenshot%202025-12-17%20155451.png)
- WiFi has the highest engagement (30 actions per session).
  Likely because WiFi is more stable, faster, and less battery-draining, and sessions are also frequent (13 sessions), making this metric reliable.
- 5G is second (21.25 actions/session).
  High-speed mobile network drives good engagement, but fewer sessions (4) → smaller sample size, this shows potential for mobile power users.
- 4G is moderate (12.78 actions/session)
  Many users rely on 4G for casual app interactions.
- 3G is the lowest (7.75 actions/session)
  Poor performance due to slower speeds and possible app lag, and this indicates that users on 3G may have frustrating experience, causing lower engagement.

  ### Insight
- Users on WiFi or 5G are likely in urban areas or office settings → good targets for premium features.
- 3G/4G users are more casual → good for freemium onboarding campaigns.

## Exploratory Data Analysis Question 4: Compare Device Quality
### The Query
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/aa64bf8317c1a0a8cd88d818558bffab159127eb/Screenshot%202025-12-17%20160845.png)
### The Result
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/1f07ecd56bf80e3b58e8cfb68a1577dd204ae347/Screenshot%202025-12-17%20162608.png)
- Subscribers crash less → better devices, all subscribers use premium devices → zero crashes while non-subscribers use budget or older devices → high crash rate.
- Device quality directly impacts engagement and stability. Subscribers’ devices are Windows Laptops, iPhones, Pixels → longer sessions, smooth performance and non-subscribers’ devices and older Android, lower-end phones
- Shorter sessions, more crashes.

### Insight
- App optimization: Focus on low-end Android and older devices to reduce crashes for non-subscribers.
- Premium positioning: Subscribers enjoy stable performance on high-end devices, this reinforces the value of subscription.
- Targeting/marketing: Users with lower-end devices might be encouraged to subscribe if app stability improves.

## Exploratory Data Analysis Question 5:  ExportPDF usage by country (business users vs casual users)
### The Query
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/ca85793d87c367cd3b99060b5f71d99bcfec8ff7/Screenshot%202025-12-17%20163925.png)
### The Result
![image alt](https://github.com/FelixDebrain/Giganote-Product-Analytics/blob/3bdd5d39ef5829966192d65321479b645fdadd24/Screenshot%202025-12-17%20163937.png)
- Germany shows premium business-grade usage patterns. This is a high-priority expansion market for enterprise/document-heavy features.
- India is a top expansion market. It combines high subscriber usage with very high document workflow activity.
- Nigeria is an emerging growth market. This country has high engagement, but users are still mostly casual

### Insight
ExportPDF engagement is strongest among subscribers in Germany and India, showing clear professional and enterprise usage patterns. Nigeria, although driven by casual users, demonstrates high engagement (42 actions/session), indicating strong potential for adoption through targeted onboarding and device-optimized export flows.
