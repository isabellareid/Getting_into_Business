README
================

## Loading Data

``` r
# Define the dataset to download
dataset <- "fratzcan/usa-house-prices"

# Create a system command to download the dataset
system(paste("kaggle datasets download -d", dataset, "--unzip"))
```

    ## Warning in system(paste("kaggle datasets download -d", dataset, "--unzip")):
    ## error in running command

``` r
# Print confirmation message
print("Dataset downloaded and extracted successfully!")
```

    ## [1] "Dataset downloaded and extracted successfully!"

``` r
# Define the URL for the dataset
dataset_url <- "https://www.kaggle.com/api/v1/datasets/download/fratzcan/usa-house-prices"

# Define the destination file path (you can change this)
destination_file <- "usa-house-prices.zip"

# Download the dataset
download.file(dataset_url, destfile = destination_file, mode = "wb")

# Confirm download
print("Download complete!")
```

    ## [1] "Download complete!"

``` r
# Extract the dataset
unzip(destination_file, exdir = "usa-house-prices")

# List extracted files
list.files("usa-house-prices")
```

    ## [1] "USA Housing Dataset.csv"

``` r
#Import dataset
housing_data <- read.csv ("USA Housing Dataset.csv", stringsAsFactors = FALSE )

getwd()
```

    ## [1] "/Users/isabellareid/Documents/GitHub/Getting_into_Business"

\#Getting summary statistics of the dataset

``` r
head(housing_data)
```

    ##                  date   price bedrooms bathrooms sqft_living sqft_lot floors
    ## 1 2014-05-09 00:00:00  376000        3      2.00        1340     1384      3
    ## 2 2014-05-09 00:00:00  800000        4      3.25        3540   159430      2
    ## 3 2014-05-09 00:00:00 2238888        5      6.50        7270   130017      2
    ## 4 2014-05-09 00:00:00  324000        3      2.25         998      904      2
    ## 5 2014-05-10 00:00:00  549900        5      2.75        3060     7015      1
    ## 6 2014-05-10 00:00:00  320000        3      2.50        2130     6969      2
    ##   waterfront view condition sqft_above sqft_basement yr_built yr_renovated
    ## 1          0    0         3       1340             0     2008            0
    ## 2          0    0         3       3540             0     2007            0
    ## 3          0    0         3       6420           850     2010            0
    ## 4          0    0         3        798           200     2007            0
    ## 5          0    0         5       1600          1460     1979            0
    ## 6          0    0         3       2130             0     2003            0
    ##                       street         city statezip country
    ## 1    9245-9249 Fremont Ave N      Seattle WA 98103     USA
    ## 2           33001 NE 24th St    Carnation WA 98014     USA
    ## 3           7070 270th Pl SE     Issaquah WA 98029     USA
    ## 4             820 NW 95th St      Seattle WA 98117     USA
    ## 5          10834 31st Ave SW      Seattle WA 98146     USA
    ## 6 Cedar to Green River Trail Maple Valley WA 98038     USA

``` r
summary(housing_data)
```

    ##      date               price             bedrooms     bathrooms    
    ##  Length:4140        Min.   :       0   Min.   :0.0   Min.   :0.000  
    ##  Class :character   1st Qu.:  320000   1st Qu.:3.0   1st Qu.:1.750  
    ##  Mode  :character   Median :  460000   Median :3.0   Median :2.250  
    ##                     Mean   :  553063   Mean   :3.4   Mean   :2.163  
    ##                     3rd Qu.:  659125   3rd Qu.:4.0   3rd Qu.:2.500  
    ##                     Max.   :26590000   Max.   :8.0   Max.   :6.750  
    ##   sqft_living       sqft_lot           floors        waterfront      
    ##  Min.   :  370   Min.   :    638   Min.   :1.000   Min.   :0.000000  
    ##  1st Qu.: 1470   1st Qu.:   5000   1st Qu.:1.000   1st Qu.:0.000000  
    ##  Median : 1980   Median :   7676   Median :1.500   Median :0.000000  
    ##  Mean   : 2144   Mean   :  14698   Mean   :1.514   Mean   :0.007488  
    ##  3rd Qu.: 2620   3rd Qu.:  11000   3rd Qu.:2.000   3rd Qu.:0.000000  
    ##  Max.   :10040   Max.   :1074218   Max.   :3.500   Max.   :1.000000  
    ##       view          condition       sqft_above   sqft_basement   
    ##  Min.   :0.0000   Min.   :1.000   Min.   : 370   Min.   :   0.0  
    ##  1st Qu.:0.0000   1st Qu.:3.000   1st Qu.:1190   1st Qu.:   0.0  
    ##  Median :0.0000   Median :3.000   Median :1600   Median :   0.0  
    ##  Mean   :0.2466   Mean   :3.452   Mean   :1831   Mean   : 312.3  
    ##  3rd Qu.:0.0000   3rd Qu.:4.000   3rd Qu.:2310   3rd Qu.: 602.5  
    ##  Max.   :4.0000   Max.   :5.000   Max.   :8020   Max.   :4820.0  
    ##     yr_built     yr_renovated       street              city          
    ##  Min.   :1900   Min.   :   0.0   Length:4140        Length:4140       
    ##  1st Qu.:1951   1st Qu.:   0.0   Class :character   Class :character  
    ##  Median :1976   Median :   0.0   Mode  :character   Mode  :character  
    ##  Mean   :1971   Mean   : 808.4                                        
    ##  3rd Qu.:1997   3rd Qu.:1999.0                                        
    ##  Max.   :2014   Max.   :2014.0                                        
    ##    statezip           country         
    ##  Length:4140        Length:4140       
    ##  Class :character   Class :character  
    ##  Mode  :character   Mode  :character  
    ##                                       
    ##                                       
    ## 

