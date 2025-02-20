README
================

## Loading Data

``` r
# Define the dataset to download
dataset <- "fratzcan/usa-house-prices"

# Create a system command to download the dataset
system(paste("kaggle datasets download -d", dataset, "--unzip"))

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

#getwd()
```

# Getting summary statistics of the dataset

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

\#UNDERSTANDING THE DATA \# Calculating Min and Max

The dataset has the min date of 2014-05-02 00:00:00

``` r
#Where was the data acquired? (geographical location)
table(housing_data$city)
```

    ## 
    ##             Algona             Auburn Beaux Arts Village           Bellevue 
    ##                  1                162                  1                260 
    ##      Black Diamond            Bothell             Burien          Carnation 
    ##                  7                 30                 64                 18 
    ##         Clyde Hill          Covington         Des Moines             Duvall 
    ##                 10                 39                 52                 39 
    ##           Enumclaw          Fall City        Federal Way           Issaquah 
    ##                 28                  9                131                162 
    ##            Kenmore               Kent           Kirkland   Lake Forest Park 
    ##                 58                167                166                 33 
    ##       Maple Valley             Medina      Mercer Island             Milton 
    ##                 90                 11                 81                  2 
    ##          Newcastle      Normandy Park         North Bend            Pacific 
    ##                 31                 16                 45                  6 
    ##            Preston         Ravensdale            Redmond             Renton 
    ##                  2                  4                209                261 
    ##          Sammamish             SeaTac            Seattle          Shoreline 
    ##                158                 29               1415                112 
    ##          Skykomish         Snoqualmie    Snoqualmie Pass            Tukwila 
    ##                  2                 65                  1                 28 
    ##             Vashon        Woodinville       Yarrow Point 
    ##                 28                103                  4

``` r
city_table <-as.data.frame(table(housing_data$city))
colnames(city_table) <-c("City", "Frequency")
head(city_table)
```

    ##                 City Frequency
    ## 1             Algona         1
    ## 2             Auburn       162
    ## 3 Beaux Arts Village         1
    ## 4           Bellevue       260
    ## 5      Black Diamond         7
    ## 6            Bothell        30

``` r
#View(city_table)
```

``` r
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
```

    ##        Attribute                                     Description
    ## 1           date                    Date when the house was sold
    ## 2          price                         Sale price of the house
    ## 3       bedrooms                              Number of bedrooms
    ## 4      bathrooms                             Number of bathrooms
    ## 5    sqft_living                      Living area in square feet
    ## 6       sqft_lot                         Lot area in square feet
    ## 7         floors                                Number of floors
    ## 8     waterfront Whether the house is waterfront (1: Yes, 0: No)
    ## 9           view       Number of times the house has been viewed
    ## 10     condition              Condition of the house (1-5 scale)
    ## 11    sqft_above        Square footage of the house above ground
    ## 12 sqft_basement                  Square footage of the basement
    ## 13      yr_built                        Year the house was built
    ## 14  yr_renovated       Year of renovation (0 if never renovated)
    ## 15        street                         Street address of house
    ## 16          city                      City of the house location
    ## 17      statezip                  Zip code of the house location
    ## 18       country                   Country of the house location

``` r
str(housing_data, list.len = ncol(housing_data))
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
#View(attributes_table)
#Finding the data types of each attribute 
print(typeof(housing_data$date))
```

    ## [1] "character"

``` r
print(typeof(housing_data$price))
```

    ## [1] "double"

``` r
print(typeof(housing_data$bedrooms))
```

    ## [1] "double"

``` r
print(typeof(housing_data$bathrooms))
```

    ## [1] "double"

``` r
print(typeof(housing_data$sqft_living))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$sqft_lot))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$floors))
```

    ## [1] "double"

``` r
print(typeof(housing_data$waterfront))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$view))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$condition))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$sqft_above))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$sqft_basement))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$yr_built))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$yr_renovated))
```

    ## [1] "integer"

``` r
print(typeof(housing_data$statezip))
```

    ## [1] "character"

