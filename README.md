README
================

## Importing the Dataset

``` r
# Define the dataset to download
dataset <- "fratzcan/usa-house-prices"

# Create a system command to download the dataset
system(paste("kaggle datasets download -d", dataset, "--unzip"))
```

``` r
# Define the URL for the dataset
dataset_url <- "https://www.kaggle.com/api/v1/datasets/download/fratzcan/usa-house-prices"

# Define the destination file path (you can change this)
destination_file <- "usa-house-prices.zip"

# Download the dataset
download.file(dataset_url, destfile = destination_file, mode = "wb")

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

    ##  [1] "date"          "price"         "bedrooms"      "bathrooms"    
    ##  [5] "sqft_living"   "sqft_lot"      "floors"        "waterfront"   
    ##  [9] "view"          "condition"     "sqft_above"    "sqft_basement"
    ## [13] "yr_built"      "yr_renovated"  "street"        "city"         
    ## [17] "statezip"      "country"

## Understanding the Data

### When was the data acquired?

The data was gathered over the period of time from May 2, 2014 and July
10, 2014. The data was uploaded to Kaggle. The date this data was first
accessed for this analysis was February 12, 2025. The dataset has the
min date of 2014-05-02 00:00:00

### Where was the data acquired?

The data was acquired from Zillow from several different cities in
Washington State. The data was then uploaded to Kaggle. Below is a table
that displays the number of houses in each city in Washington:

| City               | Frequency |
|:-------------------|----------:|
| Algona             |         1 |
| Auburn             |       162 |
| Beaux Arts Village |         1 |
| Bellevue           |       260 |
| Black Diamond      |         7 |
| Bothell            |        30 |
| Burien             |        64 |
| Carnation          |        18 |
| Clyde Hill         |        10 |
| Covington          |        39 |
| Des Moines         |        52 |
| Duvall             |        39 |
| Enumclaw           |        28 |
| Fall City          |         9 |
| Federal Way        |       131 |
| Issaquah           |       162 |
| Kenmore            |        58 |
| Kent               |       167 |
| Kirkland           |       166 |
| Lake Forest Park   |        33 |
| Maple Valley       |        90 |
| Medina             |        11 |
| Mercer Island      |        81 |
| Milton             |         2 |
| Newcastle          |        31 |
| Normandy Park      |        16 |
| North Bend         |        45 |
| Pacific            |         6 |
| Preston            |         2 |
| Ravensdale         |         4 |
| Redmond            |       209 |
| Renton             |       261 |
| Sammamish          |       158 |
| SeaTac             |        29 |
| Seattle            |      1415 |
| Shoreline          |       112 |
| Skykomish          |         2 |
| Snoqualmie         |        65 |
| Snoqualmie Pass    |         1 |
| Tukwila            |        28 |
| Vashon             |        28 |
| Woodinville        |       103 |
| Yarrow Point       |         4 |

### How was the data acquired?

### What are the attributes of this dataset?

The dataset contains eighteen different attributes. This section
presents the attributes that appear in the dataset. First, we specify
what each attribute is with descriptions and their data type. Then, we
provide a codebook that specifies a number with each individual
attribute. These numbers will be useful in determining which attribute
is correlated with the summary statistics displayed in the last table.

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
```

``` r
# Add a column corresponding to each of the attributes data type 
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

## Summary Statistics

``` r
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
```

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