``` r
str(housing_data)
```

    ## 'data.frame':    4140 obs. of  18 variables:
    ##  $ date         : chr  "2014-05-09 00:00:00" "2014-05-09 00:00:00" "2014-05-09 00:00:00" "2014-05-09 00:00:00" ...
    ##  $ price        : num  376000 800000 2238888 324000 549900 ...
    ##  $ bedrooms     : num  3 4 5 3 5 3 4 4 3 4 ...
    ##  $ bathrooms    : num  2 3.25 6.5 2.25 2.75 2.5 2 1 2.5 2.5 ...
    ##  $ sqft_living  : int  1340 3540 7270 998 3060 2130 2520 1940 1350 2160 ...
    ##  $ sqft_lot     : int  1384 159430 130017 904 7015 6969 6000 9533 1250 5298 ...
    ##  $ floors       : num  3 2 2 2 1 2 1 1 3 2.5 ...
    ##  $ waterfront   : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ view         : int  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ condition    : int  3 3 3 3 5 3 3 3 3 4 ...
    ##  $ sqft_above   : int  1340 3540 6420 798 1600 2130 1400 1080 1270 2160 ...
    ##  $ sqft_basement: int  0 0 850 200 1460 0 1120 860 80 0 ...
    ##  $ yr_built     : int  2008 2007 2010 2007 1979 2003 1921 1962 2006 1902 ...
    ##  $ yr_renovated : int  0 0 0 0 0 0 2007 2003 0 0 ...
    ##  $ street       : chr  "9245-9249 Fremont Ave N" "33001 NE 24th St" "7070 270th Pl SE" "820 NW 95th St" ...
    ##  $ city         : chr  "Seattle" "Carnation" "Issaquah" "Seattle" ...
    ##  $ statezip     : chr  "WA 98103" "WA 98014" "WA 98029" "WA 98117" ...
    ##  $ country      : chr  "USA" "USA" "USA" "USA" ...

``` r
#install.packages("DT")
#library(DT)
#datatable(housing_data)

#View(housing_data)

#List column names 
names(housing_data)
```

    ##  [1] "date"          "price"         "bedrooms"      "bathrooms"    
    ##  [5] "sqft_living"   "sqft_lot"      "floors"        "waterfront"   
    ##  [9] "view"          "condition"     "sqft_above"    "sqft_basement"
    ## [13] "yr_built"      "yr_renovated"  "street"        "city"         
    ## [17] "statezip"      "country"

\#UNDERSTANDING THE DATA