``` r
print(typeof(housing_data$country))
```

    ## [1] "character"

``` r
attributes_table$Type = c ( "character", "double", "double", "double",
                "integer", "integer", "double", "integer", "integer", "integer",
                "integer", "integer", "integer", "integer",
                "character", "character", "character", "character")





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
```

<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
📌 USA Housing Data
</caption>
<thead>
<tr>
<th style="text-align:left;font-weight: bold;color: white !important;background-color: black !important;">
Attribute
</th>
<th style="text-align:left;font-weight: bold;color: white !important;background-color: black !important;">
Description
</th>
<th style="text-align:left;font-weight: bold;color: white !important;background-color: black !important;">
Type
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
date
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Date when the house was sold
</td>
<td style="text-align:left;width: 40em; ">
character
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
price
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Sale price of the house
</td>
<td style="text-align:left;width: 40em; ">
double
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
bedrooms
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Number of bedrooms
</td>
<td style="text-align:left;width: 40em; ">
double
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
bathrooms
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Number of bathrooms
</td>
<td style="text-align:left;width: 40em; ">
double
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
sqft_living
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Living area in square feet
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
sqft_lot
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Lot area in square feet
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
floors
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Number of floors
</td>
<td style="text-align:left;width: 40em; ">
double
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
waterfront
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Whether the house is waterfront (1: Yes, 0: No)
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
view
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Number of times the house has been viewed
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
condition
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Condition of the house (1-5 scale)
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
sqft_above
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Square footage of the house above ground
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
sqft_basement
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Square footage of the basement
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
yr_built
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Year the house was built
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
yr_renovated
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Year of renovation (0 if never renovated)
</td>
<td style="text-align:left;width: 40em; ">
integer
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
street
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Street address of house
</td>
<td style="text-align:left;width: 40em; ">
character
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
city
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
City of the house location
</td>
<td style="text-align:left;width: 40em; ">
character
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
statezip
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Zip code of the house location
</td>
<td style="text-align:left;width: 40em; ">
character
</td>
</tr>
<tr>
<td style="text-align:left;font-weight: bold;color: black !important;">
country
</td>
<td style="text-align:left;font-style: italic;color: blue !important;">
Country of the house location
</td>
<td style="text-align:left;width: 40em; ">
character
</td>
</tr>
</tbody>
</table>

``` r
#View(attributes_table)
```

``` r
#PART 2
#Summary statistics for each attribute 

describe(housing_data)
```

    ##               vars    n      mean        sd    median   trimmed       mad  min
    ## date*            1 4140     38.69     17.46     40.00     38.89     20.76    1
    ## price            2 4140 553062.88 583686.45 460000.00 489266.09 237216.00    0
    ## bedrooms         3 4140      3.40      0.90      3.00      3.37      1.48    0
    ## bathrooms        4 4140      2.16      0.78      2.25      2.12      0.74    0
    ## sqft_living      5 4140   2143.64    957.48   1980.00   2043.78    845.08  370
    ## sqft_lot         6 4140  14697.64  35876.84   7676.00   8441.01   4119.40  638
    ## floors           7 4140      1.51      0.53      1.50      1.48      0.74    1
    ## waterfront       8 4140      0.01      0.09      0.00      0.00      0.00    0
    ## view             9 4140      0.25      0.79      0.00      0.00      0.00    0
    ## condition       10 4140      3.45      0.68      3.00      3.33      0.00    1
    ## sqft_above      11 4140   1831.35    861.38   1600.00   1723.73    726.47  370
    ## sqft_basement   12 4140    312.29    464.35      0.00    225.19      0.00    0
    ## yr_built        13 4140   1970.81     29.81   1976.00   1973.07     34.10 1900
    ## yr_renovated    14 4140    808.37    979.38      0.00    759.14      0.00    0
    ## street*         15 4140   2042.56   1178.46   2041.50   2043.07   1515.22    1
    ## city*           16 4140     25.91     11.65     32.00     27.20      4.45    1
    ## statezip*       17 4140     39.83     20.96     42.00     40.29     26.69    1
    ## country*        18 4140      1.00      0.00      1.00      1.00      0.00    1
    ##                       max       range  skew kurtosis      se
    ## date*               68.00       67.00 -0.13    -1.12    0.27
    ## price         26590000.00 26590000.00 24.75  1008.37 9071.51
    ## bedrooms             8.00        8.00  0.39     0.99    0.01
    ## bathrooms            6.75        6.75  0.53     1.24    0.01
    ## sqft_living      10040.00     9670.00  1.46     4.63   14.88
    ## sqft_lot       1074218.00  1073580.00 11.77   237.14  557.59
    ## floors               3.50        2.50  0.52    -0.58    0.01
    ## waterfront           1.00        1.00 11.42   128.49    0.00
    ## view                 4.00        4.00  3.29    10.03    0.01
    ## condition            5.00        4.00  0.98     0.18    0.01
    ## sqft_above        8020.00     7650.00  1.40     3.09   13.39
    ## sqft_basement     4820.00     4820.00  1.59     3.49    7.22
    ## yr_built          2014.00      114.00 -0.50    -0.68    0.46
    ## yr_renovated      2014.00     2014.00  0.39    -1.85   15.22
    ## street*           4079.00     4078.00  0.00    -1.20   18.32
    ## city*               43.00       42.00 -0.74    -0.82    0.18
    ## statezip*           77.00       76.00 -0.15    -1.13    0.33
    ## country*             1.00        0.00   NaN      NaN    0.00

