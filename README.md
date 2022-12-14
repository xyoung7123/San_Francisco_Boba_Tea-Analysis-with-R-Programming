# San_Francisco_Boba_Tea-Analysis-with-R-Programming
Data Wrangling and Visualization with R Programming

## Installing the packages, setting up Rstudio cloud and wrangling packages
install.packages("tidyverse")
library(tidyverse)
install.packages("dplyr")
library("dplyr")

## Importing the csv dataset into R
read.csv("San Francisco Boba Tea Shop.csv")

## saving the dataset
Boba_tea<- read.csv("San Francisco Boba Tea Shop.csv")

## checking the structure and summary of the columns
str(Boba_tea)
head(Boba_tea)
library("ggplot2")


## Updating the tidyverse packages
tidyverse_update()
update.packages()

## create folder to keep your file
dir.create("Data Cleaning")
dir.create("Data Viz")
file.copy("Data_VIsuaalization.R", "Data viz")

## Cleaning Data after installing packages for cleaning
  install.packages("here")
  library("here")
  install.packages("skimr")
  library("skimr")
  install.packages("janitor")
  library("janitor")
  library("dplyr")


## Working with pipes
install.packages("dplyr")
library(dplyr)

## filtering dataset
filtered_boba <- filter(Boba_tea,rating ==5)
View(filtered_boba)

## sorting and arranging dataset
arrange(filtered_boba, city)

## Sorting the rating by mean, max summary
    Boba_tea %>% 
      group_by(rating) %>% 
      summarize(mean_rating = mean(rating))  
      
    
    Boba_tea %>% 
      group_by(city) %>% 
      summarize(max_rating = max(rating))  
    
    
    Boba_tea %>% 
      group_by(city, name) %>% 
      summarize(max_rating = max(rating), mean_rating = mean(rating))  


## applying pipes for filtering and sorting the top rated tea shops and top cities
Filtered_BR5 <- Boba_tea %>% 
  filter(rating>4.5) %>% 
  arrange(rating)
View(Filtered_BR5)

Filter_id <- Boba_tea %>% 
  filter(rating>2.5) %>% 
  arrange(id)
View(Filter_id)

## using pipes to find the mean rating per city above 4.0 rating
Filter_Good_Rating_City <- Boba_tea %>% 
  filter(rating>3.5) %>% 
  group_by(city) %>% 
  summarize(mean_rating = mean(rating, na.rm = T),.group="Good & Excellent Rating")
View(Filter_Good_Rating_City)
    
## Separate the Longitute and latitude
  separate(Boba_tea, lat.long, into = c('lat', 'long'), sep '-')

## code for visualization
ggplot(data = Boba_tea) + geom_bar(mapping = aes(x = rating, color = rating))


## Tea shop count with minimum of 4.0
Boba_tea %>% 
  filter(rating>=4) %>% 
  ggplot(aes(x=name)) + geom_bar(mapping = aes(x = rating), colour = "red") +
  labs(title = "Tea Shop Count with at least rating of 4")

