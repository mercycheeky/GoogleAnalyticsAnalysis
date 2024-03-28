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
```
import pandas as pd
import plotly.express as px
```
## Clean the data⚔️
```
# we can make a copy first inorder to make changes that won't override the original dataframe and cause major repercussions incase we didn't want the changes anymore. Also imporatant to attach a time zone to your time stamp.
df_clean=df.copy()
df_clean['visitStartTime']=pd.to_datetime(df_clean['visitStartTime'],unit='s').dt.tz_localize('UTC')
df_clean
```
This is after we looked at the datatypes of the different variables and found out the column visitStarttime is of type integer instead of timestamp
![Screenshot 2024-03-28 213207](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/a251c6e1-1150-47d3-9a28-1ed69d6978d4)

After changing datatype and adding a timezone:
![Screenshot 2024-03-28 213437](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/3cce147e-510a-4860-8d13-2ddc769f800a)

## Explore the data👩‍🚀
- Use the predefined plotting function to explore different grouped session counts as either a bar chart or a pie chart.
  ```
  def plot_sessions_per_group(df, group, viz_type='bar'):
    sessions_per_group = df.groupby(group).size().reset_index(name='sessions').sort_values(by='sessions')
    if viz_type == 'bar':
        return px.bar(sessions_per_group,
                      x=group,
                      y='sessions',
                      title=f'Number of sessions per {group}',
                      text='sessions')
    elif viz_type == 'pie':
        return px.pie(sessions_per_group,
                      names=group,
                      values='sessions',
                      title=f'Distribution of sessions per {group}')
    else:
        raise ValueError("viz_type can only be 'bar' or 'pie'")
  ```
  
- Explore after asking different questions related to what we would want to know
  for instance we can plot the number of sessions on  the ecommerce website, per continent. Use the function plot_sessions_per_group and take the dataframe and continent as inputs.
  ```
  plot_sessions_per_group(df_clean,'continent')
  ```
  ![Screenshot 2024-03-28 220345](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/ea0a5fbe-4cc0-4d1f-834f-3f7fe183506a)
   Distribution of sessions per device category and set the visualization type to pie
  ```
  plot_sessions_per_group(df_clean,'deviceCategory', viz_type='pie')
  ```
  ![Screenshot 2024-03-28 220537](https://github.com/mercycheeky/GoogleAnalyticsAnalysis/assets/56400871/8f2dcf01-ee7e-47fc-a692-628c7f4ac20b)

  
