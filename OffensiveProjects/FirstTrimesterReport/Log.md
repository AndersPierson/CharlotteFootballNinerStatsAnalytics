Author: Anders Pierson (Offensive Team Lead - Fall 2023)

What follows is an account of the process of completing this project from start to finish. 
This is for future generations of the Football NinerStats team to look back on and learn from as well as use as a guideline.

(MAIN) DATA GATHERING AND CLEANING PROCESS:

The first step of any good project in analytics is getting your data together and looking neat.
To do this I needed to gather my data from two sources, from PFF(Pro Football Focus) and from our in-house system in the front office (Catapult).

  (SUB) GATHERING DATA FROM PFF:
  
  First, you need to log into your PFF Ultimate account. Your login is not your own, but rather from a member of the coaching staff or a team lead (offense or defense). Be sure to ask them for it if you need to       grab data.
  Next, you will come to the starting page of the PFF system. From here you will want to filter the available plays to your needs. (Filtering access underscored in red)
  ![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/3bf49ef7-0bb7-4794-885d-c32d5457ba47)

  Once you click on "Filters" you can see you can get very specific with how you filter the data available.
  ![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/aa62e41b-830c-4361-9cd3-33bd4ac9a2fc)

  For the purposes of this project, we will show a relatively basic filtering process in order to access offensive data.

  To access data for Charlotte Football and only Charlotte Football, keep "League" set to "NCAA". Then for "Season/Weeks" filter to the specific season you are working in and select the weeks you need to include.     An example of the first trimester of the 2023 season is shown below.
  ![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/52cc80c8-30c6-424b-9fdc-488c29b959ab)

  After filtering the timeframe of the data you are looking for you need to pick what team we are focusing on. We look for Charlotte as an example, but you can find any team by selecting either the "Offense",   "Defense", or "Entire Team" filter based on your needs.
![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/502a522b-c990-43f0-b992-eb373b0aa410)

From here you can select the games you want from your filtered search under the "Games" filter. Once you close the filter you will see reports that include data filtered to your specific requests and you are welcome to delve as deep as you want into these for the reports you create from what is available!
![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/85246483-6137-4c70-8c2c-edc6da4ec37c)

To be more specific, if you want to view raw data and/or video, look at the top right corner of the page just below your account menu. You will see three buttons titled "Save", "Share" and "# plays".
If you want to save your filter to come back to later just click on the "Save" button. This will be saved under the "Collections" menu which is right next to your account menu. The save option will let you name your filter as well as make any additional notes and share the filter with other PFF Ultimate Users.
![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/12be3784-12ea-45fb-8c18-757c1e1c5c8f)

Clicking on the "# plays" button lets you view videos of the plays from the games you have filtered. I recommend using the "Quick Video" option to view plays as it is quick and easy. To actually download play data click on the "Play Feed CSV" option to directly download a .csv file of your filtered data to your system.

![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/eaa06af9-547d-4b9c-bdef-81e916ebf1cd)

(SUB) GATHERING DATA FROM CATAPULT: [CLASSIFIED UNTIL FURTHER NOTICE]

Once the data was gathered came the challenge of cleaning the data...
