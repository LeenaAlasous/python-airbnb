
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

<img src="https://github.com/user-attachments/assets/276ec50d-9561-4d82-ad2b-3f4a8c486583" alt="Value Counts Output" width="600"/>


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
<img src="https://github.com/user-attachments/assets/01c01ce8-e6c9-46bb-a6bb-6d3865d9b08d" alt="Value Counts Output" width="600"/>

# Download listings dataset of London 
Click here to downloed 👉🏻 https://data.insideairbnb.com/united-kingdom/england/london/2024-09-06/visualisations/listings.csv

```python
import pandas as pd
listings = pd.read_csv('/Users/leenafahad/Desktop/listings.csv')
listings
```
<img src="https://github.com/user-attachments/assets/b9444ab0-2d07-4171-a784-c1f56aa56175" alt="Value Counts Output" width="600"/>

```python
listings.columns
```
<img src="https://github.com/user-attachments/assets/908f1c68-66ae-4ff4-9310-51fc9f07145c" alt="Value Counts Output" width="600"/>

# Room type and price is given seperately
```python
import matplotlib.pyplot as plt
price_by_room = listings.groupby('room_type')['price'].mean()
print(price_by_room)

# Plot price by room type
price_by_room.plot(kind='bar', color='hotpink')
plt.title('Average Price by Room Type')
plt.ylabel('Average Price')
plt.xlabel('Room Type')

plt.show()
```
<img src="https://github.com/user-attachments/assets/006a1e98-9fec-45be-af62-4f3ceae0c21b" alt="Value Counts Output" width="600"/>

# Which are the top 10 neighborhoods with the most listings?
```python
neighborhood_counts = listings['neighbourhood'].value_counts().head(10)
print("Top 10 Neighborhoods by Listings:")
print(neighborhood_counts)

# Plot neighborhoods with most listings
neighborhood_counts.plot(kind='bar', color='lightcoral')
plt.title('Top 10 Neighborhoods by Listings')
plt.ylabel('Number of Listings')
plt.xlabel('Neighborhood')
plt.xticks(rotation=90)
plt.show()
```

<img src="https://github.com/user-attachments/assets/7fe531e7-c146-4acb-9293-f5d0f61bb63f" alt="Value Counts Output" width="600"/>

# Geographical Distribution of Listings (Price Colored)
```python
import matplotlib.pyplot as plt
import seaborn as sns
plt.figure(figsize=(10, 6))
sns.scatterplot(data=listings, x='longitude', y='latitude', hue='price', palette='viridis', size='price', sizes=(10, 200))
plt.title('Geographical Distribution of Listings (Price Colored)')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.show()
```
<img src="https://github.com/user-attachments/assets/fce80807-b902-41f2-b19c-47e685d8bd99" alt="Value Counts Output" width="600"/>

# Let us see the listings on a real map
```python
import folium
from folium.plugins import HeatMap
import pandas as pd


hawaii_data = listings[['latitude', 'longitude', 'price']]  # Example, you may add more columns

# Create a base map centered around Hawaii
m = folium.Map(location=[51.50890223091212, -0.13550076130101943], zoom_start=10)

# Prepare the data for the heatmap
heat_data = [[row['latitude'], row['longitude']] for index, row in hawaii_data.iterrows()]

# Add the heatmap to the map
HeatMap(heat_data).add_to(m)

# Save the map as an HTML file to view in a browser
m.save('London_heatmap.html')

# If you're using Jupyter Notebook, you can display the map directly in the notebook:
m
```
![image](https://github.com/user-attachments/assets/40b5429c-9039-4478-a954-c7c5ca7f840d)

 # Additional questions 
 ## Q1. Find the average price of listings by neighborhood
 ```python
average_price_by_neighborhood = listings.groupby('neighbourhood')['price'].mean().sort_values(ascending=False)
print("Average Price by Neighborhood:")
print(average_price_by_neighborhood.head(10))
```

git commit --amend


 
 




















