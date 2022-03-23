## Question 1
The American Community Survey distributes downloadable data about United States communities. Download the 2006 microdata survey about housing for the state of Idaho using download.file() from here: 

https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv

and load the data into R. The code book, describing the variable names is here:

https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FPUMSDataDict06.pdf 

How many properties are worth $1,000,000 or more?

```R
fileUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv"
download.file(fileUrl, destfile = "./getdata_data_ss06hid.csv", sep = ",", method = "curl")
communitydata <- read.csv("./getdata_data_ss06hid.csv")
sum(communitydata$VAL == 24, na.rm = TRUE)   # From cookbook, 24 = over $1,000,000

# Answer: 
# 53

```


## Question 2
Use the data you loaded from Question 1. Consider the variable FES in the code book. Which of the "tidy data" principles does this variable violate? 

```R
# Answer: 
# Tidy data has one variable per column. 
```

## Question 3
Download the Excel spreadsheet on Natural Gas Aquisition Program here: 

 https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FDATA.gov_NGAP.xlsx 

Read rows 18-23 and columns 7-15 into R and assign the result to a variable called:

```R
dat
```
What is the value of:
```R
sum(dat$Zip*dat$Ext,na.rm=T)
```
(original data source: http://catalog.data.gov/dataset/natural-gas-acquisition-program)

```R
install.packages("openxlsx")
library(openxlsx)

fileUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FDATA.gov_NGAP.xlsx"
download.file(fileUrl, destfile = "./getdata_data_DATA.gov_NGAP.xlsx", method = "curl")
dat <- read.xlsx("./getdata_data_DATA.gov_NGAP.xlsx", rows = 18:23, cols = 7:15)
sum(dat$Zip*dat$Ext, na.rm=T)

# Answer: 
# 36534720

```



## Question 4
Read the XML data on Baltimore restaurants from here:

https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml 

How many restaurants have zipcode 21231? 

## Question 5
The American Community Survey distributes downloadable data about United States communities. Download the 2006 microdata survey about housing for the state of Idaho using download.file() from here: 

https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06pid.csv

using the fread() command load the data into an R object

```R
DT
```
Which of the following is the fastest way to calculate the average value of the variable
```R
pwgtp15
```
broken down by sex using the data.table package?