``` r
summary(housing_data$price)
```

    ##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
    ##        0   320000   460000   553063   659125 26590000

``` r
describe(housing_data$price)
```

    ##    vars    n     mean       sd median  trimmed    mad min      max    range
    ## X1    1 4140 553062.9 583686.4 460000 489266.1 237216   0 26590000 26590000
    ##     skew kurtosis      se
    ## X1 24.75  1008.37 9071.51

``` r
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
```

    ##                   Attribute  Min         Max         Mean    Median
    ## price                 price    0 26590000.00 5.530629e+05 460000.00
    ## bedrooms           bedrooms    0        8.00 3.400483e+00      3.00
    ## bathrooms         bathrooms    0        6.75 2.163043e+00      2.25
    ## sqft_living     sqft_living  370    10040.00 2.143639e+03   1980.00
    ## sqft_lot           sqft_lot  638  1074218.00 1.469764e+04   7676.00
    ## floors               floors    1        3.50 1.514130e+00      1.50
    ## waterfront       waterfront    0        1.00 7.487923e-03      0.00
    ## view                   view    0        4.00 2.466184e-01      0.00
    ## condition         condition    1        5.00 3.452415e+00      3.00
    ## sqft_above       sqft_above  370     8020.00 1.831351e+03   1600.00
    ## sqft_basement sqft_basement    0     4820.00 3.122874e+02      0.00
    ## yr_built           yr_built 1900     2014.00 1.970814e+03   1976.00
    ## yr_renovated   yr_renovated    0     2014.00 8.083684e+02      0.00
    ##                         SD
    ## price         5.836865e+05
    ## bedrooms      9.039388e-01
    ## bathrooms     7.847330e-01
    ## sqft_living   9.574816e+02
    ## sqft_lot      3.587684e+04
    ## floors        5.349409e-01
    ## waterfront    8.621861e-02
    ## view          7.906195e-01
    ## condition     6.785332e-01
    ## sqft_above    8.613829e+02
    ## sqft_basement 4.643492e+02
    ## yr_built      2.980794e+01
    ## yr_renovated  9.793805e+02

