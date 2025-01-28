# python-airbnb
* Here we are writing with calender file of london
* this is my link https://data.insideairbnb.com/united-kingdom/england/london/2024-09-06/data/calendar.csv.gz
![image](https://github.com/user-attachments/assets/4e344cd1-106d-40ba-ab39-6889be2b6a47)

  ## import the file
  ```python
  import pandas as pd
  calendar = pd.read_csv('/Users/leenafahad/Desktop/calendar.csv')
  ```
  ![image](https://github.com/user-attachments/assets/766fff64-2333-4cda-8a65-a3ea914711cf)
# Qustions
## Q1. Want to know the number of available and unavailable rooms
```python
calendar.available.value_counts()
```
![image](https://github.com/user-attachments/assets/563f7c24-dba1-469c-b78b-f73f7153b82e)
## Q2. Calculates the percentage of available (t) and unavailable (f) dates
```python
availability_percentage = calendar['available'].value_counts(normalize=True) * 100
availability_percentage
```
![image](https://github.com/user-attachments/assets/cccbd212-cbaa-4136-b0f5-d4d002374237)

## Q3. Count the busiest day
```python
busiest_dates = calendar[calendar['available'] == 'f']['date'].value_counts()
print("Busiest Dates:")
print(busiest_dates.head())
```
![image](https://github.com/user-attachments/assets/276ec50d-9561-4d82-ad2b-3f4a8c486583)
## Q4. Plot a bar graph to show availability percentage
```python
import matplotlib.pyplot as plt
availability_percentage.plot(kind='bar', color=['hotpink', 'purple'])
plt.title('Availability Percentages')
plt.ylabel('Percentage')
plt.xlabel('Available (t/f)')
plt.show()
```
<img src="https://github.com/user-attachments/assets/582df64a-9506-40f8-9fbd-c3ac80d844e0" alt="Value Counts Output" width="600"/>

## Q5. Plot the busiest day
```python 
busiest_dates.head(10).plot(kind='bar', color='red')
plt.title('Top 10 Busiest Dates')
plt.ylabel('Number of Listings Unavailable')
plt.xlabel('Date')
plt.show()
```






