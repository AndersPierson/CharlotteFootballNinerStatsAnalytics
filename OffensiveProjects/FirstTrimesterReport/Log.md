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

(SUB) CLEANING THE DATA:

Once the data was gathered came the challenge of cleaning the data...

The goal here is to be able to join the two datasets of play data on the same play to maximize the amount of information available for each play.
To do so, we must do a bit of coding... first, we must read in the .csv data from our two sources to be able to clean them.
Don't forget to import the associated packages needed to manipulate the data we are using.

Further documentation and all of the code for the project can be found here:
https://app.hex.tech/85371e2a-dc5e-44c9-8028-8d17b3d18e74/hex/5312ec4a-760f-4f44-b83c-3e70825288f2/draft/logic

This link above will take you to the Hex Software Engine which I have had been made available to me by my 5122 - Visual Analytics Professor Chase Romano.
Here you can view the full script of data cleaning and all of the comments associated with it. You'll see the end of the data-cleaning process denoted by a
text box saying "***END OF DATA CLEANING PROCESS***"

After the data has been cleaned and queried by the code I wrote... there is unfortunately one last process needed to truly clean the data. This is a rudimentary process that involves combing through the data to find duplicate joins between our two datasets.

Now while the SQL query I wrote was accurate in joining the two datasets, it was by no means perfect. There were still duplicate joins from the PFF data that ended up in the final query database. Now it is possible to go further in the query by possibly joining the datasets on the additional joint column of gain of yards on a play. However, until someone manages to fix the inevitable occurrence of human error, this would do more harm than good as just missing the appropriate gain by a single yard in data entry can render valuable data missing from the dataset we use to do our analysis. The only foolproof way to go about making sure our data is as accurate as possible after executing the query is by downloading and cleaning the resultant .csv file by hand.

Once we have downloaded and opened the .csv file from the query, we can go in and identify the duplicate rows and get rid of them by deletion.
I chose to highlight the columns "Gain" from the Catapult data and "pff_GAINLOSS" from the PFF data as well as "pff_DISTANCE" as these make it much easier to identify which duplicate values are wrong. YOu are able to discern which is wrong as the gain from the PFF data with not match with the gain from Catapult. If the gain for a row is off by one or two from PFF when cleaning, just treat it as the same play as this attributes to the human error I have already mentioned. Here is an example in case you guys are a bit confused by my explanation.

Catapult data side of the table:
![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/92a29e8a-1064-4759-93d7-88788fde2269)

PFF data side of the table (with the join match pair of dates included):
![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/276c20a0-1021-4a7e-a53c-57536fdd207d)

Once you go through this process and clean the data manually you are left with rows that should look like this:
![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/81e6cc82-edd9-4be7-90b6-3d4627ceb203)
Everything that is highlighted had duplicate entries and has since been cleaned. As you can see, the number for the play sequence now flows quite nicely and looks good!

Once the manual cleaning was finished it looks good to go with analysis! However, as a word of warning, do look over the whole table before you go forward as PFF can have gaps in the data for some games that you'll need to be aware of before any subsequent analysis begins.

Below is an example of such an occurrence. On either side of the joined date columns, denoted by ####### for some reason I don't know why, we can see catapult and PFF data for the Charlotte vs. Georgia State game. But it seems that while there is continuous data on the catapult side, there is no data from PFF to accompany it! The reason as to why always requires further thought and investigation. Upon investigation, the data that is available on PFF for this game is HEAVILY flawed. With some drives outright not being there and instead having plays not worth anything to the offense, such as special teams plays.

![image](https://github.com/AndersPierson/CharlotteFootballNinerStatsAnalytics/assets/77944969/eecf16dd-7619-46bf-aeb7-db3b90b1d9df)

To work around this we will most likely be using only catapult data for anything involving the Georgia State game as trying to use PFF data just destroys any hope of valuable analytics.
