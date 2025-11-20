# -------------------------------

# Assignment 6

# SURYA KANT TIWARI

# 102303737 (3C52)

# -------------------------------

# Q1 create the following dataset with 20 different YEARS and perform the operations using dplyr

install.packages("dplyr")
library(dplyr)

set.seed(123)
years <- 2000:2019
countries <- c("India", "USA", "CHINA", "Brazil", "Germany", "France", "UK", "Canada", "Australia", "Russia")
continents <- c("Asia", "North America", "South America", "Europe", "Australia")

DATASET <- data.frame(
Country = sample(countries, 100, replace = TRUE),
Continent = sample(continents, 100, replace = TRUE),
Year = sample(years, 100, replace = TRUE),
LifeExp = round(runif(100, 50, 85), 1),
Pop = sample(1e6:1e7, 100, replace = TRUE),
GdpPerc = round(runif(100, 1000, 50000), 2)
)

# Q1.1 Unique countries per continent

DATASET %>% group_by(Continent) %>% summarise(UniqueCountries = n_distinct(Country))

# Q1.2 Lowest GDP per capita in Europe for year 2010

year_query <- 2010
DATASET %>% filter(Continent == "Europe", Year == year_query) %>% arrange(GdpPerc) %>% slice(1)

# Q1.3 Average life expectancy across each continent in a given year

DATASET %>% filter(Year == year_query) %>% group_by(Continent) %>% summarise(AverageLifeExp = mean(LifeExp))

# Q1.4 Top 5 countries with highest total GDP

DATASET %>% group_by(Country) %>% summarise(TotalGdp = sum(GdpPerc \* Pop)) %>% arrange(desc(TotalGdp)) %>% slice(1:5)

# Q1.5 Countries and years with LifeExp ≥ 80

DATASET %>% filter(LifeExp >= 80) %>% select(Country, Year, LifeExp)

# Q1.6 Top 10 countries with strongest correlation between LifeExp & GdpPerc

DATASET %>% group_by(Country) %>% summarise(Correlation = cor(LifeExp, GdpPerc)) %>% arrange(desc(abs(Correlation))) %>% slice(1:10)

# Q1.7 Highest avg population outside Asia

DATASET %>% filter(Continent != "Asia") %>% group_by(Year, Continent) %>% summarise(AvgPopulation = mean(Pop)) %>% arrange(desc(AvgPopulation))

# Q1.8 Most consistent populations (lowest SD)

DATASET %>% group_by(Country) %>% summarise(PopulationSD = sd(Pop)) %>% arrange(PopulationSD) %>% slice(1:3)

# Q1.9 Population decreased + LifeExp increased (excluding a year)

exclude_year <- 2015
DATASET %>% arrange(Country, Year) %>% group_by(Country) %>% filter(Year != exclude_year) %>%
mutate(Pop_Change = Pop - lag(Pop), LifeExp_Change = LifeExp - lag(LifeExp)) %>%
filter(Pop_Change < 0 & LifeExp_Change > 0)

# -------------------------------

# Question 2 (Medicine Dataset)

# -------------------------------

set.seed(67)
medicine_data <- data.frame(
MedID = 1:10,
Med_Name = c("Paracetamol","Ibuprofen","Amoxicillin","Cetirizine","Azithromycin",
"Metformin","Atorvastatin","Omeprazole","Amlodipine","Simvastatin"),
Company = c("PharmaA","PharmaB","PharmaC","PharmaD","PharmaE","PharmaF","PharmaG","PharmaH","PharmaI","PharmaJ"),
Manf_year = sample(2015:2023, 10, replace = TRUE),
Exp_date = sample(2016:2028, 10, replace = TRUE),
Quantity_in_stock = sample(50:500, 10, replace = TRUE),
Sales = sample(100:1000, 10, replace = TRUE)
)

write.csv(medicine_data, "DataSet.csv", row.names = FALSE)
medicine_df <- read.csv("DataSet.csv")

# First 4 and last 4 records

head(medicine_df, 4)
tail(medicine_df, 4)

# Correlation between quantity and expiry

cor(medicine_df$Quantity_in_stock, medicine_df$Exp_date)

# Sales vs manufacturing year barplot (ggplot2)

library(ggplot2)
ggplot(medicine_df, aes(x = factor(Manf_year), y = Sales)) + geom_bar(stat = "identity", fill = "skyblue") +
xlab("Manufacturing Year") + ylab("Sales") + ggtitle("Sales vs Manufacturing Year")

# Company with more than one medicine

medicine_df %>% group_by(Company) %>% summarise(MedicineCount = n()) %>% filter(MedicineCount > 1)

# Types of medicine available

unique(medicine_df$Med_Name)

# Boxplot of expiry dates

boxplot(medicine_df$Exp_date, main = "Expiry Dates", ylab = "Expiry Year", col = "lightgreen")

# Average stock

mean(medicine_df$Quantity_in_stock)

# Regression line between Manf_year and Sales

plot(medicine_df$Manf_year, medicine_df$Sales, xlab="Manufacturing Year", ylab="Sales", main="Sales vs Manufacturing Year")
abline(lm(Sales ~ Manf_year, data = medicine_df), col="red")