``` r
library(fBasics)
colnames(housing_data) <- c("Date", "Price", "# of Bedrooms", "# of Bathrooms", "Sqft of Living", "Sqft of Lot", "# of Floors", "Waterfront", "View", "Condition", "Sqft Above Ground", "Sqft of Basement", "Year Built", "Year Rennovated", "Street", "City", "Zipcode", "Country")

Attribute <- colnames(housing_data)  # Extract column names
Code <- seq_along(Attribute)  # Create a sequence for the codes

# Create a proper data frame
df <- data.frame(Code, Attribute, stringsAsFactors = FALSE)

# Generate a well-formatted table
df %>% 
  kable(caption = "Attribute Codes for Housing Data", longtable = TRUE) %>%
  kable_styling(latex_options = c("hold_position", "repeat_header")) %>%
  row_spec(0, bold = TRUE) %>%
  column_spec(1, bold = TRUE)
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Attribute Codes for Housing Data
</caption>
<thead>
<tr>
<th style="text-align:right;font-weight: bold;">
Code
</th>
<th style="text-align:left;font-weight: bold;">
Attribute
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;font-weight: bold;">
1
</td>
<td style="text-align:left;">
Date
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
2
</td>
<td style="text-align:left;">
Price
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
3
</td>
<td style="text-align:left;">
\# of Bedrooms
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
4
</td>
<td style="text-align:left;">
\# of Bathrooms
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
5
</td>
<td style="text-align:left;">
Sqft of Living
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
6
</td>
<td style="text-align:left;">
Sqft of Lot
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
7
</td>
<td style="text-align:left;">
\# of Floors
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
8
</td>
<td style="text-align:left;">
Waterfront
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
9
</td>
<td style="text-align:left;">
View
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
10
</td>
<td style="text-align:left;">
Condition
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
11
</td>
<td style="text-align:left;">
Sqft Above Ground
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
12
</td>
<td style="text-align:left;">
Sqft of Basement
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
13
</td>
<td style="text-align:left;">
Year Built
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
14
</td>
<td style="text-align:left;">
Year Rennovated
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
15
</td>
<td style="text-align:left;">
Street
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
16
</td>
<td style="text-align:left;">
City
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
17
</td>
<td style="text-align:left;">
Zipcode
</td>
</tr>
<tr>
<td style="text-align:right;font-weight: bold;">
18
</td>
<td style="text-align:left;">
Country
</td>
</tr>
</tbody>
</table>

``` r
colnames (housing_data) = Code
housing_data3 = housing_data[-c(1:18)]
housing_data2 = housing_data[-c(1, 15:18)]
bstats = basicStats (housing_data2)[c("Mean", "Stdev", "Median", "Minimum", "Maximum",
"NAs"), ]
m<-matrix(1:ncol(bstats), 3)
for (i in 1:ncol(m)) {
cat(kable(bstats[, m[, i]], "latex", booktabs = TRUE, digits = 2, ), "\\newline")
}
```

    ## 
    ## \begin{tabular}{lrrr}
    ## \toprule
    ##   & X2 & X3 & X4\\
    ## \midrule
    ## Mean & 553062.9 & 3.4 & 2.16\\
    ## Stdev & 583686.4 & 0.9 & 0.78\\
    ## Median & 460000.0 & 3.0 & 2.25\\
    ## Minimum & 0.0 & 0.0 & 0.00\\
    ## Maximum & 26590000.0 & 8.0 & 6.75\\
    ## \addlinespace
    ## NAs & 0.0 & 0.0 & 0.00\\
    ## \bottomrule
    ## \end{tabular} \newline
    ## \begin{tabular}{lrrr}
    ## \toprule
    ##   & X5 & X6 & X7\\
    ## \midrule
    ## Mean & 2143.64 & 14697.64 & 1.51\\
    ## Stdev & 957.48 & 35876.84 & 0.53\\
    ## Median & 1980.00 & 7676.00 & 1.50\\
    ## Minimum & 370.00 & 638.00 & 1.00\\
    ## Maximum & 10040.00 & 1074218.00 & 3.50\\
    ## \addlinespace
    ## NAs & 0.00 & 0.00 & 0.00\\
    ## \bottomrule
    ## \end{tabular} \newline
    ## \begin{tabular}{lrrr}
    ## \toprule
    ##   & X8 & X9 & X10\\
    ## \midrule
    ## Mean & 0.01 & 0.25 & 3.45\\
    ## Stdev & 0.09 & 0.79 & 0.68\\
    ## Median & 0.00 & 0.00 & 3.00\\
    ## Minimum & 0.00 & 0.00 & 1.00\\
    ## Maximum & 1.00 & 4.00 & 5.00\\
    ## \addlinespace
    ## NAs & 0.00 & 0.00 & 0.00\\
    ## \bottomrule
    ## \end{tabular} \newline
    ## \begin{tabular}{lrrr}
    ## \toprule
    ##   & X11 & X12 & X13\\
    ## \midrule
    ## Mean & 1831.35 & 312.29 & 1970.81\\
    ## Stdev & 861.38 & 464.35 & 29.81\\
    ## Median & 1600.00 & 0.00 & 1976.00\\
    ## Minimum & 370.00 & 0.00 & 1900.00\\
    ## Maximum & 8020.00 & 4820.00 & 2014.00\\
    ## \addlinespace
    ## NAs & 0.00 & 0.00 & 0.00\\
    ## \bottomrule
    ## \end{tabular} \newline
    ## \begin{tabular}{lrrr}
    ## \toprule
    ##   & X14 & X2 & X3\\
    ## \midrule
    ## Mean & 808.37 & 553062.9 & 3.4\\
    ## Stdev & 979.38 & 583686.4 & 0.9\\
    ## Median & 0.00 & 460000.0 & 3.0\\
    ## Minimum & 0.00 & 0.0 & 0.0\\
    ## Maximum & 2014.00 & 26590000.0 & 8.0\\
    ## \addlinespace
    ## NAs & 0.00 & 0.0 & 0.0\\
    ## \bottomrule
    ## \end{tabular} \newline

``` r
print(kable(summary(bstats), format = "pipe", digits = 2))
```

    ## 
    ## 
    ## |   |      X2         |      X3      |      X4       |      X5        |      X6        |      X7       |      X8         |      X9       |     X10       |     X11       |     X12       |     X13       |     X14       |
    ## |:--|:----------------|:-------------|:--------------|:---------------|:---------------|:--------------|:----------------|:--------------|:--------------|:--------------|:--------------|:--------------|:--------------|
    ## |   |Min.   :       0 |Min.   :0.000 |Min.   :0.0000 |Min.   :    0.0 |Min.   :      0 |Min.   :0.0000 |Min.   :0.000000 |Min.   :0.0000 |Min.   :0.0000 |Min.   :   0.0 |Min.   :   0.0 |Min.   :   0.0 |Min.   :   0.0 |
    ## |   |1st Qu.:  115000 |1st Qu.:0.226 |1st Qu.:0.1962 |1st Qu.:  516.9 |1st Qu.:   2398 |1st Qu.:0.6512 |1st Qu.:0.000000 |1st Qu.:0.0000 |1st Qu.:0.7589 |1st Qu.: 492.8 |1st Qu.:   0.0 |1st Qu.: 497.4 |1st Qu.:   0.0 |
    ## |   |Median :  506531 |Median :1.952 |Median :1.4739 |Median : 1468.7 |Median :  11187 |Median :1.2500 |Median :0.003744 |Median :0.1233 |Median :2.0000 |Median :1230.7 |Median : 156.1 |Median :1935.4 |Median : 404.2 |
    ## |   |Mean   : 4697792 |Mean   :2.551 |Mean   :1.9913 |Mean   : 2581.9 |Mean   : 188851 |Mean   :1.3415 |Mean   :0.182284 |Mean   :0.8395 |Mean   :2.1885 |Mean   :2113.8 |Mean   : 932.8 |Mean   :1315.1 |Mean   : 633.6 |
    ## |   |3rd Qu.:  576031 |3rd Qu.:3.300 |3rd Qu.:2.2283 |3rd Qu.: 2102.7 |3rd Qu.:  30582 |3rd Qu.:1.5106 |3rd Qu.:0.066536 |3rd Qu.:0.6546 |3rd Qu.:3.3393 |3rd Qu.:1773.5 |3rd Qu.: 426.3 |3rd Qu.:1974.7 |3rd Qu.: 936.6 |
    ## |   |Max.   :26590000 |Max.   :8.000 |Max.   :6.7500 |Max.   :10040.0 |Max.   :1074218 |Max.   :3.5000 |Max.   :1.000000 |Max.   :4.0000 |Max.   :5.0000 |Max.   :8020.0 |Max.   :4820.0 |Max.   :2014.0 |Max.   :2014.0 |

``` r
summary_table <- as.data.frame(summary(bstats))
#gt(summary_table)
```

``` r
summary_stats <- bstats %>%
  summarise(across(everything(), list(
    Min = ~min(.x, na.rm = TRUE),
    Q1 = ~quantile(.x, 0.25, na.rm = TRUE),
    Median = ~median(.x, na.rm = TRUE),
    Mean = ~mean(.x, na.rm = TRUE),
    Q3 = ~quantile(.x, 0.75, na.rm = TRUE),
    Max = ~max(.x, na.rm = TRUE),
    SD = ~sd(.x, na.rm = TRUE)
  ), .names = "{.col}_{.fn}"))

