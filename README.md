# Kickstarting with Excel
MSU DS Bootcamp Challenge #1

by David Gornowicz, davidgornowicz@gmail.com

## Overview of Project
Using Pivot tables and countifs arrays to visualize and gain insights into kickstarter fundraising outcomes based on relevant paramenters (Launch Date and Fundraising Goal).

### Purpose
Louise was fundraising for her theatrical play, Fever. After almost reaching her goal in a short time, she wanted to know how different campaigns performed in relation to their launch dates and their funding goals.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
A pivot table was used to populate the outcomes based on launch date. The count of each outcome was analyzed by month and filterable by "Parent Category" and "Year". I filtered based on the "Theater" parent category and did not filter based on year.

<img width="453" alt="Outcomes based on date table" src="https://user-images.githubusercontent.com/102050273/174140807-7896957e-da00-4bde-9c48-ea0a50552501.png">

An accompanying line pivot chart was used to visualize the outcomes based on launch date. The Y-Axis is "Count of Outcomes" and the X-Axis is "Month". The data was filtered by "Theater" parent category.

<img width="471" alt="Theater_Outcomes_vs_Launch" src="https://user-images.githubusercontent.com/102050273/174141456-516f0c31-8bb7-46a0-bb94-2608f09a63f6.png">

### Analysis of Outcomes Based on Goals
A countifs array was used to populate outcomes based on fundraising goals. A new sheet with 8 columns and 12 rows was created. The Columns were:
- Goal
- Succesful
- Failed
- Canceled
- Total
- Succesful%
- Failed%
- Canceled%

The Rows were the "Goal" grouped ranges:
- Less than 1000
- 1000 to 4999
- 5000 to 9999
- 10000 to 14999
- 15000 to 19999
- 20000 to 24999
- 25000 to 29999
- 30000 to 34999
- 35000 to 39999
- 40000 to 44999
- 45000 to 50000
- 50000 or More

The "Succesful", "Failed", and "Canceled" coloumns were populated using the countifs function. The following is the function for the "Succesful Outcomes" and Less than 1000" Cell.
> =COUNTIFS(Kickstarter!$D$2:$D$4115, "<1000",Kickstarter!$F$2:$F$4115,"successful",Kickstarter!$P$2:$P$4115, "plays")

For the rows with two range constraints, an additional criteria was added to define the upper and lower bounds
> =COUNTIFS(Kickstarter!$D$2:$D$4115, "<5000", Kickstarter!$D$2:$D$4115, ">=1000", Kickstarter!$F$2:$F$4115,"successful",Kickstarter!$P$2:$P$4115, "plays")

The following table was the result of filling the rest of the countifs columns and then finding the perecentage of outcomes.
<img width="746" alt="Outcomes vs goal table" src="https://user-images.githubusercontent.com/102050273/174145305-3aa020bf-a1e5-44db-956c-6525cc95a3c0.png">

Finally, a line graph was used to compare the percentage outcomes by Goal.
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/102050273/174145680-1d98693a-b404-4339-9a88-b6de4e99c429.png)

### Challenges and Difficulties Encountered
- I found that filling out the countifs array criterias with manual text such as "succesful" and "<1000" was a bit tedious and that I could have used cell references to make the process quicker and more reliable. 
- Getting the kickstarter data to group by month when using the "Date Created Conversion" column to populate the "Outcomes based on Launch Date" pivot table was a bit unintuitive. 

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
  
  - There are more theater kickstarter campaigns launched during the middle of the year (May-August) than the rest of the year (September-April)
  - May is the most common month to launch a theater kickstarter campaign (163) and the month with the most succesful campaigns (111). This is a 68% success rate. This is contrast to December with 75 total campaigns and 37 succesful campaigns - a 54% success rate. 
  - Therefore, the Summer, and specifically May, has been the best time to launch a Theater Kickstarter campaign.
  
- What can you conclude about the Outcomes based on Goals?
  
  - The vast majority of Theater/Play kickstarter campaigns have a goal below $5000 (76%).
  - The two goal ranges with the highest percentage of succesful campaigns are "Less than 1000" (76%) and "1000 to 4999" (73%). The average success rate for all Theater/Play kickstarter campaigns is 66%.
  
  - As the goal range increases, the success rate generally declines. However, the sample size also decreases at a much greater rate - increasing the variance and decreasing the reliability of the success rate signal.

- What are some limitations of this dataset?
  
  - The primary limitation of this dataset was limited sample sizes after several layers of filtering and grouping. This was most obvious in the "Outcomes Based on Goals" analysis where sample sizes for every grouping more than 15000 where a fraction of the sample sizes for the lower goal ranges. For example, there are 186, 534, and 169 campgaigns for the "Less than 1000", "1000 to 4999", and "5000 to 9999" goal ranges, respectively. However there are 6, 3, and 1 campaigns for the "35000 to 39999", "40000 to 44999", and "45000 to 49999" goal ranges.

- What are some other possible tables and/or graphs that we could create?
  
  - In addition to analyzing outcomes by Goal Amount, it could be useful to create a table and/or graph for Outcomes by Average donation. It could also be useful analyze the relationship between Goal Amount and Average Donation.
  - In addition to analyzing outcomes by Launch Date, it could be useful to measure and analyze outcomes by Campaign duration.
