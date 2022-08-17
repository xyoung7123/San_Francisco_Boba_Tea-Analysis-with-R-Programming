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

## code for visualization
ggplot(data = Boba_tea) + geom_bar(mapping = aes(x = rating, color = rating))