summary_long <- summary_stats %>%
  pivot_longer(cols = everything(), names_to = c("Attribute", "Statistic"), names_sep = "_") %>%
  pivot_wider(names_from = "Attribute", values_from = "value") %>%
  mutate(across(where(is.numeric), ~round(.x, 2)))

print(summary_long)
```

    ## # A tibble: 7 × 14
    ##   Statistic     X2    X3    X4     X5     X6    X7    X8    X9   X10   X11   X12
    ##   <chr>      <dbl> <dbl> <dbl>  <dbl>  <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    ## 1 Min       0       0     0        0  0       0     0     0     0       0     0 
    ## 2 Q1        1.15e5  0.23  0.2    517. 2.40e3  0.65  0     0     0.76  493.    0 
    ## 3 Median    5.07e5  1.95  1.47  1469. 1.12e4  1.25  0     0.12  2    1231.  156.
    ## 4 Mean      4.70e6  2.55  1.99  2582. 1.89e5  1.34  0.18  0.84  2.19 2114.  933.
    ## 5 Q3        5.76e5  3.3   2.23  2103. 3.06e4  1.51  0.07  0.65  3.34 1774.  426.
    ## 6 Max       2.66e7  8     6.75 10040  1.07e6  3.5   1     4     5    8020  4820 
    ## 7 SD        1.07e7  3.04  2.53  3752. 4.34e5  1.21  0.4   1.58  1.93 2977. 1914.
    ## # ℹ 2 more variables: X13 <dbl>, X14 <dbl>

``` r
summary_long <- summary_stats %>%
  pivot_longer(cols = everything(), names_to = c("Attribute", "Statistic"), names_sep = "_") %>%
  pivot_wider(names_from = "Attribute", values_from = "value") %>%
  mutate(across(where(is.numeric), ~round(.x, 2)))
