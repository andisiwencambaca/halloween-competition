# Maven Halloween Challenge

Bring out the ghosts, bring out the mystery! When all the decorations are up and the costumes are ready, the last thing to prepare is Halloween treats. Halloween candy delights all ages, transforming neighbourhoods into sweet treasure hunts. Now the question is, which candies are the winners?

# Objective

Find the 3 treats you'll give out on Halloween to guarantee that trick-or-treaters of all tastes find something they'll love. 

# Hypothesis

I expect chocolate, peanut or almond flavours to perform better.

# Tools

1. PostgreSQL
2. Git and GitHub
3. LibreOffice Calc
4. Looker Studio

# Data Source

For this challenge, the data I will be analysing is provided by [Maven Analytics](https://mavenanalytics.io/challenges/maven-halloween-challenge/701f06a2-a19b-41e9-95d3-37a0dcc5492f) in CSV format and includes a data dictionary, pictured below, which defines what each column means.

![dictionary](https://github.com/user-attachments/assets/a343528d-40d8-4d81-bd82-c38d97a312d1)

# Data Cleaning/Preparation

- The dataset contains 85 non-null values and 13 columns.
- I put underscores on some columns to make the names easier to read and understand.
- The data was clean and ready for analysis.

# Exploratory Data Analysis

The table below illustrates the overall minimum, maximum, and average values for the numeric columns: win_percent, price_percent, and sugar_percent
![EDA numeric columns](https://github.com/user-attachments/assets/4508e65a-dda3-43b2-ab69-0f61878f3096)

![corr](https://github.com/user-attachments/assets/d0657247-f79b-47f4-a877-a317fa552a1d) Correlation between the numeric fields

![stddev](https://github.com/user-attachments/assets/a07236d7-a29d-472e-88c6-e556ede1bd77) Standard deviation

![count of true vs false](https://github.com/user-attachments/assets/007bc70e-01cc-4ace-9965-a9fed6cb1b46) Count of True vs False

![true vs false %](https://github.com/user-attachments/assets/0654ea53-7b0f-4880-94ea-77ac2c229106) Count of True vs False as a percentage

From the two bar graphs above, we can draw the following summaries:

- Chocolate and fruity candies are the most common.
- Candies that come in a bag or box are also prevalent.
- Bar-type candies are moderately common, with 21 types falling into this category.
- Hard candies, caramel, and peanut/almond candies are less common.
- The least common flavours are nougat and crisped rice/wafer, with only 7 types each.

![min max avg category](https://github.com/user-attachments/assets/b9da607e-4db5-4b02-8bae-3c4f5d83eb15) The minimum, maximum and average win percentage for each category where the boolean value is True.

![contains all](https://github.com/user-attachments/assets/a3dcdb60-71c1-4d67-a0e4-9224bb239b7c) No single candy contains true for all characteristics

![all false](https://github.com/user-attachments/assets/a020731e-5e13-481a-94f9-40218c2f811b) One dime and One quarter have false for all characteristics 

![cheap candy](https://github.com/user-attachments/assets/7403009c-2362-4357-b241-4695013d31bb) Cheapest candy

![expensive candy](https://github.com/user-attachments/assets/609a92ef-4821-49c4-9e1e-d38ddaaef3f5) Expensive candy

![price bins](https://github.com/user-attachments/assets/36fcfb8c-2f10-431d-b9ef-80d9631b1c5e) Count of candy grouped into different price buckets

![high sugar](https://github.com/user-attachments/assets/fb4b8568-0fac-4965-9962-028bfff4b9ef) Candy with the highest sugar

![low sugar](https://github.com/user-attachments/assets/da99c8c3-e840-45e3-bedf-d213b841f123) Candy with the lowest sugar

![high win](https://github.com/user-attachments/assets/b9cf504c-5427-484f-9e8c-bdf2ca9f0724) Candy with the highest win_pecent

![least popular](https://github.com/user-attachments/assets/da67d246-cd85-4b38-8639-098c3c62af64) Candy with the lowest win_percent

# Data Analysis

    -- selecting 2 Halloween treats from the ones with the highest win_percent 
    select competitor_name, chocolate, caramel, peanut_almondy,nougat, crisped_rice_wafer, hard, bar, win_percent
    from candy_data
    order by win_percent DESC
    limit 5;

![treat 1 and 2](https://github.com/user-attachments/assets/7872c2a8-065f-4cb9-9fb5-f3d6e31d9e3a)
The table above is the result of the query above and shows the best-performing chocolate-flavoured candy.

    -- Selection of treat 3
    SELECT competitor_name, fruity, caramel, peanut_almondy, nougat, crisped_rice_wafer, hard, bar, win_percent
    FROM candy_data
    WHERE fruity = TRUE and chocolate = false and peanut_almondy = false
    ORDER BY win_percent DESC
    LIMIT 5;

![treat 3](https://github.com/user-attachments/assets/4424d105-af8d-4c39-9005-9300b26e89e6)
Best-performing fruit-flavoured candy

### Treat #1

**Reese’s Peanut Butter Cup**

The reason I chose this first is because not only does it have a winning percentage of 84.18, but it also contains both chocolate and peanuts, which by far have the highest number of votes.

### Treat #2

**Twix**

Made with a mix of caramel and cookies, covered with chocolate, this bar will delight a large crowd of trick-or-treaters.

Coupled with an 81.64 win percentage, the Twix bar would also suit those who don’t want to eat peanuts or almonds.

### Treat #3

**Starburst**

The third treat to make it into the Halloween bowl is for those who want neither chocolate nor nut but instead a burst of fruitiness. Although fruity candy received fewer votes, it still has a maximum win percentage higher than the overall average.

# Results/Findings

Summary of findings:

- Although 44.71% of the candy in the database has a fruit component, it received fewer votes overall than other flavours.
- None of the fruity treats have chocolate.
- Fewer candies have caramel, peanuts/almonds, or crisped rice/wafers, however, those that do receive higher votes.

# Recommendations

To ensure that trick-or-treaters of all tastes find something they love at your doorstep this Halloween, have a bowl with a mix of soft and hard, bar, and pluribus candy.
