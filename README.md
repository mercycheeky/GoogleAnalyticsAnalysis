# Google Merchandise Store Analytics
Analyzed Google Analytics data of a sample dataset that contains obfuscated  GA360  data for August 1,2017 from the Google merchandise store[https://app.datacamp.com/workspace/external-link?url=https%3A%2F%2Fshop.googlemerchandisestore.com%2F].
The data provides insights into what drives sales into the ecommerce website.
- This data is typical of what you'd see on an ecommerce website🖥️. It contains session data with traffic source, location and transaction information.Other data has been anonymized. The data is available for in a publicly available Google Sheet📇.
-  We will be using a combination of SQL and Python to analyze this dataset, getting more insights into what is driving sales on this particular day.

  ## Requirements, packages and installations🔩
  - Datacamp workspace.
  - A workspace is an AI-enabled data notebook to discover and share insights effectively. Every workspace runs in a fully-managed, cloud-hosted environment with R / Python, built-in support for SQL and all commonly used data science packages pre-installed. If you need more, you can easily install additional packages.
  - Workspace makes connecting to external databases a breeze. Set up the connection once and access data in any workspace. Write your query in a SQL cell; the result will be available as a data frame so you can continue your analysis.
  - Basic understanding of SQL concepts
  - Python

## Getting started🏴
- Download the dataset which is inform of a google sheet and copy it to your google drive.
- click the plus icon on the top left space near the word databases.
  ![Screenshot 2024-03-28 210521](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/101febbf-8fc3-4565-b36a-68039462aa38)
- 
choose the google sheets option

![Screenshot 2024-03-28 210707](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/79de50bf-99bd-4be6-b683-bd2008a3c012)
 Choose a sheet
 
![Screenshot 2024-03-28 210822](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/0a8f38c7-b079-4ce9-a2ef-0be4e5eff690)
Now ga_sample_data google sheets shows up as a connected database.

![Screenshot 2024-03-28 211015](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/fbd2cf60-02d1-4104-9401-51391fcd1e98)

- Import session data using basic sql statement 
- select * from ga_sessions
  ![Screenshot 2024-03-28 211259](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/f0533d92-56b9-48b8-9183-0e55b34a357d)

  - the datacamp workspace is an integration of sql and python languages. So the google sheet automatically available as a dataframe.
  
![Screenshot 2024-03-28 211437](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/c97e5938-85ba-417f-88ee-5b6cf236cf90)

## Import packages🗳️