print(summary_long)
```

    ## # A tibble: 7 × 14
    ##   Statistic     X2    X3    X4     X5     X6    X7    X8    X9   X10   X11   X12
    ##   <chr>      <dbl> <dbl> <dbl>  <dbl>  <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    ## 1 Min       0       0     0        0  0       0     0     0     0       0     0 
    ## 2 Q1        1.15e5  0.23  0.2    517. 2.40e3  0.65  0     0     0.76  493.    0 
    ## 3 Median    5.07e5  1.95  1.47  1469. 1.12e4  1.25  0     0.12  2    1231.  156.
    ## 4 Mean      4.70e6  2.55  1.99  2582. 1.89e5  1.34  0.18  0.84  2.19 2114.  933.
    ## 5 Q3        5.76e5  3.3   2.23  2103. 3.06e4  1.51  0.07  0.65  3.34 1774.  426.
    ## 6 Max       2.66e7  8     6.75 10040  1.07e6  3.5   1     4     5    8020  4820 
    ## 7 SD        1.07e7  3.04  2.53  3752. 4.34e5  1.21  0.4   1.58  1.93 2977. 1914.
    ## # ℹ 2 more variables: X13 <dbl>, X14 <dbl>

``` r
summary_long %>%
  kable(caption = "Summary Statistics for Housing Data", longtable = TRUE, align = "c") %>%
  kable_styling(latex_options = c("hold_position", "repeat_header")) %>%
  row_spec(0, bold = TRUE) %>%  # Bold column names (first row)
  row_spec(1:nrow(summary_long), font_size = 12) %>%  # Adjust font size for summary rows
  column_spec(1, bold = TRUE)   # Bold the first column (Statistic names)
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>
Summary Statistics for Housing Data
</caption>
<thead>
<tr>
<th style="text-align:center;font-weight: bold;">
Statistic
</th>
<th style="text-align:center;font-weight: bold;">
X2
</th>
<th style="text-align:center;font-weight: bold;">
X3
</th>
<th style="text-align:center;font-weight: bold;">
X4
</th>
<th style="text-align:center;font-weight: bold;">
X5
</th>
<th style="text-align:center;font-weight: bold;">
X6
</th>
<th style="text-align:center;font-weight: bold;">
X7
</th>
<th style="text-align:center;font-weight: bold;">
X8
</th>
<th style="text-align:center;font-weight: bold;">
X9
</th>
<th style="text-align:center;font-weight: bold;">
X10
</th>
<th style="text-align:center;font-weight: bold;">
X11
</th>
<th style="text-align:center;font-weight: bold;">
X12
</th>
<th style="text-align:center;font-weight: bold;">
X13
</th>
<th style="text-align:center;font-weight: bold;">
X14
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center;font-size: 12px;font-weight: bold;">
Min
</td>
<td style="text-align:center;font-size: 12px;">
0.0
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
</tr>
<tr>
<td style="text-align:center;font-size: 12px;font-weight: bold;">
Q1
</td>
<td style="text-align:center;font-size: 12px;">
115000.0
</td>
<td style="text-align:center;font-size: 12px;">
0.23
</td>
<td style="text-align:center;font-size: 12px;">
0.20
</td>
<td style="text-align:center;font-size: 12px;">
516.87
</td>
<td style="text-align:center;font-size: 12px;">
2397.50
</td>
<td style="text-align:center;font-size: 12px;">
0.65
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.76
</td>
<td style="text-align:center;font-size: 12px;">
492.85
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
497.36
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
</tr>
<tr>
<td style="text-align:center;font-size: 12px;font-weight: bold;">
Median
</td>
<td style="text-align:center;font-size: 12px;">
506531.4
</td>
<td style="text-align:center;font-size: 12px;">
1.95
</td>
<td style="text-align:center;font-size: 12px;">
1.47
</td>
<td style="text-align:center;font-size: 12px;">
1468.74
</td>
<td style="text-align:center;font-size: 12px;">
11186.82
</td>
<td style="text-align:center;font-size: 12px;">
1.25
</td>
<td style="text-align:center;font-size: 12px;">
0.00
</td>
<td style="text-align:center;font-size: 12px;">
0.12
</td>
<td style="text-align:center;font-size: 12px;">
2.00
</td>
<td style="text-align:center;font-size: 12px;">
1230.69
</td>
<td style="text-align:center;font-size: 12px;">
156.14
</td>
<td style="text-align:center;font-size: 12px;">
1935.41
</td>
<td style="text-align:center;font-size: 12px;">
404.18
</td>
</tr>
<tr>
<td style="text-align:center;font-size: 12px;font-weight: bold;">
Mean
</td>
<td style="text-align:center;font-size: 12px;">
4697791.5
</td>
<td style="text-align:center;font-size: 12px;">
2.55
</td>
<td style="text-align:center;font-size: 12px;">
1.99
</td>
<td style="text-align:center;font-size: 12px;">
2581.85
</td>
<td style="text-align:center;font-size: 12px;">
188851.08
</td>
<td style="text-align:center;font-size: 12px;">
1.34
</td>
<td style="text-align:center;font-size: 12px;">
0.18
</td>
<td style="text-align:center;font-size: 12px;">
0.84
</td>
<td style="text-align:center;font-size: 12px;">
2.19
</td>
<td style="text-align:center;font-size: 12px;">
2113.79
</td>
<td style="text-align:center;font-size: 12px;">
932.77
</td>
<td style="text-align:center;font-size: 12px;">
1315.10
</td>
<td style="text-align:center;font-size: 12px;">
633.62
</td>
</tr>
<tr>
<td style="text-align:center;font-size: 12px;font-weight: bold;">
Q3
</td>
<td style="text-align:center;font-size: 12px;">
576030.6
</td>
<td style="text-align:center;font-size: 12px;">
3.30
</td>
<td style="text-align:center;font-size: 12px;">
2.23
</td>
<td style="text-align:center;font-size: 12px;">
2102.73
</td>
<td style="text-align:center;font-size: 12px;">
30582.04
</td>
<td style="text-align:center;font-size: 12px;">
1.51
</td>
<td style="text-align:center;font-size: 12px;">
0.07
</td>
<td style="text-align:center;font-size: 12px;">
0.65
</td>
<td style="text-align:center;font-size: 12px;">
3.34
</td>
<td style="text-align:center;font-size: 12px;">
1773.51
</td>
<td style="text-align:center;font-size: 12px;">
426.33
</td>
<td style="text-align:center;font-size: 12px;">
1974.70
</td>
<td style="text-align:center;font-size: 12px;">
936.63
</td>
</tr>
<tr>
<td style="text-align:center;font-size: 12px;font-weight: bold;">
Max
</td>
<td style="text-align:center;font-size: 12px;">
26590000.0
</td>
<td style="text-align:center;font-size: 12px;">
8.00
</td>
<td style="text-align:center;font-size: 12px;">
6.75
</td>
<td style="text-align:center;font-size: 12px;">
10040.00
</td>
<td style="text-align:center;font-size: 12px;">
1074218.00
</td>
<td style="text-align:center;font-size: 12px;">
3.50
</td>
<td style="text-align:center;font-size: 12px;">
1.00
</td>
<td style="text-align:center;font-size: 12px;">
4.00
</td>
<td style="text-align:center;font-size: 12px;">
5.00
</td>
<td style="text-align:center;font-size: 12px;">
8020.00
</td>
<td style="text-align:center;font-size: 12px;">
4820.00
</td>
<td style="text-align:center;font-size: 12px;">
2014.00
</td>
<td style="text-align:center;font-size: 12px;">
2014.00
</td>
</tr>
<tr>
<td style="text-align:center;font-size: 12px;font-weight: bold;">
SD
</td>
<td style="text-align:center;font-size: 12px;">
10728194.6
</td>
<td style="text-align:center;font-size: 12px;">
3.04
</td>
<td style="text-align:center;font-size: 12px;">
2.53
</td>
<td style="text-align:center;font-size: 12px;">
3751.67
</td>
<td style="text-align:center;font-size: 12px;">
433939.73
</td>
<td style="text-align:center;font-size: 12px;">
1.21
</td>
<td style="text-align:center;font-size: 12px;">
0.40
</td>
<td style="text-align:center;font-size: 12px;">
1.58
</td>
<td style="text-align:center;font-size: 12px;">
1.93
</td>
<td style="text-align:center;font-size: 12px;">
2976.73
</td>
<td style="text-align:center;font-size: 12px;">
1914.43
</td>
<td style="text-align:center;font-size: 12px;">
1007.85
</td>
<td style="text-align:center;font-size: 12px;">
807.46
</td>
</tr>
</tbody>
</table>
