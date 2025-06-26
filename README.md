# Restaurant-tips-analysis 
This is  the restaurant tips dataset to show composition plots and visualizations. 
Details are about the tips given to restaurant staff, such as the total bill, tip amount, gender of the person paying, smoking status, day of the week, time of day, and party size that explain explain the relationship between different variables and the tips given.
## Data introduction:
Import libraries: Pandas & Matplotlib.

import pandas as pd
import matplotlib.pyplot as plt

Load data from the following link: https://raw.githubusercontent.com/RusAbk/sca_datasets/main/tips.csv

df = pd.read_csv('https://raw.githubusercontent.com/RusAbk/sca_datasets/main/tips.csv')

df.head()

the result:
![image](https://github.com/user-attachments/assets/c6ce395d-4e23-4368-8929-af36850b6bb7)

## Type data:
### df.info()
![image](https://github.com/user-attachments/assets/e5d2e2f5-e0be-49c8-937f-9bb51b558577)

### Make fix data:
df1 = df.convert_dtypes()
df1.info()
![image](https://github.com/user-attachments/assets/feaa1c0f-b75f-4b46-8aa4-592c383c41b2)

### Show describle data
df1.describe()
![image](https://github.com/user-attachments/assets/b2275d3d-f432-4358-9225-f4b90c914bdd)

## Data analysis:
### Do people who smoke give more tips?
#### Separate smokers and non-smokers:
smokers_df = df1.query('smoker== "Yes"')
smokers_df.sample(5)
![image](https://github.com/user-attachments/assets/5b3032ae-1681-4235-980c-c47fc0137b2b)

non_smokers_df = df1.query('smoker== "No"')
smokers_df.sample(5)
![image](https://github.com/user-attachments/assets/098bc9bd-e474-43e3-958f-2bdc1f389eed)

#### Compare their measures of central tendency:
##### Calculate them for the 'tip' column through the whole dataset and save them into the following variables:
common_tip_min = df1['tip'].min()
common_tip_max = df1['tip'].max()
common_tip_mean = df1['tip'].mean()
common_tip_median = df1['tip'].median()

##### Make a list of values
common_values = [common_tip_min, common_tip_max, common_tip_mean, common_tip_median]
##### Round all the values to 4 decimal places
common_values = map(lambda x: round(x, 4), common_values)

##### Make a dataframe from the list
common_mct = pd.DataFrame(common_values, index=['min', 'max', 'mean', 'median'])
##### Output the dataframe
common_mct

#### Smokers
##### Code
 smokers_tip_min = smokers_df.tip.min()
 smokers_tip_max = smokers_df.tip.max()
 smokers_tip_mean = smokers_df.tip.mean()
 smokers_tip_median = smokers_df.tip.median()
##### Make a list of values
 smokers_values = [smokers_tip_min, smokers_tip_max, smokers_tip_mean, smokers_tip_median]
##### Round all the values to 4 decimal places
 smokers_values = map(lambda x: round(x, 4), smokers_values)
##### Make a dataframe from the list
 smokers_mct = pd.DataFrame(smokers_values, index=['min', 'max', 'mean', 'median'])
##### Output the dataframe
 smokers_mct

 #### Non-smokers
 ##### YOUR CODE
 non_smokers_tip_min = non_smokers_df.tip.min()
 non_smokers_tip_max = non_smokers_df.tip.max()
 non_smokers_tip_mean = non_smokers_df.tip.mean()
 non_smokers_tip_median = non_smokers_df.tip.median()

 ##### Make a list of values
 non_smokers_values = [non_smokers_tip_min, non_smokers_tip_max, non_smokers_tip_mean, non_smokers_tip_median]
 ##### Round all the values to 4 decimal places
 non_smokers_values = map(lambda x: round(x, 4), non_smokers_values)
 ##### Make a dataframe from the list
 non_smokers_mct = pd.DataFrame(non_smokers_values, index=['min', 'max', 'mean', 'median'])
 ##### Output the dataframe
 non_smokers_mct

 #### Conclustion:
 ##### Code:
 all_vals_dict = {
    'Common': {'min': common_tip_min, 'max': common_tip_max, 'mean': common_tip_mean, 'median': common_tip_median},
    'Smokers': {'min': smokers_tip_min, 'max': smokers_tip_max, 'mean': smokers_tip_mean, 'median': smokers_tip_median},
    'Non-smokers': {'min': non_smokers_tip_min, 'max': non_smokers_tip_max, 'mean': non_smokers_tip_mean, 'median': non_smokers_tip_median}
 }
 ##### Make a dataframe
 all_mct = pd.DataFrame(all_vals_dict)
 ##### Output the dataframe
 all_mct

 ## Histogram
 ### Dataset tips histogram
 #### Code:
 plt.figure(figsize =(15, 5))
 plt.hist(df1['tip'], color = '#74b9ff')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Whole dataset tip values')
 plt.grid(True)
 plt.show()

 ![image](https://github.com/user-attachments/assets/d3de28bc-6927-4547-ba96-8f73fb27158d)

 ### Smokers tips histogram
 #### Code:
  plt.figure(figsize =(15, 5))
 plt.hist(smokers_df['tip'], color = '#ff7675')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Smokers tip values')
 plt.grid(True)
 plt.show()
 
 ![image](https://github.com/user-attachments/assets/dbecea52-8711-4979-9df3-46ed9c3e3cf0)

 ### Non-smokers tips histogram
 #### Code:
  plt.figure(figsize =(15, 5))
 plt.hist(non_smokers_df['tip'], color = '#55efc4')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Non-smokers tip values')
 plt.grid(True)
 plt.show()

 ![image](https://github.com/user-attachments/assets/fc57dfb1-3c68-465c-8752-d61005b25ef3)

### 3 charts
#### YOUR CODE
figure, axis = plt.subplots(1,3, figsize=(15,5))

axis[0].hist(df1['tip'], color = '#74b9ff')
axis[0].set_xlabel('Tip value')
axis[0].set_ylabel('Frequency')
axis[0].set_title('Whole dataset tip values')
axis[0].grid(True)

axis[1].hist(smokers_df['tip'], color = '#ff7675')
axis[1].set_xlabel('Tip value')
axis[1].set_ylabel('Frequency')
axis[1].set_title('Smokers tip values')
axis[1].grid(True)

axis[2].hist(non_smokers_df['tip'], color = '#55efc4')
axis[2].set_xlabel('Tip value')
axis[2].set_ylabel('Frequency')
axis[2].set_title('Non-smokers tip values')
axis[2].grid(True)

plt.show()


figure, axis = plt.subplots(1, 3, figsize=(15, 5))

##### Whole dataset
axis[0].hist(df1['tip'], color='#74b9ff')
axis[0].axvline(df1['tip'].median(), color='indigo', linestyle='--', label='Median')
axis[0].set_xlabel('Tip value')
axis[0].set_ylabel('Frequency')
axis[0].set_title('Whole dataset tip values')
axis[0].grid(True)
axis[0].legend()

##### Smokers
axis[1].hist(smokers_df['tip'], color='#ff7675')
axis[1].axvline(smokers_df['tip'].median(), color='indigo', linestyle='--', label='Median')
axis[1].set_xlabel('Tip value')
axis[1].set_ylabel('Frequency')
axis[1].set_title('Smokers tip values')
axis[1].grid(True)
axis[1].legend()

##### Non-smokers
axis[2].hist(non_smokers_df['tip'], color='#55efc4')
axis[2].axvline(non_smokers_df['tip'].median(), color='indigo', linestyle='--', label='Median')
axis[2].set_xlabel('Tip value')
axis[2].set_ylabel('Frequency')
axis[2].set_title('Non-smokers tip values')
axis[2].grid(True)
axis[2].legend()

plt.tight_layout()
plt.show()

![image](https://github.com/user-attachments/assets/71c1d86b-adae-4b0c-94e4-a45428452577)

#### Conclustion:
Insight 1
General conclusion: There is a clear difference in tipping behavior between smokers and non-smokers, both in terms of average values and distribution patterns.
Smokers tend to leave higher tips, with both the mean and median tip values surpassing those of non-smokers.

Insight 2
Distribution Differences The distribution of tip amounts among smokers is more spread out and extends toward higher values, suggesting that a subset of smokers tend to be particularly generous.

In contrast, the distribution for non-smokers is more concentrated around lower tip values, indicating a tendency toward more modest tipping behavior, with relatively few exceeding the $9 mark.

The distribution for the entire dataset represents a blended pattern of the two groups but skews slightly toward the non-smoker profile, likely due to their greater representation in the data.

#### Overall Conclusion:
Smokers generally exhibit a tendency to tip more generously, and their tipping distribution includes higher values more frequently.
Relying solely on the mean can be misleading due to skewed distributions. For more accurate assessment, both the median and distribution shape should be considered.
If a restaurant is evaluating customer segmentation strategies—such as offering targeted incentives—smokers represent a group with the potential to generate higher tip-related revenue.

### Do males give more tips?
#### Separate males and females
##### Code:
females_df = df1.query('sex =="Female"')
females_df.sample(5)
![image](https://github.com/user-attachments/assets/6836b692-c286-45e5-b103-636dc2f4c1e5)

females_df = df1.query('sex =="Female"')
females_df.sample(5)
![image](https://github.com/user-attachments/assets/d8401cd6-417c-4242-994a-65b3a11afa0b)

#### Compare their measures of central tendency:
gender_common_tip_min = df1.tip.min()
gender_common_tip_max = df1.tip.max()
gender_common_tip_mean = df1.tip.mean()
gender_common_tip_median = df1.tip.median()

 ##### Make a list of values
 gender_common_values = [gender_common_tip_min, gender_common_tip_max, gender_common_tip_mean, gender_common_tip_median]
 ##### Round all the values to 4 decimal places
 gender_common_values = map(lambda x: round(x, 4), gender_common_values)
 ##### Make a dataframe from the list
 gender_common_mct = pd.DataFrame(gender_common_values, index=['min', 'max', 'mean', 'median'])
 ##### Output the dataframe
 gender_common_mct

#### Females
females_tip_min = females_df.tip.min()
females_tip_max = females_df.tip.max()
females_tip_mean = females_df.tip.mean()
females_tip_median = females_df.tip.median()

##### Make a list of values
 females_values = [females_tip_min, females_tip_max, females_tip_mean, females_tip_median]
##### Round all the values to 4 decimal places
 females_values = map(lambda x: round(x, 4), females_values)
##### Make a dataframe from the list
 females_mct = pd.DataFrame(females_values, index=['min', 'max', 'mean', 'median'])
##### Output the dataframe
 females_mct

#### Males
 plt.figure(figsize =(15, 5))
 plt.hist(males_df['tip'], color = '#55efc4')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Males tip values')
 plt.grid(True)
 plt.show()
 ![image](https://github.com/user-attachments/assets/1a8b45f0-38f7-45f9-83e5-089f687bfd95)

### 3 charts
#### YOUR CODE
  figure, axis = plt.subplots(1, 3, figsize=(15, 5))
 #Whole dataset
 axis[0].hist(df1['tip'], color='#74b9ff')
 axis[0].axvline(df1['tip'].median(), color='indigo', linestyle='--', label='Median')
 axis[0].set_xlabel('Tip value')
 axis[0].set_ylabel('Frequency')
 axis[0].set_title('Gender dataset tip values')
 axis[0].grid(True)
 axis[0].legend()
 #Females
 axis[1].hist(females_df['tip'], color='#ff7675')
 axis[1].axvline(females_df['tip'].median(), color='indigo', linestyle='--', label='Median')
 axis[1].set_xlabel('Tip value')
 axis[1].set_ylabel('Frequency')
 axis[1].set_title('Females tip values')
 axis[1].grid(True)
 axis[1].legend()
 #Males
 axis[2].hist(males_df['tip'], color='#55efc4')
 axis[2].axvline(males_df['tip'].median(), color='indigo', linestyle='--', label='Median')
 axis[2].set_xlabel('Tip value')
 axis[2].set_ylabel('Frequency')
 axis[2].set_title('Males tip values')
 axis[2].grid(True)
 axis[2].legend()
 
plt.tight_layout()
 plt.show()

![image](https://github.com/user-attachments/assets/86dcc385-f02e-41e7-98b3-2f166d10d889)

#### Conclustion:
1. Insight 1 Males show significantly higher mean and median tip values compared to females. This indicates that the tendency to tip
 generously is relatively widespread within the male group, rather than being driven by a few outliers.
 2. Insight 2 Histograms reveal a wider spread in male tipping behavior, with more frequent occurrences of tips in the 9 range. In
 contrast, female tipping distributions are more concentrated, mostly under the $5 mark.
 6
3. Insight 3: Behavioral Differences May Reflect Social Roles Gender-based differences in tipping behavior may stem from a range of
 factors — such as the payer’s role in group settings, willingness to spend, or social norms regarding generosity. These insights can
 inform strategies for personalized customer engagement or loyalty programs based on gender segmentation.

####  General conclusion:
The data analysis suggests that gender plays a notable role in tipping behavior. Male customers generally leave higher tips than female
customers — both in terms of average (mean) and typical (median) values. This difference may reflect contrasting consumer habits or
spending psychology between the two genders.

### Do weekends bring more tips?
#### Separate weekday and weekend

#####Create a new dataframe weekday_df containing only info about weekday. 
weekday_df = df1.query('day in ["Thur", "Fri"]')
weekday_df.sample(5)
![image](https://github.com/user-attachments/assets/0629496b-c033-4651-9d72-d1e96d348fd9)

##### Also create another one dataframe weekend_df containing only weekend
weekend_df = df1.query('day in ["Sat","Sun"]')
weekend_df.sample(5)
![image](https://github.com/user-attachments/assets/1ad421ce-1e0a-4525-866c-19086b45e5b6)

#### Compare their measures of central tendency
##### Calculate them for the 'tip' column through the whole dataset and save them into the following variables:
 min => day_common_tip_min
 max => day_common_tip_max
 mean => day_common_tip_mean
 median => day_common_tip_median
 
 day_common_tip_min = df1.tip.min()
 day_common_tip_max = df1.tip.max()
 day_common_tip_mean = df1.tip.mean()
 day_common_tip_median = df1.tip.median()
 Let's show the resulting values for whole dataset
 ###### Make a list of values
 day_common_values = [day_common_tip_min, day_common_tip_max, day_common_tip_mean, day_common_tip_median]
 
 ###### Round all the values to 4 decimal places
 day_common_values = map(lambda x: round(x, 4), day_common_values)
 
 ###### Make a dataframe from the list
 day_common_mct = pd.DataFrame(day_common_values, index=['min', 'max', 'mean', 'median'])
 
 ##### Output the dataframe
 day_common_mct
![image](https://github.com/user-attachments/assets/ed7e1122-a517-48bc-a40e-2a9f17763935)

#### Weekday

#####  Do the same taking into account only weekday. Use the following variables:
 min => weekday_tip_min
 max => weekday_tip_max
 mean => weekday_tip_mean
 median => weekday_tip_median
 
 weekday_tip_min = weekday_df.tip.min()
 weekday_tip_max = weekday_df.tip.max()
 weekday_tip_mean = weekday_df.tip.mean()
 weekday_tip_median = weekday_df.tip.median()

##### Make the same dataframe containing the measures of central tendency for smokers
###### Make a list of values
 weekday_values = [weekday_tip_min, weekday_tip_max, weekday_tip_mean, weekday_tip_median]
 
###### Round all the values to 4 decimal places
 weekday_values = map(lambda x: round(x, 4), weekday_values)

###### Make a dataframe from the list
 weekday_mct = pd.DataFrame(weekday_values, index=['min', 'max', 'mean', 'median'])

###### Output the dataframe
 weekday_mct
![image](https://github.com/user-attachments/assets/90340f50-919f-4e27-996d-75e42754f786)

#### Weekend
##### Now repeat it for weekend. Use the following variables:
 min => weekend_tip_min
 max => weekend_tip_max
 mean => weekend_tip_mean
 median => weekend_tip_median
 
 weekend_tip_min = weekend_df.tip.min()
 weekend_tip_max = weekend_df.tip.max()
 weekend_tip_mean = weekend_df.tip.mean()
 weekend_tip_median = weekend_df.tip.median()
 
##### Make a list of values
weekend_values = [weekend_tip_min, weekend_tip_max, weekend_tip_mean, weekend_tip_median]
##### Round all the values to 4 decimal places
weekend_values = map(lambda x: round(x, 4), weekend_values)
##### Make a dataframe from the list
weekend_mct = pd.DataFrame(weekend_values, index=['min', 'max', 'mean', 'median'])
##### Output the dataframe
weekend_mc

#### Conclusion
all_vals_dict = {
    'Day_common': {'min': day_common_tip_min, 'max': day_common_tip_max, 'mean': day_common_tip_mean, 'median': day_common_tip_median},
    'Weekday': {'min': weekday_tip_min, 'max': weekday_tip_max, 'mean': weekday_tip_mean, 'median': weekday_tip_median},
    'Weekdend': {'min': weekend_tip_min, 'max': weekend_tip_max, 'mean': weekend_tip_mean, 'median': weekend_tip_median}
 }
##### Make a dataframe
 all_mct = pd.DataFrame(all_vals_dict)
  Output the dataframe
 all_mct
![image](https://github.com/user-attachments/assets/2aca68d0-b12d-41fd-8439-4a97d455730d)

#####  Insight 1: 
Weekend tip more
Weekday tip no more than $6.7

#### General conclusion:
Given the clear differences observed between weekdays and weekends, the recommendations will focus on leveraging these temporal patterns.
Staffing/Resources: Allocate more staff or resources (e.g., server capacity, customer support) for weekend operations if the variable indicates higher activity or demand.

####  Histogram

 plt.figure(figsize =(15, 5))
 plt.hist(df1['tip'], color = '#74b9ff')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Whole day tip values')
 plt.grid(True)
 plt.show()
 ![image](https://github.com/user-attachments/assets/498a44ea-3292-4241-9cf7-0ef1a93e2e22)

 ####  Weekday tips histogram
 
 plt.figure(figsize =(15, 5))
 plt.hist(weekday_df['tip'], color = '#ff7675')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Weekday tip values')
 plt.grid(True)
![image](https://github.com/user-attachments/assets/c76bc7fe-44d5-4f76-80bc-70f4564af4a5)

####  Weekend tips histogram
 
 plt.figure(figsize =(15, 5))
 plt.hist(weekend_df['tip'], color = '#55efc4')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Weekend tip values')
 plt.grid(True)

 ![image](https://github.com/user-attachments/assets/2221d7c2-9d99-4572-a665-505bdeda0bec)

 ### 3 charts 

  igure, axis = plt.subplots(1, 3, figsize=(15, 5))
 #Whole dataset
 axis[0].hist(df1['tip'], color='#74b9ff')
 axis[0].axvline(df1['tip'].median(), color='indigo', linestyle='--', label='Median')
 axis[0].set_xlabel('Tip value')
 axis[0].set_ylabel('Frequency')
 axis[0].set_title('Whole day tip values')
 axis[0].grid(True)
 axis[0].legend()
 #weekday
 axis[1].hist(weekday_df['tip'], color='#ff7675')
 axis[1].axvline(weekday_df['tip'].median(), color='indigo', linestyle='--', label='Median')
 axis[1].set_xlabel('Tip value')
 axis[1].set_ylabel('Frequency')
 axis[1].set_title('Weekday tip values')
 axis[1].grid(True)
 axis[1].legend()
 #Weekend
 axis[2].hist(weekend_df['tip'], color='#55efc4')
 axis[2].axvline(weekend_df['tip'].median(), color='indigo', linestyle='--', label='Median')
 axis[2].set_xlabel('Tip value')
 axis[2].set_ylabel('Frequency')
 axis[2].set_title('Weekend tip values')
 axis[2].grid(True)
 axis[2].legend()
 plt.tight_layout()
 plt.show()

![image](https://github.com/user-attachments/assets/4fd23fe4-b121-4d7b-bf2f-1ed630615aef)

#### Conclusion
1. Insight 1 Customers dining on weekends leave significantly higher tips than those dining on weekdays. Tip amounts on weekdays rarely
 exceed 6.7, whiletipsabove are much more common on weekends.
 2. Insight 2 The histogram shows that tip values on weekends are more widely spread, with several high-value tips. In contrast, the
 weekday distribution is more concentrated around lower amounts, with fewer outliers.
 3. Insight 3 Customers dining out on weekends are more likely to be in social settings, celebrating occasions, or dining at upscale
 locations. This context leads to more generous tipping behavior, while weekday diners may exhibit more practical and restrained
 spending.

#### General conclusion
The analysis clearly indicates that customers tend to tip more on weekends compared to weekdays. Both mean and median tip values are
 higher on Saturdays and Sundays, and the distribution spreads wider. This may reflect more relaxed spending behavior, social occasions, or a
 leisure-oriented mindset during weekends

### Do dinners bring more tips?
#### Separate lunch and dinner

##### Create a new dataframe lunch_df containing only info about lunch
lunch_df = df1.query('time =="Lunch"')
lunch_df.sample(5)
![image](https://github.com/user-attachments/assets/b4ac03bd-007b-4c7c-9c51-a6753b670aa5)

#### Also create another one dataframe dinner_df containing only weekend.
dinner_df = df1.query('time ==["Dinner"]')
dinner_df.sample(5)
![image](https://github.com/user-attachments/assets/04b93f8c-3391-4970-a377-5631a62cd4c9)

### Compare their measures of central tendency

#### Calculate them for the 'tip' column through the whole dataset and save them into the following variables:
 min => meal_common_tip_min
 max => meal_common_tip_max
 mean => meal_common_tip_mean
 median => meal_common_tip_median

 ##### Make a list of values
 meal_common_values = [meal_common_tip_min, meal_common_tip_max, meal_common_tip_mean, meal_common_tip_median]
 
 ##### Round all the values to 4 decimal places
 meal_common_values = map(lambda x: round(x, 4), meal_common_values)
 
 ##### Make a dataframe from the list
 meal_common_mct = pd.DataFrame(meal_common_values, index=['min', 'max', 'mean', 'median'])
 
 ##### Output the dataframe
 meal_common_mct

 ![image](https://github.com/user-attachments/assets/126178a4-fc8e-4997-a9b9-dc63a7b4e3c9)

 #### Lunch
 Do the same taking into account only smokers. Use the following variables:
 min => lunch_tip_min
 max => lunch_tip_max
 mean => lunch_tip_mean
 median => lunch_tip_median
 
 lunch_tip_min = lunch_df.tip.min()
 lunch_tip_max = lunch_df.tip.max()
 lunch_tip_mean = lunch_df.tip.mean()
 lunch_tip_median = lunch_df.tip.median()

 ##### Make a list of values
 lunch_values = [lunch_tip_min, lunch_tip_max, lunch_tip_mean, lunch_tip_median]
 
 ##### Round all the values to 4 decimal places
 lunch_values = map(lambda x: round(x, 4), lunch_values)
 ##### Make a dataframe from the list
 lunch_mct = pd.DataFrame(lunch_values, index=['min', 'max', 'mean', 'median'])
 ##### Output the dataframe
 lunch_mct
![image](https://github.com/user-attachments/assets/336b6916-7382-457b-be64-12917de8df7a)

#### Dinner
Now repeat it for weekend. Use the following variables:
min => dinner_tip_min
max => dinner_tip_max
mean => dinner_tip_mean
median => dinner_tip_median

 dinner_tip_min = dinner_df.tip.min()
 dinner_tip_max = dinner_df.tip.max()
 dinner_tip_mean = dinner_df.tip.mean()
 dinner_tip_median = dinner_df.tip.median()
 
##### Make the same dataframe containing the measures of central tendency for dinner 
 Make a list of values
 dinner_values = [dinner_tip_min, dinner_tip_max, dinner_tip_mean, dinner_tip_median]
 
##### Round all the values to 4 decimal places
 dinner_values = map(lambda x: round(x, 4), dinner_values)
 
##### Make a dataframe from the list
 dinner_mct = pd.DataFrame(dinner_values, index=['min', 'max', 'mean', 'median'])
 
##### Output the dataframe
 dinner_mct
![image](https://github.com/user-attachments/assets/283401df-54dc-4917-8aac-c7b181dd1712)

#### Conclusion

 all_vals_dict = {
    'Meal': {'min': meal_common_tip_min, 'max': meal_common_tip_max, 'mean': meal_common_tip_mean, 'median': meal_common_tip_median},
    'Lunch': {'min': lunch_tip_min, 'max': lunch_tip_max, 'mean': lunch_tip_mean, 'median': lunch_tip_median},
    'Dinner': {'min': dinner_tip_min, 'max': dinner_tip_max, 'mean': dinner_tip_mean, 'median': dinner_tip_median}
 }
##### Make a dataframe
 all_mct = pd.DataFrame(all_vals_dict)
 
##### Output the dataframe
 all_mct
 
##### Insights
Similar to the weekday/weekend distinction, the 'Lunch' period shows a notably lower maximum value (6.7) compared to 'Meal_common' and 'Dinner' (both 10.0). This indicates that the highest values for this variable are not reached during lunch periods, suggesting a peak or higher ceiling only at dinner times or weekends.

##### General conclusion:
As we already discussed on the last lecture, there are a lot of cases, when comparing the measures of central tendency is not enough.
This is because they only show the most typical values. However, the way data is distributed is equally important. There are situations where
measures of central tendency are exactly the same, but due to different distributions, it is incorrect to say that the datasets are similar.

#### Histogram

 plt.figure(figsize =(15, 5))
 plt.hist(df1['tip'], color = '#74b9ff')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Whole meal dataset tip values')
 plt.grid(True)
 plt.show()

 ![image](https://github.com/user-attachments/assets/4120bfa5-4f8c-401a-8b88-7a0e198aaad7)

 #### Lunch tips histogram

 plt.figure(figsize =(15, 5))
 plt.hist(lunch_df['tip'], color = '#ff7675')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Lunch tip values')
 plt.grid(True)
 plt.show()

 ![image](https://github.com/user-attachments/assets/a982b545-2b21-4fd1-8aac-e96bccfec3d3)

#### Dinner tips histogram

plt.figure(figsize =(15, 5))
 plt.hist(dinner_df['tip'], color = '#55efc4')
 plt.xlabel('Tip value')
 plt.ylabel('Frequency')
 plt.title('Dinner tip values')
 plt.grid(True)
 plt.show()

 ![image](https://github.com/user-attachments/assets/b3114ba3-54f0-4dc5-ba88-64490d9f4a1b)

 #### 3 CHARTS

 #Lunch
axis[1].hist(lunch_df['tip'], color='#ff7675')
axis[1].axvline(lunch_df['tip'].median(), color='indigo', linestyle='--', label='Median')
axis[1].set_xlabel('Tip value')
axis[1].set_ylabel('Frequency')
axis[1].set_title('Lunch tip values')
axis[1].grid(True)figure, axis = plt.subplots(1, 3, figsize=(15, 5))

#Whole dataset
axis[0].hist(df1['tip'], color='#74b9ff')
axis[0].axvline(df1['tip'].median(), color='indigo', linestyle='--', label='Median')
axis[0].set_xlabel('Tip value')
axis[0].set_ylabel('Frequency')
axis[0].set_title('Whole meal dataset tip values')
axis[0].grid(True)
axis[0].legend()

axis[1].legend()

#Dinner
axis[2].hist(dinner_df['tip'], color='#55efc4')
axis[2].axvline(dinner_df['tip'].median(), color='indigo', linestyle='--', label='Median')
axis[2].set_xlabel('Tip value')
axis[2].set_ylabel('Frequency')
axis[2].set_title('Dinner tip values')
axis[2].grid(True)
axis[2].legend()

plt.tight_layout()
plt.show()

![image](https://github.com/user-attachments/assets/f8c92739-7831-4a34-aa83-979bb31439b5)

##### Conclusion
1. Insight 1
Statistics indicate that dinner service receives higher tips than lunch. Lunch tips typically remain in the low-to-mid range, while tips above $7 are more commonly observed at dinner.
2. Insight 2
Histograms show that the dinner tip distribution is wider, with more entries at higher values. In contrast, the lunch tip distribution is more concentrated near the lower values, with very few high-value outliers.
3. Insight 3
Dinner is often associated with social events, romantic outings, or celebratory meals, leading to more generous tipping habits. Lunch, on the other hand, may occur during work breaks and is usually shorter, more practical, and cost-conscious.

##### General conclusion
The analysis reveals that dinner customers tend to tip more generously than those who dine during lunch. Both the mean and median tip values are significantly higher at dinner, and the histogram shows a wider distribution with more high-end tips, suggesting a more relaxed spending behavior in the evening.











