# day-25-how-to-use-pandas-library

## TODO: How to open files in 3 different ways
### 1. Pure way
```
with open("weather_data.csv") as file:
    data = file.readlines()
    print(data)
```
### 2. Use the in-built csv library
```
import csv

with open("weather_data.csv") as file:
    data = csv.reader(file)
    temperatures = []
    for row in data:
        if row[1] != "temp":
            temperatures.append(int(row[1])) # get temperature and append it
    print(temperatures)
``` 
### 3. Use the pandas library
```
import pandas # Need to download this library to use it

data = pandas.read_csv("weather_data.csv")
print(data["temp"]) # Print tempeature data only

# Data to dictionary
data_to_dict = data.to_dict()
print(data_to_dict["temp"])
```

## TODO: Calculate average temperatures
```
# Get the temperate from the CSV and make it to a list
temp_list = data["temp"].to_list()
print(temp_list)
```

### 1. My solution
```
sum_temp = 0
for temp in temp_list:
    sum_temp += temp
avg_temp = sum_temp / len(temp_list)
print(round(avg_temp, 2))
```
### 2. Angela's solution using 'sum' function
```
avg_temp = sum(temp_list)/len(temp_list)
print(round(avg_temp, 2))
```
### 3. Use the Pandas library
```
avg_temp = data["temp"].mean()
print(round(avg_temp, 2))
```

## TODO: Create a dataframe from scratch
```
data_dict = {
    "students": ["Amy", "James", "Angela"],
    "scores": [76, 56, 65]
}
data = pandas.DataFrame(data_dict)
data.to_csv("new_data.csv")
```

## TODO: Squirrel Census data analysis (with Pandas)
```
import pandas
# Get the squirrel data
data = pandas.read_csv("2018_Central_Park_Squirrel_Census_-_Squirrel_Data.csv")

# Get the squirrel's "Primary Fur Color" column
primary_fur_color = data["Primary Fur Color"]

# Sort out by the "Primary Fur Color" and count them
get_primary_fur_color = data.groupby(primary_fur_color).count()["Lat/Long"]
descending_get_primary_fur_color = get_primary_fur_color.sort_values(ascending=False)
print(descending_get_primary_fur_color)

# Save it to "squirrel_count.csv" file
descending_get_primary_fur_color.to_csv("squirrel_count.csv")
```

# Lesson
1. Use the Pandas library to analyze a large set of data