``` r
#When was the data acquired? 
min(housing_data$date, na.rm = TRUE)
max(housing_data$date, na.rm = TRUE)

#ANSWER: > min(housing_data$date, na.rm = TRUE)
#[1] "2014-05-02 00:00:00"
#> max(housing_data$date, na.rm = TRUE)
#[1] "2014-07-10 00:00:00"




#Where was the data acquired? (geographical location)
table(housing_data$city)
city_table <-as.data.frame(table(housing_data$city))
colnames(city_table) <-c("City", "Frequency")
head(city_table)
#View(city_table)



# Create a data frame with attribute names and descriptions
attributes_table <- data.frame(
  Attribute = c("date", "price", "bedrooms", "bathrooms", "sqft_living",
                "sqft_lot", "floors", "waterfront", "view", "condition",  "sqft_above", "sqft_basement", "yr_built", "yr_renovated", "street", "city", "statezip", "country"),
 
  Description = c("Date when the house was sold",
                  "Sale price of the house",
                  "Number of bedrooms",
                  "Number of bathrooms",
                  "Living area in square feet",
                  "Lot area in square feet",
                  "Number of floors",
                  "Whether the house is waterfront (1: Yes, 0: No)",
                  "Number of times the house has been viewed",
                  "Condition of the house (1-5 scale)",
                  "Square footage of the house above ground",
                  "Square footage of the basement",
                  "Year the house was built",
                  "Year of renovation (0 if never renovated)",
                  "Street address of house",
                  "City of the house location",
                  "Zip code of the house location",
                  "Country of the house location")
)

# Print the table
print(attributes_table)

#View(attributes_table)
#Finding the data types of each attribute 
print(typeof(housing_data$date))
print(typeof(housing_data$price))
print(typeof(housing_data$bedrooms))
print(typeof(housing_data$bathrooms))
print(typeof(housing_data$sqft_living))
print(typeof(housing_data$sqft_lot))
print(typeof(housing_data$floors))
print(typeof(housing_data$waterfront))
print(typeof(housing_data$view))
print(typeof(housing_data$condition))
print(typeof(housing_data$sqft_above))
print(typeof(housing_data$sqft_basement))
print(typeof(housing_data$yr_built))
print(typeof(housing_data$yr_renovated))
print(typeof(housing_data$statezip))
print(typeof(housing_data$country))
attributes_table$Type = c ( "character", "double", "double", "double",
                "integer", "integer", "double", "integer", "integer", "integer",
                "integer", "integer", "integer", "integer",
                "character", "character", "character", "character")




if (!require("kableExtra")) install.packages("kableExtra", dependencies = TRUE)
if (!require("knitr")) install.packages("knitr", dependencies = TRUE)
library(knitr)


# Generate a well-formatted table
styled_table <- kable(attributes_table, format = "html", caption = "📌 USA Housing Data") %>%
  kable_styling(bootstrap_options = c("striped", "hover", "condensed", "responsive"),
                full_width = F, position = "center") %>%
  column_spec(1, bold = TRUE, color = "black") %>%
  column_spec(2, italic = TRUE, color = "blue") %>%
  column_spec(3, width = "40em") %>%
  row_spec(0, bold = TRUE, color = "white", background = "black")

# Display the table
styled_table


View(attributes_table)


#PART 2
#Summary statistics for each attribute 
# Install required package if not installed
if (!require("psych")) install.packages("psych", dependencies = TRUE)

# Load the library
library(psych)

describe(housing_data)
summary(housing_data$price)
describe(housing_data$price)

# Select only numeric columns
numeric_data <- housing_data[sapply(housing_data, is.numeric)]

# Create a summary table, ensuring NAs are handled correctly
summary_table <- data.frame(
  Attribute = colnames(numeric_data),
  Min = sapply(numeric_data, function(x) min(x, na.rm = TRUE)),
  Max = sapply(numeric_data, function(x) max(x, na.rm = TRUE)),
  Mean = sapply(numeric_data, function(x) mean(x, na.rm = TRUE)),
  Median = sapply(numeric_data, function(x) median(x, na.rm = TRUE)),
  SD = sapply(numeric_data, function(x) sd(x, na.rm = TRUE))
)

# Print the corrected summary table
print(summary_table)

# Melt the summary statistics data for plotting
library(reshape2)
summary_melted <- melt(summary_table, id.vars = "Attribute", variable.name = "Statistic")

library(ggplot2)
# Plot histograms of the statistics
ggplot(summary_melted, aes(x = value)) +
  geom_histogram(binwidth = 1, fill = "blue", color = "black", alpha = 0.7) +
  facet_wrap(~ Statistic, scales = "free") +
  labs(title = "Histogram of Summary Statistics", x = "Value", y = "Frequency") +
  theme_minimal()
```

``` r
#ggplot(housing_data, aes(x = "", y=price)) + geom_boxplot(fill="steelblue", color ="black", outlier.color = "red", outlier.shape = 16, outlier.size = 3) + stat_summary(fun = mean, geom = "point", shape = 18, size = 4, color = "darkred") + labs(title = "Boxplot of Housing Prices", y = "Price ($)") + theme_minimal(base_size = 14) + theme(plot.title = element_text(hjust = 0.5, face = "bold"), axis.text.y = element_text(color = "black"), axis.title.y = element_text(face = "bold"), axis.text.x = element_blank(),axis.ticks.x = element_blank())
```

``` r
#Rename column names as code 
#colnames(attributes_table) = "Code"

#attributes_table2 = attributes_table[-c(1:18)]
#attributes_table = all_of(attributes_table[-c(1, 2, 19, 20)])
```
