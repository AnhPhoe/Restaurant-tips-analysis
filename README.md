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

 


