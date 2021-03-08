# Kickstarting with Excel

## Overview of Project
Data analysis was performed on thousands of crowdfunding projects on Kickstarter by using data collected on campaigns. The data included the campaign name, a description of the campaign, and the monetary goal of the campaign along with the amount pledged which helped determine whether the outcome of the campaign was succeessful, failed, canceled, or live. Additional data included country of origin of campaigns, the day they were launched at and deadline, the number of donors, category and subcategory. 

### Purpose
The purpose of the analysis was to uncover trends among Kickstarter campaigns to help fundraisers make better decisisons as to what category to campaign in and when.

## Analysis and Challenges
The percentage pledged of the goal amount was calculated using the round function and inserted into column O. Average donation per person was calculated by taking the total amount pledged per campaign and dividing it by the total number of donors for that campaign. Some campaigns had 0 donors and thus, were categorized as failed outcomes. However, I had to include the IFERROR function as if I divided the total amount pledged by 0 donors, the cell would enter an error. If error, enter 0. Some campaigns had money pledged with 0 donors because they were self-funded. Using the text-to-column feature, I seperated the categories by their parent category and subcategory and placed them in columnns Q and R. Since the deadline and launched date were in Epoch Unix timestamps, I changed it to a more readable format in columns S and T using the DATE function. Column U had the year the campaign was created in using the YEAR function. I also created a PivotTable and placed it into another sheet on the refined dataset. 

### Analysis of Outcomes Based on Launch Date
Using a PivotTable, I analyzed the total of number of campaigns that occured during each month they were launched, filtered by year and parent category. I specifically chose theatre as the parent category as that has the most amount of successful campaigns. Then using PivotCharts, I created a visual representation of the trend as shown by the [theatre outcomes by month launch date](https://github.com/MuddassirR/kickstarter-analysis/blob/main/Theatre_Outcomes_vs_Launch.png) graph.

### Analysis of Outcomes Based on Goals
After analyzing outcomes by month for the parent category "theatres", I analyzed outcomes based on goals for the subcategory "plays". I categorized goals in $5000 increments then used the COUNTIF function to see if a campaign that belonged in the subcategory "plays" was successful, canceled, or failed depending on the goal range. Next, I created a visual representaion of my findings, as shown by the [outcomes based on goals](https://github.com/MuddassirR/kickstarter-analysis/blob/main/Outcomes_vs_Goals.png) graph.

### Challenges and Difficulties Encountered
For the most part, the analysis was easy to do and was done within 2 hours. Dealing with large datasets can be tedious but the filter option helps tremendously. Another annoyance was having to deal with many worksheets. This could have been solved by placing PivotTables on the same sheet instead of creating multiple. I also struggled a little with the COUNTIF function, in specific, I was getting an error when I wrote =COUNTIFS(Kickstarter!$D:$D, "<1000", Kickstarter!$F:$F, "successful", Kickstarter!$R:$R, "plays") to determine how many campaigns were successful in the subcategory plays that had a goal of less than $1000. However, after 5 minutes... I realized I was spelling successful wrong which is why I kept on getting errors. 

## Results
We see from the theatre outcomes by month launch date graph that Spring and Summer had the most amount of successful campaigns in the theatre parent category. Also, we see from the graph that in the Winter months, the number of successful outcomes dropped sharply. We also see that in November and December specifically, the number of successful outcomes decreased while the number of failed outcomes increased for theatre campaigns. There were no canceled theatre campaigns. This tells us that if one wishes to fundraise in the theatre category, they are better off fundraising in the Spring/Summer as the likelihood of them meeting their monetary goal is more likely. I do not recommend doing theatre campaigns in the Winter.

Furthermore, we also see from the outcomes based on goals graph that the number of successful campaigns in the play subcategory decreases as the goal amount increases. Thus, we also see that the amount of failed outcomes increases as the goal amount increases. However, we see that from $30,000 to $40,000 more players are successful than failed in the plays subcategory. The percentage of successful plays campaigns is larger than the percentage of failed plays campaigns for goals between $0 to $15,000 and $30,000 to $40,000. Thus, we recommend that fundraisers campaign in the theatre parent category, plays subcategory, during the Spring/Summer months and have a goal amount below $15,000 or between $30,000 and $40,000. 

### Limitations of Data & Extensions
The analysis concludes that theatre campaigns are more successful in Spring/Summer. However, that is only correct on Kickstarter. Other fundraising platforms may have different target audiences and fundraisers, resulting in the analysis found in this study not being an accurate representation of the industry as a whole. Furthermore, the study only analyzed the theatre parent category and could have gone more in depth by analyzing trends across parent categories, then subcategories, determining which category is the best for fundraisers. 

