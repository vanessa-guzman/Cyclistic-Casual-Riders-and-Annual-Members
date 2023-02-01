Cyclistic- Casual Riders and Annual Members
================
2022-07-05

# Cyclistic: Casual Riders and Annual Members

## Installing Packages

``` r
install.packages('tidyverse', repos = "http://cran.us.r-project.org")
```

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/21/536vjlp524v0yj99lmnbb4z00000gn/T//RtmpKoK0j7/downloaded_packages

``` r
install.packages('dplyr', repos = "http://cran.us.r-project.org")
```

    ## 
    ##   There is a binary version available but the source version is later:
    ##       binary source needs_compilation
    ## dplyr 1.0.10  1.1.0              TRUE

    ## installing the source package 'dplyr'

    ## Warning in install.packages("dplyr", repos = "http://cran.us.r-project.org"):
    ## installation of package 'dplyr' had non-zero exit status

``` r
install.packages('lubridate', repos = "http://cran.us.r-project.org")
```

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/21/536vjlp524v0yj99lmnbb4z00000gn/T//RtmpKoK0j7/downloaded_packages

## Loading Packages

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.4.0      ✔ purrr   1.0.1 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.3.0      ✔ stringr 1.5.0 
    ## ✔ readr   2.1.3      ✔ forcats 1.0.0 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(dplyr)
library(lubridate)
```

    ## 
    ## Attaching package: 'lubridate'
    ## 
    ## The following objects are masked from 'package:base':
    ## 
    ##     date, intersect, setdiff, union

## Importing the Data

The data can be located
[here](https://divvy-tripdata.s3.amazonaws.com/index.html). The data
analyzed was data from the past 12 months, made available before July
5th, 2022.

``` r
Jun_2021 <- read.csv("202106-divvy-tripdata.csv")
Jul_2021 <- read.csv("202107-divvy-tripdata.csv")
Aug_2021 <- read.csv("202108-divvy-tripdata.csv")
Sep_2021 <- read.csv("202109-divvy-tripdata.csv")
Oct_2021 <- read.csv("202110-divvy-tripdata.csv")
Nov_2021 <- read.csv("202111-divvy-tripdata.csv")
Dec_2021 <- read.csv("202112-divvy-tripdata.csv")
Jan_2022 <- read.csv("202201-divvy-tripdata.csv")
Feb_2022 <- read.csv("202202-divvy-tripdata.csv")
Mar_2022 <- read.csv("202203-divvy-tripdata.csv")
Apr_2022 <- read.csv("202204-divvy-tripdata.csv")
May_2022 <- read.csv("202205-divvy-tripdata.csv")
```

## Inspecting and Cleaning the Data Before Combining the Files

The functions **colnames** and **str** will be used to ensure everything
is consistent before combining the files.

``` r
colnames(Jun_2021)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Jul_2021)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Aug_2021)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Sep_2021) 
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Oct_2021)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Nov_2021)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Dec_2021)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Jan_2022)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Feb_2022)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Mar_2022)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(Apr_2022)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
colnames(May_2022)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(Jun_2021)
```

    ## 'data.frame':    729595 obs. of  13 variables:
    ##  $ ride_id           : chr  "99FEC93BA843FB20" "06048DCFC8520CAF" "9598066F68045DF2" "B03C0FE48C412214" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : chr  "2021-06-13 14:31:28" "2021-06-04 11:18:02" "2021-06-04 09:49:35" "2021-06-03 19:56:05" ...
    ##  $ ended_at          : chr  "2021-06-13 14:34:11" "2021-06-04 11:24:19" "2021-06-04 09:55:34" "2021-06-03 20:21:55" ...
    ##  $ start_station_name: chr  "" "" "" "" ...
    ##  $ start_station_id  : chr  "" "" "" "" ...
    ##  $ end_station_name  : chr  "" "" "" "" ...
    ##  $ end_station_id    : chr  "" "" "" "" ...
    ##  $ start_lat         : num  41.8 41.8 41.8 41.8 41.8 ...
    ##  $ start_lng         : num  -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num  41.8 41.8 41.8 41.8 41.8 ...
    ##  $ end_lng           : num  -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...

``` r
str(Jul_2021)
```

    ## 'data.frame':    822410 obs. of  13 variables:
    ##  $ ride_id           : chr  "0A1B623926EF4E16" "B2D5583A5A5E76EE" "6F264597DDBF427A" "379B58EAB20E8AA5" ...
    ##  $ rideable_type     : chr  "docked_bike" "classic_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : chr  "2021-07-02 14:44:36" "2021-07-07 16:57:42" "2021-07-25 11:30:55" "2021-07-08 22:08:30" ...
    ##  $ ended_at          : chr  "2021-07-02 15:19:58" "2021-07-07 17:16:09" "2021-07-25 11:48:45" "2021-07-08 22:23:32" ...
    ##  $ start_station_name: chr  "Michigan Ave & Washington St" "California Ave & Cortez St" "Wabash Ave & 16th St" "California Ave & Cortez St" ...
    ##  $ start_station_id  : chr  "13001" "17660" "SL-012" "17660" ...
    ##  $ end_station_name  : chr  "Halsted St & North Branch St" "Wood St & Hubbard St" "Rush St & Hubbard St" "Carpenter St & Huron St" ...
    ##  $ end_station_id    : chr  "KA1504000117" "13432" "KA1503000044" "13196" ...
    ##  $ start_lat         : num  41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num  -87.6 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ end_lat           : num  41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num  -87.6 -87.7 -87.6 -87.7 -87.7 ...
    ##  $ member_casual     : chr  "casual" "casual" "member" "member" ...

``` r
str(Aug_2021)
```

    ## 'data.frame':    804352 obs. of  13 variables:
    ##  $ ride_id           : chr  "99103BB87CC6C1BB" "EAFCCCFB0A3FC5A1" "9EF4F46C57AD234D" "5834D3208BFAF1DA" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : chr  "2021-08-10 17:15:49" "2021-08-10 17:23:14" "2021-08-21 02:34:23" "2021-08-21 06:52:55" ...
    ##  $ ended_at          : chr  "2021-08-10 17:22:44" "2021-08-10 17:39:24" "2021-08-21 02:50:36" "2021-08-21 07:08:13" ...
    ##  $ start_station_name: chr  "" "" "" "" ...
    ##  $ start_station_id  : chr  "" "" "" "" ...
    ##  $ end_station_name  : chr  "" "" "" "" ...
    ##  $ end_station_id    : chr  "" "" "" "" ...
    ##  $ start_lat         : num  41.8 41.8 42 42 41.8 ...
    ##  $ start_lng         : num  -87.7 -87.7 -87.7 -87.7 -87.6 ...
    ##  $ end_lat           : num  41.8 41.8 42 42 41.8 ...
    ##  $ end_lng           : num  -87.7 -87.6 -87.7 -87.7 -87.6 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...

``` r
str(Sep_2021)
```

    ## 'data.frame':    756147 obs. of  13 variables:
    ##  $ ride_id           : chr  "9DC7B962304CBFD8" "F930E2C6872D6B32" "6EF72137900BB910" "78D1DE133B3DBF55" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : chr  "2021-09-28 16:07:10" "2021-09-28 14:24:51" "2021-09-28 00:20:16" "2021-09-28 14:51:17" ...
    ##  $ ended_at          : chr  "2021-09-28 16:09:54" "2021-09-28 14:40:05" "2021-09-28 00:23:57" "2021-09-28 15:00:06" ...
    ##  $ start_station_name: chr  "" "" "" "" ...
    ##  $ start_station_id  : chr  "" "" "" "" ...
    ##  $ end_station_name  : chr  "" "" "" "" ...
    ##  $ end_station_id    : chr  "" "" "" "" ...
    ##  $ start_lat         : num  41.9 41.9 41.8 41.8 41.9 ...
    ##  $ start_lng         : num  -87.7 -87.6 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num  41.9 42 41.8 41.8 41.9 ...
    ##  $ end_lng           : num  -87.7 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ member_casual     : chr  "casual" "casual" "casual" "casual" ...

``` r
str(Oct_2021)
```

    ## 'data.frame':    631226 obs. of  13 variables:
    ##  $ ride_id           : chr  "620BC6107255BF4C" "4471C70731AB2E45" "26CA69D43D15EE14" "362947F0437E1514" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : chr  "2021-10-22 12:46:42" "2021-10-21 09:12:37" "2021-10-16 16:28:39" "2021-10-16 16:17:48" ...
    ##  $ ended_at          : chr  "2021-10-22 12:49:50" "2021-10-21 09:14:14" "2021-10-16 16:36:26" "2021-10-16 16:19:03" ...
    ##  $ start_station_name: chr  "Kingsbury St & Kinzie St" "" "" "" ...
    ##  $ start_station_id  : chr  "KA1503000043" "" "" "" ...
    ##  $ end_station_name  : chr  "" "" "" "" ...
    ##  $ end_station_id    : chr  "" "" "" "" ...
    ##  $ start_lat         : num  41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num  -87.6 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num  41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num  -87.6 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...

``` r
str(Nov_2021)
```

    ## 'data.frame':    359978 obs. of  13 variables:
    ##  $ ride_id           : chr  "7C00A93E10556E47" "90854840DFD508BA" "0A7D10CDD144061C" "2F3BE33085BCFF02" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : chr  "2021-11-27 13:27:38" "2021-11-27 13:38:25" "2021-11-26 22:03:34" "2021-11-27 09:56:49" ...
    ##  $ ended_at          : chr  "2021-11-27 13:46:38" "2021-11-27 13:56:10" "2021-11-26 22:05:56" "2021-11-27 10:01:50" ...
    ##  $ start_station_name: chr  "" "" "" "" ...
    ##  $ start_station_id  : chr  "" "" "" "" ...
    ##  $ end_station_name  : chr  "" "" "" "" ...
    ##  $ end_station_id    : chr  "" "" "" "" ...
    ##  $ start_lat         : num  41.9 42 42 41.9 41.9 ...
    ##  $ start_lng         : num  -87.7 -87.7 -87.7 -87.8 -87.6 ...
    ##  $ end_lat           : num  42 41.9 42 41.9 41.9 ...
    ##  $ end_lng           : num  -87.7 -87.7 -87.7 -87.8 -87.6 ...
    ##  $ member_casual     : chr  "casual" "casual" "casual" "casual" ...

``` r
str(Dec_2021)
```

    ## 'data.frame':    247540 obs. of  13 variables:
    ##  $ ride_id           : chr  "46F8167220E4431F" "73A77762838B32FD" "4CF42452054F59C5" "3278BA87BF698339" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "electric_bike" "classic_bike" ...
    ##  $ started_at        : chr  "2021-12-07 15:06:07" "2021-12-11 03:43:29" "2021-12-15 23:10:28" "2021-12-26 16:16:10" ...
    ##  $ ended_at          : chr  "2021-12-07 15:13:42" "2021-12-11 04:10:23" "2021-12-15 23:23:14" "2021-12-26 16:30:53" ...
    ##  $ start_station_name: chr  "Laflin St & Cullerton St" "LaSalle Dr & Huron St" "Halsted St & North Branch St" "Halsted St & North Branch St" ...
    ##  $ start_station_id  : chr  "13307" "KP1705001026" "KA1504000117" "KA1504000117" ...
    ##  $ end_station_name  : chr  "Morgan St & Polk St" "Clarendon Ave & Leland Ave" "Broadway & Barry Ave" "LaSalle Dr & Huron St" ...
    ##  $ end_station_id    : chr  "TA1307000130" "TA1307000119" "13137" "KP1705001026" ...
    ##  $ start_lat         : num  41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num  -87.7 -87.6 -87.6 -87.6 -87.7 ...
    ##  $ end_lat           : num  41.9 42 41.9 41.9 41.9 ...
    ##  $ end_lng           : num  -87.7 -87.7 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr  "member" "casual" "member" "member" ...

``` r
str(Jan_2022)
```

    ## 'data.frame':    103770 obs. of  13 variables:
    ##  $ ride_id           : chr  "C2F7DD78E82EC875" "A6CF8980A652D272" "BD0F91DFF741C66D" "CBB80ED419105406" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : chr  "2022-01-13 11:59:47" "2022-01-10 08:41:56" "2022-01-25 04:53:40" "2022-01-04 00:18:04" ...
    ##  $ ended_at          : chr  "2022-01-13 12:02:44" "2022-01-10 08:46:17" "2022-01-25 04:58:01" "2022-01-04 00:33:00" ...
    ##  $ start_station_name: chr  "Glenwood Ave & Touhy Ave" "Glenwood Ave & Touhy Ave" "Sheffield Ave & Fullerton Ave" "Clark St & Bryn Mawr Ave" ...
    ##  $ start_station_id  : chr  "525" "525" "TA1306000016" "KA1504000151" ...
    ##  $ end_station_name  : chr  "Clark St & Touhy Ave" "Clark St & Touhy Ave" "Greenview Ave & Fullerton Ave" "Paulina St & Montrose Ave" ...
    ##  $ end_station_id    : chr  "RP-007" "RP-007" "TA1307000001" "TA1309000021" ...
    ##  $ start_lat         : num  42 42 41.9 42 41.9 ...
    ##  $ start_lng         : num  -87.7 -87.7 -87.7 -87.7 -87.6 ...
    ##  $ end_lat           : num  42 42 41.9 42 41.9 ...
    ##  $ end_lng           : num  -87.7 -87.7 -87.7 -87.7 -87.6 ...
    ##  $ member_casual     : chr  "casual" "casual" "member" "casual" ...

``` r
str(Feb_2022)
```

    ## 'data.frame':    115609 obs. of  13 variables:
    ##  $ ride_id           : chr  "E1E065E7ED285C02" "1602DCDC5B30FFE3" "BE7DD2AF4B55C4AF" "A1789BDF844412BE" ...
    ##  $ rideable_type     : chr  "classic_bike" "classic_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : chr  "2022-02-19 18:08:41" "2022-02-20 17:41:30" "2022-02-25 18:55:56" "2022-02-14 11:57:03" ...
    ##  $ ended_at          : chr  "2022-02-19 18:23:56" "2022-02-20 17:45:56" "2022-02-25 19:09:34" "2022-02-14 12:04:00" ...
    ##  $ start_station_name: chr  "State St & Randolph St" "Halsted St & Wrightwood Ave" "State St & Randolph St" "Southport Ave & Waveland Ave" ...
    ##  $ start_station_id  : chr  "TA1305000029" "TA1309000061" "TA1305000029" "13235" ...
    ##  $ end_station_name  : chr  "Clark St & Lincoln Ave" "Southport Ave & Wrightwood Ave" "Canal St & Adams St" "Broadway & Sheridan Rd" ...
    ##  $ end_station_id    : chr  "13179" "TA1307000113" "13011" "13323" ...
    ##  $ start_lat         : num  41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num  -87.6 -87.6 -87.6 -87.7 -87.6 ...
    ##  $ end_lat           : num  41.9 41.9 41.9 42 41.9 ...
    ##  $ end_lng           : num  -87.6 -87.7 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...

``` r
str(Mar_2022)
```

    ## 'data.frame':    284042 obs. of  13 variables:
    ##  $ ride_id           : chr  "47EC0A7F82E65D52" "8494861979B0F477" "EFE527AF80B66109" "9F446FD9DEE3F389" ...
    ##  $ rideable_type     : chr  "classic_bike" "electric_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : chr  "2022-03-21 13:45:01" "2022-03-16 09:37:16" "2022-03-23 19:52:02" "2022-03-01 19:12:26" ...
    ##  $ ended_at          : chr  "2022-03-21 13:51:18" "2022-03-16 09:43:34" "2022-03-23 19:54:48" "2022-03-01 19:22:14" ...
    ##  $ start_station_name: chr  "Wabash Ave & Wacker Pl" "Michigan Ave & Oak St" "Broadway & Berwyn Ave" "Wabash Ave & Wacker Pl" ...
    ##  $ start_station_id  : chr  "TA1307000131" "13042" "13109" "TA1307000131" ...
    ##  $ end_station_name  : chr  "Kingsbury St & Kinzie St" "Orleans St & Chestnut St (NEXT Apts)" "Broadway & Ridge Ave" "Franklin St & Jackson Blvd" ...
    ##  $ end_station_id    : chr  "KA1503000043" "620" "15578" "TA1305000025" ...
    ##  $ start_lat         : num  41.9 41.9 42 41.9 41.9 ...
    ##  $ start_lng         : num  -87.6 -87.6 -87.7 -87.6 -87.6 ...
    ##  $ end_lat           : num  41.9 41.9 42 41.9 41.9 ...
    ##  $ end_lng           : num  -87.6 -87.6 -87.7 -87.6 -87.7 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...

``` r
str(Apr_2022)
```

    ## 'data.frame':    371249 obs. of  13 variables:
    ##  $ ride_id           : chr  "3564070EEFD12711" "0B820C7FCF22F489" "89EEEE32293F07FF" "84D4751AEB31888D" ...
    ##  $ rideable_type     : chr  "electric_bike" "classic_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : chr  "2022-04-06 17:42:48" "2022-04-24 19:23:07" "2022-04-20 19:29:08" "2022-04-22 21:14:06" ...
    ##  $ ended_at          : chr  "2022-04-06 17:54:36" "2022-04-24 19:43:17" "2022-04-20 19:35:16" "2022-04-22 21:23:29" ...
    ##  $ start_station_name: chr  "Paulina St & Howard St" "Wentworth Ave & Cermak Rd" "Halsted St & Polk St" "Wentworth Ave & Cermak Rd" ...
    ##  $ start_station_id  : chr  "515" "13075" "TA1307000121" "13075" ...
    ##  $ end_station_name  : chr  "University Library (NU)" "Green St & Madison St" "Green St & Madison St" "Delano Ct & Roosevelt Rd" ...
    ##  $ end_station_id    : chr  "605" "TA1307000120" "TA1307000120" "KA1706005007" ...
    ##  $ start_lat         : num  42 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num  -87.7 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num  42.1 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num  -87.7 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr  "member" "member" "member" "casual" ...

``` r
str(May_2022)
```

    ## 'data.frame':    634858 obs. of  13 variables:
    ##  $ ride_id           : chr  "EC2DE40644C6B0F4" "1C31AD03897EE385" "1542FBEC830415CF" "6FF59852924528F8" ...
    ##  $ rideable_type     : chr  "classic_bike" "classic_bike" "classic_bike" "classic_bike" ...
    ##  $ started_at        : chr  "2022-05-23 23:06:58" "2022-05-11 08:53:28" "2022-05-26 18:36:28" "2022-05-10 07:30:07" ...
    ##  $ ended_at          : chr  "2022-05-23 23:40:19" "2022-05-11 09:31:22" "2022-05-26 18:58:18" "2022-05-10 07:38:49" ...
    ##  $ start_station_name: chr  "Wabash Ave & Grand Ave" "DuSable Lake Shore Dr & Monroe St" "Clinton St & Madison St" "Clinton St & Madison St" ...
    ##  $ start_station_id  : chr  "TA1307000117" "13300" "TA1305000032" "TA1305000032" ...
    ##  $ end_station_name  : chr  "Halsted St & Roscoe St" "Field Blvd & South Water St" "Wood St & Milwaukee Ave" "Clark St & Randolph St" ...
    ##  $ end_station_id    : chr  "TA1309000025" "15534" "13221" "TA1305000030" ...
    ##  $ start_lat         : num  41.9 41.9 41.9 41.9 41.9 ...
    ##  $ start_lng         : num  -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num  41.9 41.9 41.9 41.9 41.9 ...
    ##  $ end_lng           : num  -87.6 -87.6 -87.7 -87.6 -87.7 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...

All column names are consistent. The structure is also consistent, so we
can move onto combining the 12 .csv files.

## Combining all the .csv Files

``` r
all_trips <- bind_rows(Jun_2021, Jul_2021, Aug_2021, Sep_2021, Oct_2021, Nov_2021, Dec_2021, Jan_2022, Feb_2022, Mar_2022, Apr_2022, May_2022)
```

## Inspecting and Cleaning the new table

### Inspecting the new table

``` r
colnames(all_trips)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"

``` r
str(all_trips)
```

    ## 'data.frame':    5860776 obs. of  13 variables:
    ##  $ ride_id           : chr  "99FEC93BA843FB20" "06048DCFC8520CAF" "9598066F68045DF2" "B03C0FE48C412214" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : chr  "2021-06-13 14:31:28" "2021-06-04 11:18:02" "2021-06-04 09:49:35" "2021-06-03 19:56:05" ...
    ##  $ ended_at          : chr  "2021-06-13 14:34:11" "2021-06-04 11:24:19" "2021-06-04 09:55:34" "2021-06-03 20:21:55" ...
    ##  $ start_station_name: chr  "" "" "" "" ...
    ##  $ start_station_id  : chr  "" "" "" "" ...
    ##  $ end_station_name  : chr  "" "" "" "" ...
    ##  $ end_station_id    : chr  "" "" "" "" ...
    ##  $ start_lat         : num  41.8 41.8 41.8 41.8 41.8 ...
    ##  $ start_lng         : num  -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num  41.8 41.8 41.8 41.8 41.8 ...
    ##  $ end_lng           : num  -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...

``` r
dim(all_trips)
```

    ## [1] 5860776      13

``` r
summary(all_trips)
```

    ##    ride_id          rideable_type       started_at          ended_at        
    ##  Length:5860776     Length:5860776     Length:5860776     Length:5860776    
    ##  Class :character   Class :character   Class :character   Class :character  
    ##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##  start_station_name start_station_id   end_station_name   end_station_id    
    ##  Length:5860776     Length:5860776     Length:5860776     Length:5860776    
    ##  Class :character   Class :character   Class :character   Class :character  
    ##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##    start_lat       start_lng         end_lat         end_lng      
    ##  Min.   :41.64   Min.   :-87.84   Min.   :41.39   Min.   :-88.97  
    ##  1st Qu.:41.88   1st Qu.:-87.66   1st Qu.:41.88   1st Qu.:-87.66  
    ##  Median :41.90   Median :-87.64   Median :41.90   Median :-87.64  
    ##  Mean   :41.90   Mean   :-87.65   Mean   :41.90   Mean   :-87.65  
    ##  3rd Qu.:41.93   3rd Qu.:-87.63   3rd Qu.:41.93   3rd Qu.:-87.63  
    ##  Max.   :45.64   Max.   :-73.80   Max.   :42.17   Max.   :-87.49  
    ##                                   NA's   :5036    NA's   :5036    
    ##  member_casual     
    ##  Length:5860776    
    ##  Class :character  
    ##  Mode  :character  
    ##                    
    ##                    
    ##                    
    ## 

### Converting “started_at” and “ended_at” to date time

We will need to calculate the ride length, in order to do so we need to
convert the “started_at” and “ended_at” columns from character to date
time using the as.POSIXlt function.

``` r
all_trips$started_at <- as.POSIXlt(all_trips$started_at, format= "%Y-%m-%d %H:%M:%S")
all_trips$ended_at <- as.POSIXlt(all_trips$ended_at, format = "%Y-%m-%d %H:%M:%S")
```

### Adding columns for month, day, year, and weekday

``` r
all_trips$month <- format(as.Date(all_trips$started_at), "%m")
all_trips$day <- format(as.Date(all_trips$started_at), "%d")
all_trips$year <- format(as.Date(all_trips$started_at), "%Y")
all_trips$day_of_week <- format(as.Date(all_trips$started_at), "%A")
```

### Calculating ride length

``` r
all_trips$ride_length <- difftime(all_trips$ended_at, all_trips$started_at) 
```

### Checking the datatype of “ride_length” column

``` r
is.numeric("all_trips$ride_length")
```

    ## [1] FALSE

``` r
is.integer("all_trips$ride_length")
```

    ## [1] FALSE

``` r
is.character("all_trips$ride_length")
```

    ## [1] TRUE

### Changing the datatype of “ride_length” column in order to aggregate in the future

``` r
all_trips$ride_length <- as.numeric(as.character(all_trips$ride_length))
```

### Viewing trips where the length is less than zero or start location is HQ QR

The table might include instances where the ride length was negative. It
might also include instances where bikes were checked and taken out of
the docks and checked. We want to check for this doing the following:

``` r
all_trips[all_trips$start_station_name == "HQ QR" | all_trips$ride_length < 0, ]
```

    ##                  ride_id rideable_type          started_at            ended_at
    ## 15343   732D84DAD2CC9B73  classic_bike 2021-06-20 10:52:26 2021-06-20 10:52:25
    ## 69361   A18D39992AA99793  classic_bike 2021-06-15 20:58:03 2021-06-15 20:54:51
    ## 249370  126E4DA0FA0A3E11 electric_bike 2021-06-02 17:52:32 2021-06-02 17:47:26
    ## 571910  24C4FC421D642C22  classic_bike 2021-06-28 13:18:26 2021-06-28 13:18:25
    ## 728862  4E88151C0FBCA967  classic_bike 2021-06-28 14:56:28 2021-06-28 14:56:27
    ## 801714  E6C4F61273BC824D  classic_bike 2021-07-23 11:32:12 2021-07-23 11:32:08
    ## 801905  18FA8EAE88922DAF  classic_bike 2021-07-21 08:02:07 2021-07-21 08:02:02
    ## 802452  3C634446B054AB44  classic_bike 2021-07-27 19:11:55 2021-07-27 19:11:54
    ## 863352  D22A7B1DAC07DBEC  classic_bike 2021-07-25 01:38:23 2021-07-25 01:38:22
    ## 936197  CBBDF121760541A8  classic_bike 2021-07-24 13:46:27 2021-07-24 13:46:19
    ## 936345  9180A7126B192284  classic_bike 2021-07-18 12:27:30 2021-07-18 12:27:26
    ## 936763  AC7176564B0C716F  classic_bike 2021-07-20 12:52:08 2021-07-20 12:52:02
    ## 937569  B30086B9F4A40A93  classic_bike 2021-07-25 11:14:54 2021-07-25 11:14:50
    ## 946014  2C8922585E5F5B76  classic_bike 2021-07-19 18:15:41 2021-07-19 18:15:36
    ## 1176751 F15EA3F8AB85D605  classic_bike 2021-07-12 18:22:49 2021-07-12 18:22:37
    ## 1181590 C74A0859A1737B0F  classic_bike 2021-07-07 10:38:25 2021-07-07 10:38:21
    ## 1181924 2AB142C32C184032 electric_bike 2021-07-07 18:51:53 2021-07-07 18:51:45
    ## 1343026 FEA10221DC06E355 electric_bike 2021-07-24 11:17:09 2021-07-24 11:17:06
    ## 1587216 A2DBE0C0012129B1  classic_bike 2021-08-20 16:19:52 2021-08-20 16:19:16
    ## 1622527 0291C81C6932E735 electric_bike 2021-08-20 16:20:35 2021-08-20 16:19:37
    ## 1656889 4DD89B8847CF6040 electric_bike 2021-08-10 09:32:21 2021-08-10 09:31:11
    ## 1728929 ACD13D8A68452042  classic_bike 2021-08-21 14:08:50 2021-08-21 14:08:27
    ## 1728930 2F600E738BE2F08A  classic_bike 2021-08-21 14:10:29 2021-08-21 14:10:08
    ## 1776355 F33F5D42F4418061  classic_bike 2021-08-20 16:23:24 2021-08-20 16:23:05
    ## 1825468 E377D242052A190D electric_bike 2021-08-09 18:42:22 2021-08-09 18:42:09
    ## 1831749 42CCBA4971E256F4  classic_bike 2021-08-20 16:21:30 2021-08-20 16:20:27
    ## 1832543 8DE914BA31FDA368  classic_bike 2021-08-22 20:15:47 2021-08-22 20:15:46
    ## 1910740 9ACB997E90B54988 electric_bike 2021-08-26 18:56:17 2021-08-26 18:56:10
    ## 1910846 B2A56072F18F4FD9  classic_bike 2021-08-07 15:22:13 2021-08-07 15:21:59
    ## 1910899 440C3F52F65C5BCD  classic_bike 2021-08-18 23:17:45 2021-08-18 23:17:23
    ## 1911004 84DE853DC2C25C56  classic_bike 2021-08-16 15:40:19 2021-08-16 15:40:08
    ## 1911005 6F5F7FD4D13ECEA0  classic_bike 2021-08-16 15:40:53 2021-08-16 15:40:40
    ## 1911209 8610961166DA8412  classic_bike 2021-08-25 15:46:32 2021-08-25 15:46:26
    ## 1911214 099A7214A2728ACC  classic_bike 2021-08-16 21:28:56 2021-08-16 21:28:37
    ## 1911256 121C9511AE8C11CA  classic_bike 2021-08-15 02:36:39 2021-08-15 02:36:36
    ## 1911288 4E8752F0A62BA2A1  classic_bike 2021-08-22 02:48:23 2021-08-22 02:48:09
    ## 1911363 5B4D4A00D6A4DAAC  classic_bike 2021-08-11 06:56:30 2021-08-11 06:56:25
    ## 1911446 6DCF2C6EC660CAF9  classic_bike 2021-08-26 18:26:33 2021-08-26 18:26:05
    ## 1911578 641EF17482044F18  classic_bike 2021-08-15 15:12:17 2021-08-15 15:12:05
    ## 1911599 FB0519FF5907CACC  classic_bike 2021-08-30 12:03:08 2021-08-30 12:03:00
    ## 1911603 23D6456F1268AF00  classic_bike 2021-08-21 12:29:12 2021-08-21 12:29:07
    ## 2041959 E64AE57BDD6FE595  classic_bike 2021-08-20 16:10:14 2021-08-20 16:09:29
    ## 2123050 9200647C37FD38B0  classic_bike 2021-08-20 16:16:58 2021-08-20 16:14:11
    ## 2168754 4F67BFFB680CEDCD electric_bike 2021-08-10 20:54:18 2021-08-10 20:51:38
    ## 2202554 D35A56D5648A785A electric_bike 2021-08-11 06:12:16 2021-08-11 06:11:04
    ## 2226910 9121D4C66D81CDA2 electric_bike 2021-08-30 13:13:15 2021-08-30 13:11:28
    ## 2233107 3CFA7D4B92C4FDD6  classic_bike 2021-08-20 16:22:07 2021-08-20 16:21:30
    ## 2365308 BE93718DC9182ED6  classic_bike 2021-09-29 17:04:38 2021-09-29 17:04:27
    ## 2405669 6E5FD2F624AC87D3  classic_bike 2021-09-01 17:49:37 2021-09-01 17:49:31
    ## 2426307 FA4DC99A39C36D54  classic_bike 2021-09-29 16:53:34 2021-09-29 16:53:29
    ## 2439160 85BC495341AB2F18 electric_bike 2021-09-01 18:45:38 2021-09-01 18:45:24
    ## 2495775 4A68473D329D45C9  classic_bike 2021-09-29 18:42:50 2021-09-29 18:36:24
    ## 2523612 DB9D07704E3285A8  classic_bike 2021-09-29 16:10:02 2021-09-29 16:09:59
    ## 2532170 5F9FAEC899BAFDCF  classic_bike 2021-09-29 15:40:52 2021-09-29 15:40:18
    ## 2598063 CD7BE84F6552E7AB  classic_bike 2021-09-29 16:56:09 2021-09-29 16:53:46
    ## 2598128 7C194D321B885287  classic_bike 2021-09-29 14:02:52 2021-09-29 14:02:51
    ## 2612023 CAE29510F94F312A  classic_bike 2021-09-29 15:21:39 2021-09-29 15:21:09
    ## 2668253 7623D85B84ADCC27  classic_bike 2021-09-29 18:09:54 2021-09-29 18:07:08
    ## 2673572 082A465904C062EF  classic_bike 2021-09-26 11:15:17 2021-09-26 11:15:16
    ## 2686501 31B5BE372F009A2B electric_bike 2021-09-29 00:23:19 2021-09-29 00:22:11
    ## 2690019 A6CF3312091615EE electric_bike 2021-09-29 00:23:03 2021-09-29 00:22:11
    ## 2691088 41725EA31D3BB35A electric_bike 2021-09-11 13:16:43 2021-09-11 13:16:13
    ## 2711877 06576F6E68A4B2C9  classic_bike 2021-09-29 13:19:09 2021-09-29 13:19:06
    ## 2745350 35D0A35E9454B0F5 electric_bike 2021-09-29 14:51:31 2021-09-29 14:44:28
    ## 2761395 3AEF4FE696696C8F electric_bike 2021-09-29 17:49:18 2021-09-29 17:49:15
    ## 2764646 393F1F0F9D2D5E21  classic_bike 2021-09-05 05:33:11 2021-09-05 05:33:01
    ## 2766303 4EB4634DA7EC8CC7  classic_bike 2021-09-29 17:35:46 2021-09-29 17:31:19
    ## 2791689 3A47A9240BC6727E  classic_bike 2021-09-29 14:52:22 2021-09-29 14:52:09
    ## 2792234 FA44EBC79CC39AEF electric_bike 2021-09-28 17:43:33 2021-09-28 17:43:31
    ## 2815164 D5E5F806D0FFBC1C  classic_bike 2021-09-01 18:42:09 2021-09-01 18:41:40
    ## 2815216 2EDC266B1A809E5E  classic_bike 2021-09-04 09:42:26 2021-09-04 09:41:54
    ## 2815362 137BEA38C2312200  classic_bike 2021-09-02 18:38:19 2021-09-02 18:37:48
    ## 2815617 7F7679196D0D3540  classic_bike 2021-09-01 06:55:19 2021-09-01 06:55:11
    ## 2818273 D4A976387C9C88CE electric_bike 2021-09-04 17:20:37 2021-09-04 17:20:35
    ## 2884868 3E68DE63824DF361 electric_bike 2021-09-29 17:44:02 2021-09-29 17:40:51
    ## 2906228 88BA6AC7326B179B  classic_bike 2021-09-29 15:26:23 2021-09-29 15:26:22
    ## 2914087 6ACD4446FA7A9C6F electric_bike 2021-09-29 17:32:54 2021-09-29 17:28:32
    ## 2918568 F135C632A459FA86 electric_bike 2021-09-26 13:38:00 2021-09-26 13:37:04
    ## 2940248 1C374131EFC52365 electric_bike 2021-09-15 12:38:42 2021-09-15 12:38:32
    ## 2976448 008CF56DDEA16F7E electric_bike 2021-09-28 13:55:52 2021-09-28 13:54:41
    ## 2982444 EBD402BB8BF12337  classic_bike 2021-09-29 16:29:55 2021-09-29 16:26:14
    ## 2988334 448610692B74D6B7  classic_bike 2021-09-29 18:00:15 2021-09-29 17:56:57
    ## 3065993 CA0E5960C9FC5B28  classic_bike 2021-09-29 17:04:41 2021-09-29 17:00:12
    ## 3753916 B029250A1EFF2975   docked_bike 2021-11-07 01:40:02 2021-11-07 01:05:46
    ## 3754772 D631251FA9C7FC03  classic_bike 2021-11-07 01:52:53 2021-11-07 01:05:22
    ## 3755807 021DC77C70A3E367  classic_bike 2021-11-07 01:40:13 2021-11-07 01:00:29
    ## 3767681 235ACD294AFB837F electric_bike 2021-11-07 01:34:03 2021-11-07 01:17:13
    ## 3772771 6A2DCA5CB1596CA6  classic_bike 2021-11-07 01:54:25 2021-11-07 01:03:44
    ## 3778962 E89DD4EBFBD231E3  classic_bike 2021-11-07 01:54:04 2021-11-07 01:25:57
    ## 3780688 0006AA1377F8BCA1  classic_bike 2021-11-07 01:51:52 2021-11-07 01:22:53
    ## 3781751 83B6C6B10248241E  classic_bike 2021-11-07 01:54:12 2021-11-07 01:05:09
    ## 3783316 FFD5A2DDE1FAAA90  classic_bike 2021-11-07 01:54:36 2021-11-07 01:03:11
    ## 3785744 5132D82DCD66BA95 electric_bike 2021-11-07 01:51:21 2021-11-07 01:07:59
    ## 3793647 600852E2195647B8  classic_bike 2021-11-07 01:53:08 2021-11-07 01:25:33
    ## 3800452 7CA158F5F050156E electric_bike 2021-11-07 01:58:08 2021-11-07 01:00:06
    ## 3806074 B60E253706E151AF   docked_bike 2021-11-07 01:40:09 2021-11-07 01:01:44
    ## 3806540 E16920EC561FFEBD   docked_bike 2021-11-07 01:41:23 2021-11-07 01:00:35
    ## 3806908 EDBA8663286116BE   docked_bike 2021-11-07 01:41:27 2021-11-07 01:01:50
    ## 3813455 46BC473D0F68B4A2 electric_bike 2021-11-07 01:55:00 2021-11-07 01:05:54
    ## 3847749 CDB307B8494885AD electric_bike 2021-11-07 01:55:09 2021-11-07 01:02:26
    ## 3853851 0C29F2FD22BFE9C3 electric_bike 2021-11-07 01:46:06 2021-11-07 01:04:14
    ## 3855317 36BCBD47831CECD3 electric_bike 2021-11-07 01:46:03 2021-11-07 01:04:22
    ## 3861519 82ACDD5EE3627B6C  classic_bike 2021-11-07 01:52:57 2021-11-07 01:05:24
    ## 3861538 08F7F73C0EC09A0B  classic_bike 2021-11-07 01:52:47 2021-11-07 01:05:00
    ## 3861798 2B22D0C575CC2DF8  classic_bike 2021-11-07 01:53:12 2021-11-07 01:05:15
    ## 3862985 46D20A622D89BDCE  classic_bike 2021-11-07 01:52:48 2021-11-07 01:05:11
    ## 3866857 802BFC5FF150F1F8   docked_bike 2021-11-07 01:39:17 2021-11-07 01:06:03
    ## 3869586 508B09A5FB0737DC  classic_bike 2021-11-07 01:54:50 2021-11-07 01:00:45
    ## 3882438 9BEB5FBD0EF2FCFD electric_bike 2021-11-07 01:55:32 2021-11-07 01:11:50
    ## 3885822 FD8AF7324ABAE9DA electric_bike 2021-11-07 01:56:51 2021-11-07 01:00:57
    ## 3891759 1374B0438900E9E9  classic_bike 2021-11-07 01:52:15 2021-11-07 01:25:56
    ## 3894547 E17513A83D75F889 electric_bike 2021-11-07 01:50:18 2021-11-07 01:03:54
    ## 3915904 CF4D877FEB218570 electric_bike 2021-11-07 01:45:48 2021-11-07 01:08:54
    ## 3920218 E394AA8418D47B74 electric_bike 2021-11-07 01:50:56 2021-11-07 01:20:21
    ## 3922843 9D8C6B064E2ECEDE  classic_bike 2021-11-07 01:54:37 2021-11-07 01:04:33
    ## 3986015 984A42435A4BBEB0 electric_bike 2021-11-07 01:49:38 2021-11-07 01:03:11
    ## 3989061 83778DB379E8B04B electric_bike 2021-11-07 01:54:08 2021-11-07 01:12:16
    ## 3994442 D6D3692804119896  classic_bike 2021-11-07 01:54:00 2021-11-07 01:05:08
    ## 3997027 1E08692D5C77F7AA  classic_bike 2021-11-07 01:38:12 2021-11-07 01:02:11
    ## 3997606 7E24361D78747AF6 electric_bike 2021-11-07 01:58:06 2021-11-07 01:06:43
    ## 4004551 6F9E76F5EDAAC1B8 electric_bike 2021-11-07 01:55:42 2021-11-07 01:01:55
    ## 4024497 F2AF011E90AC8918  classic_bike 2021-11-07 01:53:03 2021-11-07 01:22:34
    ## 4026404 7AECC76D1562B51C  classic_bike 2021-11-07 01:54:58 2021-11-07 01:01:29
    ## 4026981 36198116E86D6457 electric_bike 2021-11-07 01:57:36 2021-11-07 01:16:31
    ## 4039754 3556173EA13B5C84 electric_bike 2021-11-07 01:53:22 2021-11-07 01:05:08
    ## 4049616 49DF29FDEC7E48FB electric_bike 2021-11-07 01:55:34 2021-11-07 01:08:44
    ## 4066204 214464733718183D electric_bike 2021-11-07 01:37:57 2021-11-07 01:13:17
    ## 4080552 658F94C7AE8F182C electric_bike 2021-11-07 01:42:19 2021-11-07 01:03:58
    ## 4081333 53222CFE6657D53D electric_bike 2021-11-07 01:52:22 2021-11-07 01:01:29
    ## 4083152 D2220642A2BF783C electric_bike 2021-11-07 01:26:28 2021-11-07 01:08:35
    ## 4086819 36CAA82BB5852EF4 electric_bike 2021-11-07 01:19:04 2021-11-07 01:00:27
    ## 4089801 287605D0D79731E6 electric_bike 2021-11-07 01:49:11 2021-11-07 01:13:26
    ## 4098892 8598DCE30427F984 electric_bike 2021-11-07 01:31:33 2021-11-07 01:03:44
    ## 4100863 5AA2BC364BC7A569 electric_bike 2021-11-07 01:59:53 2021-11-07 01:09:02
    ## 4102310 F4E4485BFB33D916 electric_bike 2021-11-07 01:57:53 2021-11-07 01:27:02
    ## 4103680 B506DCD44974C575 electric_bike 2021-11-07 01:53:34 2021-11-07 01:00:42
    ## 4754840 2D97E3C98E165D80  classic_bike 2022-03-05 11:00:57 2022-03-05 10:55:01
    ## 4758017 7407049C5D89A13D electric_bike 2022-03-05 11:38:04 2022-03-05 11:37:57
    ## 5818304 0793C9208A64302A electric_bike 2022-05-30 11:06:29 2022-05-30 11:06:17
    ##                             start_station_name start_station_id
    ## 15343                     Clinton St & Polk St            15542
    ## 69361                   Broadway & Sheridan Rd            13323
    ## 249370                                                         
    ## 571910     Mies van der Rohe Way & Chicago Ave            13338
    ## 728862                   Michigan Ave & Oak St            13042
    ## 801714                Halsted St & Dickens Ave            13192
    ## 801905                Halsted St & Dickens Ave            13192
    ## 802452                Halsted St & Dickens Ave            13192
    ## 863352                              Walsh Park            18067
    ## 936197                Halsted St & Dickens Ave            13192
    ## 936345                Halsted St & Dickens Ave            13192
    ## 936763                Halsted St & Dickens Ave            13192
    ## 937569                Halsted St & Dickens Ave            13192
    ## 946014             Racine Ave & Wrightwood Ave     TA1309000059
    ## 1176751               Damen Ave & Clybourn Ave            13271
    ## 1181590               Damen Ave & Clybourn Ave            13271
    ## 1181924               Damen Ave & Clybourn Ave            13271
    ## 1343026                                                        
    ## 1587216          Sheffield Ave & Fullerton Ave     TA1306000016
    ## 1622527                Streeter Dr & Grand Ave            13022
    ## 1656889                  Rush St & Superior St            15530
    ## 1728929               Halsted St & Dickens Ave            13192
    ## 1728930               Halsted St & Dickens Ave            13192
    ## 1776355             Fairbanks St & Superior St            18003
    ## 1825468                                                        
    ## 1831749           Michigan Ave & Washington St            13001
    ## 1832543             Clybourn Ave & Division St     TA1307000115
    ## 1910740               Halsted St & Dickens Ave            13192
    ## 1910846               Halsted St & Dickens Ave            13192
    ## 1910899               Halsted St & Dickens Ave            13192
    ## 1911004               Halsted St & Dickens Ave            13192
    ## 1911005               Halsted St & Dickens Ave            13192
    ## 1911209               Halsted St & Dickens Ave            13192
    ## 1911214               Halsted St & Dickens Ave            13192
    ## 1911256               Halsted St & Dickens Ave            13192
    ## 1911288               Halsted St & Dickens Ave            13192
    ## 1911363               Halsted St & Dickens Ave            13192
    ## 1911446               Halsted St & Dickens Ave            13192
    ## 1911578               Halsted St & Dickens Ave            13192
    ## 1911599               Halsted St & Dickens Ave            13192
    ## 1911603               Halsted St & Dickens Ave            13192
    ## 2041959               LaSalle St & Illinois St            13430
    ## 2123050           Sheffield Ave & Waveland Ave     TA1307000126
    ## 2168754                                                        
    ## 2202554                                                        
    ## 2226910                Clark St & Montrose Ave     KA1503000022
    ## 2233107           Milwaukee Ave & Wabansia Ave            13243
    ## 2365308                  Shields Ave & 28th Pl            15443
    ## 2405669             Clybourn Ave & Division St     TA1307000115
    ## 2426307          Financial Pl & Ida B Wells Dr           SL-010
    ## 2439160               Halsted St & Dickens Ave            13192
    ## 2495775              Ashland Ave & Division St            13061
    ## 2523612                   Federal St & Polk St           SL-008
    ## 2532170                 Broadway & Sheridan Rd            13323
    ## 2598063  DuSable Lake Shore Dr & Diversey Pkwy     TA1309000039
    ## 2598128                  Throop St & Taylor St            13139
    ## 2612023                   Canal St & Monroe St            13056
    ## 2668253        Pine Grove Ave & Irving Park Rd     TA1308000022
    ## 2673572                      Clark St & Elm St     TA1307000039
    ## 2686501            Dearborn Pkwy & Delaware Pl     TA1307000128
    ## 2690019                                                        
    ## 2691088             California Ave & North Ave            13258
    ## 2711877              Milwaukee Ave & Grand Ave            13033
    ## 2745350                   Federal St & Polk St           SL-008
    ## 2761395                    Clark St & Lunt Ave     KA1504000162
    ## 2764646             Clybourn Ave & Division St     TA1307000115
    ## 2766303           Michigan Ave & Washington St            13001
    ## 2791689            Lincoln Ave & Fullerton Ave     TA1309000058
    ## 2792234                                                        
    ## 2815164               Halsted St & Dickens Ave            13192
    ## 2815216               Halsted St & Dickens Ave            13192
    ## 2815362               Halsted St & Dickens Ave            13192
    ## 2815617               Halsted St & Dickens Ave            13192
    ## 2818273               Halsted St & Dickens Ave            13192
    ## 2884868             Indiana Ave & Roosevelt Rd           SL-005
    ## 2906228                  Kimbark Ave & 53rd St     TA1309000037
    ## 2914087                   New St & Illinois St     TA1306000013
    ## 2918568                                                        
    ## 2940248                 St. Clair St & Erie St            13016
    ## 2976448                                                        
    ## 2982444                 Kingsbury St & Erie St            13265
    ## 2988334                 Kingsbury St & Erie St            13265
    ## 3065993                Dearborn St & Monroe St     TA1305000006
    ## 3753916               Halsted St & Dickens Ave            13192
    ## 3754772                  Clark St & Newport St              632
    ## 3755807                   New St & Illinois St     TA1306000013
    ## 3767681             Sheridan Rd & Lawrence Ave     TA1309000041
    ## 3772771              Franklin St & Illinois St              RN-
    ## 3778962                Orleans St & Hubbard St              636
    ## 3780688                Orleans St & Hubbard St              636
    ## 3781751                   Clinton St & Lake St            13021
    ## 3783316                 State St & Randolph St     TA1305000029
    ## 3785744                 N Green St & W Lake St          20246.0
    ## 3793647                  Clark St & Newport St              632
    ## 3800452               Halsted St & Dickens Ave            13192
    ## 3806074                   New St & Illinois St     TA1306000013
    ## 3806540                   New St & Illinois St     TA1306000013
    ## 3806908                   New St & Illinois St     TA1306000013
    ## 3813455         Sheffield Ave & Wrightwood Ave     TA1309000023
    ## 3847749              Sedgwick St & Webster Ave            13191
    ## 3853851           Sheffield Ave & Waveland Ave     TA1307000126
    ## 3855317           Sheffield Ave & Waveland Ave     TA1307000126
    ## 3861519                  Clark St & Newport St              632
    ## 3861538                  Clark St & Newport St              632
    ## 3861798                  Clark St & Newport St              632
    ## 3862985                  Clark St & Newport St              632
    ## 3866857               Halsted St & Dickens Ave            13192
    ## 3869586              Sedgwick St & Webster Ave            13191
    ## 3882438                  Wabash Ave & Adams St     KA1503000015
    ## 3885822                   Clark St & North Ave            13128
    ## 3891759                Orleans St & Hubbard St              636
    ## 3894547                                                        
    ## 3915904          Major Taylor Trail & 115th St            20207
    ## 3920218                 Damen Ave & Pierce Ave     TA1305000041
    ## 3922843                  Wells St & Concord Ln     TA1308000050
    ## 3986015                Wood St & Milwaukee Ave            13221
    ## 3989061                                                        
    ## 3994442              Franklin St & Illinois St              RN-
    ## 3997027           Milwaukee Ave & Wabansia Ave            13243
    ## 3997606                   Wells St & Walton St     TA1306000011
    ## 4004551           Milwaukee Ave & Wabansia Ave            13243
    ## 4024497                Orleans St & Hubbard St              636
    ## 4026404         Sheffield Ave & Wrightwood Ave     TA1309000023
    ## 4026981               Wilton Ave & Belmont Ave     TA1307000134
    ## 4039754                 Ashland Ave & Grace St            13319
    ## 4049616                Logan Blvd & Elston Ave     TA1308000031
    ## 4066204                                                        
    ## 4080552                                                        
    ## 4081333          Milwaukee Ave & Fullerton Ave              428
    ## 4083152                                                        
    ## 4086819                                                        
    ## 4089801                                                        
    ## 4098892                    Orleans St & Elm St     TA1306000006
    ## 4100863                                                        
    ## 4102310                                                        
    ## 4103680          Milwaukee Ave & Fullerton Ave              428
    ## 4754840 DuSable Lake Shore Dr & Wellington Ave     TA1307000041
    ## 4758017         Sheffield Ave & Wellington Ave     TA1307000052
    ## 5818304                Broadway & Waveland Ave            13325
    ##                               end_station_name end_station_id start_lat
    ## 15343                     Clinton St & Polk St          15542  41.87147
    ## 69361                   Broadway & Sheridan Rd          13323  41.95283
    ## 249370          Southport Ave & Wrightwood Ave   TA1307000113  41.93000
    ## 571910     Mies van der Rohe Way & Chicago Ave          13338  41.89691
    ## 728862                   Michigan Ave & Oak St          13042  41.90096
    ## 801714                Halsted St & Dickens Ave          13192  41.91994
    ## 801905                Halsted St & Dickens Ave          13192  41.91994
    ## 802452                Halsted St & Dickens Ave          13192  41.91994
    ## 863352                              Walsh Park          18067  41.91461
    ## 936197                Halsted St & Dickens Ave          13192  41.91994
    ## 936345                Halsted St & Dickens Ave          13192  41.91994
    ## 936763                Halsted St & Dickens Ave          13192  41.91994
    ## 937569                Halsted St & Dickens Ave          13192  41.91994
    ## 946014             Racine Ave & Wrightwood Ave   TA1309000059  41.92889
    ## 1176751               Damen Ave & Clybourn Ave          13271  41.93193
    ## 1181590               Damen Ave & Clybourn Ave          13271  41.93193
    ## 1181924               Damen Ave & Clybourn Ave          13271  41.93183
    ## 1343026         Valli Produce - Evanston Plaza            599  42.04000
    ## 1587216          Sheffield Ave & Fullerton Ave   TA1306000016  41.92560
    ## 1622527                Streeter Dr & Grand Ave          13022  41.89230
    ## 1656889                                                        41.89590
    ## 1728929               Halsted St & Dickens Ave          13192  41.91994
    ## 1728930               Halsted St & Dickens Ave          13192  41.91994
    ## 1776355             Fairbanks St & Superior St          18003  41.89575
    ## 1825468         Valli Produce - Evanston Plaza            599  42.04000
    ## 1831749           Michigan Ave & Washington St          13001  41.88398
    ## 1832543             Clybourn Ave & Division St   TA1307000115  41.90461
    ## 1910740               Halsted St & Dickens Ave          13192  41.91995
    ## 1910846               Halsted St & Dickens Ave          13192  41.91994
    ## 1910899               Halsted St & Dickens Ave          13192  41.91994
    ## 1911004               Halsted St & Dickens Ave          13192  41.91994
    ## 1911005               Halsted St & Dickens Ave          13192  41.91994
    ## 1911209               Halsted St & Dickens Ave          13192  41.91994
    ## 1911214               Halsted St & Dickens Ave          13192  41.91994
    ## 1911256               Halsted St & Dickens Ave          13192  41.91994
    ## 1911288               Halsted St & Dickens Ave          13192  41.91994
    ## 1911363               Halsted St & Dickens Ave          13192  41.91994
    ## 1911446               Halsted St & Dickens Ave          13192  41.91994
    ## 1911578               Halsted St & Dickens Ave          13192  41.91994
    ## 1911599               Halsted St & Dickens Ave          13192  41.91994
    ## 1911603               Halsted St & Dickens Ave          13192  41.91994
    ## 2041959               LaSalle St & Illinois St          13430  41.89076
    ## 2123050           Sheffield Ave & Waveland Ave   TA1307000126  41.94940
    ## 2168754                                                        41.89000
    ## 2202554                                                        41.89000
    ## 2226910                                                        41.96158
    ## 2233107           Milwaukee Ave & Wabansia Ave          13243  41.91262
    ## 2365308                  Shields Ave & 28th Pl          15443  41.84273
    ## 2405669             Clybourn Ave & Division St   TA1307000115  41.90461
    ## 2426307          Financial Pl & Ida B Wells Dr         SL-010  41.87502
    ## 2439160               Halsted St & Dickens Ave          13192  41.91988
    ## 2495775              Ashland Ave & Division St          13061  41.90345
    ## 2523612             Dearborn St & Van Buren St            624  41.87208
    ## 2532170                 Broadway & Sheridan Rd          13323  41.95283
    ## 2598063  DuSable Lake Shore Dr & Diversey Pkwy   TA1309000039  41.93259
    ## 2598128                  Throop St & Taylor St          13139  41.86897
    ## 2612023                   Canal St & Monroe St          13056  41.88169
    ## 2668253        Pine Grove Ave & Irving Park Rd   TA1308000022  41.95438
    ## 2673572                      Clark St & Elm St   TA1307000039  41.90297
    ## 2686501            Dearborn Pkwy & Delaware Pl   TA1307000128  41.89897
    ## 2690019            Dearborn Pkwy & Delaware Pl   TA1307000128  41.90000
    ## 2691088             California Ave & North Ave          13258  41.91049
    ## 2711877              Milwaukee Ave & Grand Ave          13033  41.89158
    ## 2745350                   Federal St & Polk St         SL-008  41.87198
    ## 2761395                    Clark St & Lunt Ave   KA1504000162  42.00907
    ## 2764646             Clybourn Ave & Division St   TA1307000115  41.90461
    ## 2766303           Michigan Ave & Washington St          13001  41.88398
    ## 2791689            Lincoln Ave & Fullerton Ave   TA1309000058  41.92591
    ## 2792234            Lincoln Ave & Fullerton Ave   TA1309000058  41.93000
    ## 2815164               Halsted St & Dickens Ave          13192  41.91994
    ## 2815216               Halsted St & Dickens Ave          13192  41.91994
    ## 2815362               Halsted St & Dickens Ave          13192  41.91994
    ## 2815617               Halsted St & Dickens Ave          13192  41.91994
    ## 2818273               Halsted St & Dickens Ave          13192  41.91996
    ## 2884868             Indiana Ave & Roosevelt Rd         SL-005  41.86791
    ## 2906228                  Kimbark Ave & 53rd St   TA1309000037  41.79957
    ## 2914087                   New St & Illinois St   TA1306000013  41.89019
    ## 2918568          Greenview Ave & Fullerton Ave   TA1307000001  41.93000
    ## 2940248                 St. Clair St & Erie St          13016  41.89422
    ## 2976448               University Ave & 57th St   KA1503000071  41.79000
    ## 2982444                 Kingsbury St & Erie St          13265  41.89381
    ## 2988334                 Kingsbury St & Erie St          13265  41.89381
    ## 3065993                Dearborn St & Monroe St   TA1305000006  41.88132
    ## 3753916               Leavitt St & Division St            658  41.91994
    ## 3754772             Racine Ave & Fullerton Ave   TA1306000026  41.94454
    ## 3755807                  Michigan Ave & 8th St            623  41.89085
    ## 3767681   Damen Ave & Thomas St (Augusta Blvd)   TA1307000070  41.96948
    ## 3772771    Mies van der Rohe Way & Chicago Ave          13338  41.89102
    ## 3778962                 Clark St & Drummond Pl   TA1307000142  41.89003
    ## 3780688                 Broadway & Belmont Ave          13277  41.89003
    ## 3781751                    Morgan St & Polk St   TA1307000130  41.88564
    ## 3783316                   Federal St & Polk St         SL-008  41.88462
    ## 3785744               Leavitt St & Division St            658  41.89000
    ## 3793647                  Clark St & Newport St            632  41.94454
    ## 3800452                                                        41.92002
    ## 3806074                  Michigan Ave & 8th St            623  41.89085
    ## 3806540                  Michigan Ave & 8th St            623  41.89085
    ## 3806908                  Michigan Ave & 8th St            623  41.89085
    ## 3813455                 Clark St & Schiller St   TA1309000024  41.92858
    ## 3847749                 Halsted St & Roscoe St   TA1309000025  41.92219
    ## 3853851           California Ave & Fletcher St          15642  41.94928
    ## 3855317           California Ave & Fletcher St          15642  41.94915
    ## 3861519             Racine Ave & Fullerton Ave   TA1306000026  41.94454
    ## 3861538             Racine Ave & Fullerton Ave   TA1306000026  41.94454
    ## 3861798             Racine Ave & Fullerton Ave   TA1306000026  41.94454
    ## 3862985             Racine Ave & Fullerton Ave   TA1306000026  41.94454
    ## 3866857               Leavitt St & Division St            658  41.91994
    ## 3869586                Sedgwick St & North Ave   TA1307000038  41.92217
    ## 3882438                     May St & Taylor St          13160  41.87958
    ## 3885822              Larrabee St & Webster Ave          13193  41.91174
    ## 3891759                 Clark St & Drummond Pl   TA1307000142  41.89003
    ## 3894547             Wilton Ave & Diversey Pkwy   TA1306000014  41.90000
    ## 3915904                                                        41.68496
    ## 3920218               Wilton Ave & Belmont Ave   TA1307000134  41.90937
    ## 3922843                   Broadway & Barry Ave          13137  41.91213
    ## 3986015               Halsted St & Dickens Ave          13192  41.90758
    ## 3989061           Campbell Ave & Fullerton Ave          15648  41.90000
    ## 3994442              Michigan Ave & Pearson St          13034  41.89102
    ## 3997027          Greenview Ave & Diversey Pkwy          13294  41.91262
    ## 3997606                 Clark St & Randolph St   TA1305000030  41.89995
    ## 4004551              Western Ave & Division St          13241  41.91258
    ## 4024497                 Broadway & Belmont Ave          13277  41.89003
    ## 4026404         Southport Ave & Wellington Ave   TA1307000006  41.92871
    ## 4026981                 St. Clair St & Erie St          13016  41.94003
    ## 4039754                                                        41.95065
    ## 4049616                                                        41.92949
    ## 4066204                                                        41.88000
    ## 4080552                                                        41.79000
    ## 4081333                                                        41.92000
    ## 4083152                                                        41.86000
    ## 4086819                                                        41.75000
    ## 4089801                                                        41.93000
    ## 4098892                                                        41.90292
    ## 4100863                                                        41.92000
    ## 4102310                                                        41.91000
    ## 4103680                                                        41.92000
    ## 4754840 DuSable Lake Shore Dr & Wellington Ave   TA1307000041  41.93669
    ## 4758017         Sheffield Ave & Wellington Ave   TA1307000052  41.93631
    ## 5818304                                                        41.94907
    ##         start_lng  end_lat   end_lng member_casual month day year day_of_week
    ## 15343   -87.64095 41.87147 -87.64095        casual    06  20 2021      Sunday
    ## 69361   -87.64999 41.95283 -87.64999        casual    06  15 2021     Tuesday
    ## 249370  -87.66000 41.92875 -87.66393        member    06  02 2021   Wednesday
    ## 571910  -87.62174 41.89691 -87.62174        member    06  28 2021      Monday
    ## 728862  -87.62378 41.90096 -87.62378        casual    06  28 2021      Monday
    ## 801714  -87.64883 41.91994 -87.64883        casual    07  23 2021      Friday
    ## 801905  -87.64883 41.91994 -87.64883        member    07  21 2021   Wednesday
    ## 802452  -87.64883 41.91994 -87.64883        member    07  27 2021     Tuesday
    ## 863352  -87.66797 41.91461 -87.66797        casual    07  25 2021      Sunday
    ## 936197  -87.64883 41.91994 -87.64883        member    07  24 2021    Saturday
    ## 936345  -87.64883 41.91994 -87.64883        casual    07  18 2021      Sunday
    ## 936763  -87.64883 41.91994 -87.64883        casual    07  20 2021     Tuesday
    ## 937569  -87.64883 41.91994 -87.64883        casual    07  25 2021      Sunday
    ## 946014  -87.65897 41.92889 -87.65897        casual    07  19 2021      Monday
    ## 1176751 -87.67786 41.93193 -87.67786        member    07  12 2021      Monday
    ## 1181590 -87.67786 41.93193 -87.67786        casual    07  07 2021   Wednesday
    ## 1181924 -87.67776 41.93184 -87.67779        casual    07  07 2021   Wednesday
    ## 1343026 -87.70000 42.03971 -87.69944        member    07  24 2021    Saturday
    ## 1587216 -87.65371 41.92560 -87.65371        member    08  20 2021      Friday
    ## 1622527 -87.61224 41.89228 -87.61226        casual    08  20 2021      Friday
    ## 1656889 -87.62578 41.90000 -87.63000        casual    08  10 2021     Tuesday
    ## 1728929 -87.64883 41.91994 -87.64883        casual    08  21 2021    Saturday
    ## 1728930 -87.64883 41.91994 -87.64883        casual    08  21 2021    Saturday
    ## 1776355 -87.62010 41.89575 -87.62010        casual    08  20 2021      Friday
    ## 1825468 -87.70000 42.03970 -87.69945        member    08  09 2021      Monday
    ## 1831749 -87.62468 41.88398 -87.62468        casual    08  20 2021      Friday
    ## 1832543 -87.64055 41.90461 -87.64055        member    08  22 2021      Sunday
    ## 1910740 -87.64881 41.91996 -87.64884        member    08  26 2021    Thursday
    ## 1910846 -87.64883 41.91994 -87.64883        member    08  07 2021    Saturday
    ## 1910899 -87.64883 41.91994 -87.64883        member    08  18 2021   Wednesday
    ## 1911004 -87.64883 41.91994 -87.64883        member    08  16 2021      Monday
    ## 1911005 -87.64883 41.91994 -87.64883        member    08  16 2021      Monday
    ## 1911209 -87.64883 41.91994 -87.64883        member    08  25 2021   Wednesday
    ## 1911214 -87.64883 41.91994 -87.64883        member    08  16 2021      Monday
    ## 1911256 -87.64883 41.91994 -87.64883        casual    08  15 2021      Sunday
    ## 1911288 -87.64883 41.91994 -87.64883        member    08  22 2021      Sunday
    ## 1911363 -87.64883 41.91994 -87.64883        member    08  11 2021   Wednesday
    ## 1911446 -87.64883 41.91994 -87.64883        member    08  26 2021    Thursday
    ## 1911578 -87.64883 41.91994 -87.64883        member    08  15 2021      Sunday
    ## 1911599 -87.64883 41.91994 -87.64883        member    08  30 2021      Monday
    ## 1911603 -87.64883 41.91994 -87.64883        member    08  21 2021    Saturday
    ## 2041959 -87.63170 41.89076 -87.63170        member    08  20 2021      Friday
    ## 2123050 -87.65453 41.94940 -87.65453        member    08  20 2021      Friday
    ## 2168754 -87.63000 41.89000 -87.63000        member    08  10 2021     Tuesday
    ## 2202554 -87.62000 41.89000 -87.62000        member    08  11 2021   Wednesday
    ## 2226910 -87.66637 41.96000 -87.67000        casual    08  30 2021      Monday
    ## 2233107 -87.68139 41.91262 -87.68139        casual    08  20 2021      Friday
    ## 2365308 -87.63549 41.84273 -87.63549        member    09  29 2021   Wednesday
    ## 2405669 -87.64055 41.90461 -87.64055        member    09  01 2021   Wednesday
    ## 2426307 -87.63309 41.87502 -87.63309        member    09  29 2021   Wednesday
    ## 2439160 -87.64879 41.91991 -87.64878        member    09  01 2021   Wednesday
    ## 2495775 -87.66775 41.90345 -87.66775        member    09  29 2021   Wednesday
    ## 2523612 -87.62954 41.87627 -87.62915        member    09  29 2021   Wednesday
    ## 2532170 -87.64999 41.95283 -87.64999        member    09  29 2021   Wednesday
    ## 2598063 -87.63643 41.93259 -87.63643        member    09  29 2021   Wednesday
    ## 2598128 -87.65914 41.86897 -87.65914        member    09  29 2021   Wednesday
    ## 2612023 -87.63953 41.88169 -87.63953        member    09  29 2021   Wednesday
    ## 2668253 -87.64804 41.95438 -87.64804        member    09  29 2021   Wednesday
    ## 2673572 -87.63128 41.90297 -87.63128        casual    09  26 2021      Sunday
    ## 2686501 -87.62982 41.89897 -87.62982        member    09  29 2021   Wednesday
    ## 2690019 -87.63000 41.89897 -87.62981        member    09  29 2021   Wednesday
    ## 2691088 -87.69693 41.91049 -87.69693        casual    09  11 2021    Saturday
    ## 2711877 -87.64838 41.89158 -87.64838        member    09  29 2021   Wednesday
    ## 2745350 -87.62970 41.87198 -87.62976        member    09  29 2021   Wednesday
    ## 2761395 -87.67422 42.00906 -87.67424        member    09  29 2021   Wednesday
    ## 2764646 -87.64055 41.90461 -87.64055        casual    09  05 2021      Sunday
    ## 2766303 -87.62468 41.88398 -87.62468        member    09  29 2021   Wednesday
    ## 2791689 -87.64926 41.92591 -87.64926        member    09  29 2021   Wednesday
    ## 2792234 -87.65000 41.92592 -87.64924        casual    09  28 2021     Tuesday
    ## 2815164 -87.64883 41.91994 -87.64883        member    09  01 2021   Wednesday
    ## 2815216 -87.64883 41.91994 -87.64883        casual    09  04 2021    Saturday
    ## 2815362 -87.64883 41.91994 -87.64883        member    09  02 2021    Thursday
    ## 2815617 -87.64883 41.91994 -87.64883        member    09  01 2021   Wednesday
    ## 2818273 -87.64885 41.91991 -87.64886        casual    09  04 2021    Saturday
    ## 2884868 -87.62305 41.86791 -87.62305        member    09  29 2021   Wednesday
    ## 2906228 -87.59475 41.79957 -87.59475        member    09  29 2021   Wednesday
    ## 2914087 -87.61821 41.89019 -87.61821        member    09  29 2021   Wednesday
    ## 2918568 -87.67000 41.92549 -87.66584        casual    09  26 2021      Sunday
    ## 2940248 -87.62276 41.89428 -87.62275        member    09  15 2021   Wednesday
    ## 2976448 -87.60000 41.79149 -87.60007        member    09  28 2021     Tuesday
    ## 2982444 -87.64170 41.89381 -87.64170        member    09  29 2021   Wednesday
    ## 2988334 -87.64170 41.89381 -87.64170        member    09  29 2021   Wednesday
    ## 3065993 -87.62952 41.88132 -87.62952        member    09  29 2021   Wednesday
    ## 3753916 -87.64883 41.90300 -87.68382        casual    11  07 2021      Sunday
    ## 3754772 -87.65468 41.92556 -87.65840        member    11  07 2021      Sunday
    ## 3755807 -87.61862 41.87277 -87.62398        casual    11  07 2021      Sunday
    ## 3767681 -87.65473 41.90143 -87.67743        member    11  07 2021      Sunday
    ## 3772771 -87.63548 41.89691 -87.62174        casual    11  07 2021      Sunday
    ## 3778962 -87.63662 41.93125 -87.64434        casual    11  07 2021      Sunday
    ## 3780688 -87.63662 41.94011 -87.64545        casual    11  07 2021      Sunday
    ## 3781751 -87.64182 41.87174 -87.65103        member    11  07 2021      Sunday
    ## 3783316 -87.62783 41.87208 -87.62954        member    11  07 2021      Sunday
    ## 3785744 -87.65000 41.90296 -87.68367        member    11  07 2021      Sunday
    ## 3793647 -87.65468 41.94454 -87.65468        member    11  07 2021      Sunday
    ## 3800452 -87.64899 41.93000 -87.65000        casual    11  07 2021      Sunday
    ## 3806074 -87.61862 41.87277 -87.62398        casual    11  07 2021      Sunday
    ## 3806540 -87.61862 41.87277 -87.62398        casual    11  07 2021      Sunday
    ## 3806908 -87.61862 41.87277 -87.62398        casual    11  07 2021      Sunday
    ## 3813455 -87.65385 41.90802 -87.63171        casual    11  07 2021      Sunday
    ## 3847749 -87.63896 41.94361 -87.64903        casual    11  07 2021      Sunday
    ## 3853851 -87.65443 41.93847 -87.69807        casual    11  07 2021      Sunday
    ## 3855317 -87.65449 41.93845 -87.69806        casual    11  07 2021      Sunday
    ## 3861519 -87.65468 41.92556 -87.65840        member    11  07 2021      Sunday
    ## 3861538 -87.65468 41.92556 -87.65840        member    11  07 2021      Sunday
    ## 3861798 -87.65468 41.92556 -87.65840        member    11  07 2021      Sunday
    ## 3862985 -87.65468 41.92556 -87.65840        member    11  07 2021      Sunday
    ## 3866857 -87.64883 41.90300 -87.68382        casual    11  07 2021      Sunday
    ## 3869586 -87.63889 41.91139 -87.63868        member    11  07 2021      Sunday
    ## 3882438 -87.62605 41.86941 -87.65534        member    11  07 2021      Sunday
    ## 3885822 -87.63215 41.92176 -87.64403        casual    11  07 2021      Sunday
    ## 3891759 -87.63662 41.93125 -87.64434        member    11  07 2021      Sunday
    ## 3894547 -87.63000 41.93248 -87.65276        casual    11  07 2021      Sunday
    ## 3915904 -87.64527 41.67000 -87.64000        member    11  07 2021      Sunday
    ## 3920218 -87.67784 41.93997 -87.65311        casual    11  07 2021      Sunday
    ## 3922843 -87.63466 41.93758 -87.64410        casual    11  07 2021      Sunday
    ## 3986015 -87.67247 41.91983 -87.64926        casual    11  07 2021      Sunday
    ## 3989061 -87.63000 41.92464 -87.68931        member    11  07 2021      Sunday
    ## 3994442 -87.63548 41.89766 -87.62351        member    11  07 2021      Sunday
    ## 3997027 -87.68139 41.93259 -87.66594        casual    11  07 2021      Sunday
    ## 3997606 -87.63445 41.88526 -87.63231        member    11  07 2021      Sunday
    ## 4004551 -87.68142 41.90291 -87.68737        member    11  07 2021      Sunday
    ## 4024497 -87.63662 41.94011 -87.64545        casual    11  07 2021      Sunday
    ## 4026404 -87.65383 41.93573 -87.66358        casual    11  07 2021      Sunday
    ## 4026981 -87.65295 41.89516 -87.62331        member    11  07 2021      Sunday
    ## 4039754 -87.66874 41.94000 -87.70000        casual    11  07 2021      Sunday
    ## 4049616 -87.68421 41.94000 -87.65000        casual    11  07 2021      Sunday
    ## 4066204 -87.62000 41.80000 -87.59000        casual    11  07 2021      Sunday
    ## 4080552 -87.60000 41.79000 -87.60000        member    11  07 2021      Sunday
    ## 4081333 -87.70000 41.91000 -87.71000        casual    11  07 2021      Sunday
    ## 4083152 -87.63000 41.95000 -87.65000        member    11  07 2021      Sunday
    ## 4086819 -87.61000 41.75000 -87.57000        member    11  07 2021      Sunday
    ## 4089801 -87.65000 41.97000 -87.70000        casual    11  07 2021      Sunday
    ## 4098892 -87.63771 41.93000 -87.66000        casual    11  07 2021      Sunday
    ## 4100863 -87.69000 41.90000 -87.70000        casual    11  07 2021      Sunday
    ## 4102310 -87.72000 41.90000 -87.77000        casual    11  07 2021      Sunday
    ## 4103680 -87.70000 41.91000 -87.71000        casual    11  07 2021      Sunday
    ## 4754840 -87.63683 41.93669 -87.63683        casual    03  05 2022    Saturday
    ## 4758017 -87.65252 41.93625 -87.65266        casual    03  05 2022    Saturday
    ## 5818304 -87.64850 41.95000 -87.65000        casual    05  30 2022      Monday
    ##         ride_length
    ## 15343            -1
    ## 69361          -192
    ## 249370         -306
    ## 571910           -1
    ## 728862           -1
    ## 801714           -4
    ## 801905           -5
    ## 802452           -1
    ## 863352           -1
    ## 936197           -8
    ## 936345           -4
    ## 936763           -6
    ## 937569           -4
    ## 946014           -5
    ## 1176751         -12
    ## 1181590          -4
    ## 1181924          -8
    ## 1343026          -3
    ## 1587216         -36
    ## 1622527         -58
    ## 1656889         -70
    ## 1728929         -23
    ## 1728930         -21
    ## 1776355         -19
    ## 1825468         -13
    ## 1831749         -63
    ## 1832543          -1
    ## 1910740          -7
    ## 1910846         -14
    ## 1910899         -22
    ## 1911004         -11
    ## 1911005         -13
    ## 1911209          -6
    ## 1911214         -19
    ## 1911256          -3
    ## 1911288         -14
    ## 1911363          -5
    ## 1911446         -28
    ## 1911578         -12
    ## 1911599          -8
    ## 1911603          -5
    ## 2041959         -45
    ## 2123050        -167
    ## 2168754        -160
    ## 2202554         -72
    ## 2226910        -107
    ## 2233107         -37
    ## 2365308         -11
    ## 2405669          -6
    ## 2426307          -5
    ## 2439160         -14
    ## 2495775        -386
    ## 2523612          -3
    ## 2532170         -34
    ## 2598063        -143
    ## 2598128          -1
    ## 2612023         -30
    ## 2668253        -166
    ## 2673572          -1
    ## 2686501         -68
    ## 2690019         -52
    ## 2691088         -30
    ## 2711877          -3
    ## 2745350        -423
    ## 2761395          -3
    ## 2764646         -10
    ## 2766303        -267
    ## 2791689         -13
    ## 2792234          -2
    ## 2815164         -29
    ## 2815216         -32
    ## 2815362         -31
    ## 2815617          -8
    ## 2818273          -2
    ## 2884868        -191
    ## 2906228          -1
    ## 2914087        -262
    ## 2918568         -56
    ## 2940248         -10
    ## 2976448         -71
    ## 2982444        -221
    ## 2988334        -198
    ## 3065993        -269
    ## 3753916       -5656
    ## 3754772       -6451
    ## 3755807       -5984
    ## 3767681       -4610
    ## 3772771       -6641
    ## 3778962       -1687
    ## 3780688       -1739
    ## 3781751       -6543
    ## 3783316       -6685
    ## 3785744       -6202
    ## 3793647       -1655
    ## 3800452       -7082
    ## 3806074       -5905
    ## 3806540       -6048
    ## 3806908       -5977
    ## 3813455       -6546
    ## 3847749       -6763
    ## 3853851       -6112
    ## 3855317       -6101
    ## 3861519       -6453
    ## 3861538       -6467
    ## 3861798       -6477
    ## 3862985       -6457
    ## 3866857       -5594
    ## 3869586       -6845
    ## 3882438       -6222
    ## 3885822       -6954
    ## 3891759       -1579
    ## 3894547       -6384
    ## 3915904       -5814
    ## 3920218       -1835
    ## 3922843       -6604
    ## 3986015       -6387
    ## 3989061       -6112
    ## 3994442       -6532
    ## 3997027       -5761
    ## 3997606       -6683
    ## 4004551       -6827
    ## 4024497       -1829
    ## 4026404       -6809
    ## 4026981       -6065
    ## 4039754       -6494
    ## 4049616       -6410
    ## 4066204       -5080
    ## 4080552       -5901
    ## 4081333       -6653
    ## 4083152       -4673
    ## 4086819       -1117
    ## 4089801       -5745
    ## 4098892       -5269
    ## 4100863       -6651
    ## 4102310       -1851
    ## 4103680       -6772
    ## 4754840        -356
    ## 4758017          -7
    ## 5818304         -12

### Creating new data frame, excluding rows where the start station is HQ QR and the ride length is less than zero

We want to remove instances where start station is HQ QR and the ride
length is less than zero.

``` r
all_trips_v2 <- all_trips[!(all_trips$start_station_name == "HQ QR" | all_trips$ride_length < 0), ]
```

### Inspecting all_trips_v2

``` r
dim(all_trips) # to compare the number of rows to all_trips_v2
```

    ## [1] 5860776      18

``` r
dim(all_trips_v2)
```

    ## [1] 5860637      18

``` r
colnames(all_trips_v2)
```

    ##  [1] "ride_id"            "rideable_type"      "started_at"        
    ##  [4] "ended_at"           "start_station_name" "start_station_id"  
    ##  [7] "end_station_name"   "end_station_id"     "start_lat"         
    ## [10] "start_lng"          "end_lat"            "end_lng"           
    ## [13] "member_casual"      "month"              "day"               
    ## [16] "year"               "day_of_week"        "ride_length"

``` r
str(all_trips_v2)
```

    ## 'data.frame':    5860637 obs. of  18 variables:
    ##  $ ride_id           : chr  "99FEC93BA843FB20" "06048DCFC8520CAF" "9598066F68045DF2" "B03C0FE48C412214" ...
    ##  $ rideable_type     : chr  "electric_bike" "electric_bike" "electric_bike" "electric_bike" ...
    ##  $ started_at        : POSIXlt, format: "2021-06-13 14:31:28" "2021-06-04 11:18:02" ...
    ##  $ ended_at          : POSIXlt, format: "2021-06-13 14:34:11" "2021-06-04 11:24:19" ...
    ##  $ start_station_name: chr  "" "" "" "" ...
    ##  $ start_station_id  : chr  "" "" "" "" ...
    ##  $ end_station_name  : chr  "" "" "" "" ...
    ##  $ end_station_id    : chr  "" "" "" "" ...
    ##  $ start_lat         : num  41.8 41.8 41.8 41.8 41.8 ...
    ##  $ start_lng         : num  -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ end_lat           : num  41.8 41.8 41.8 41.8 41.8 ...
    ##  $ end_lng           : num  -87.6 -87.6 -87.6 -87.6 -87.6 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...
    ##  $ month             : chr  "06" "06" "06" "06" ...
    ##  $ day               : chr  "13" "04" "04" "03" ...
    ##  $ year              : chr  "2021" "2021" "2021" "2021" ...
    ##  $ day_of_week       : chr  "Sunday" "Friday" "Friday" "Thursday" ...
    ##  $ ride_length       : num  163 377 359 1550 248 405 371 378 526 551 ...

## Analyzing the New Data Frame

### Summary of the Data

``` r
summary(all_trips_v2$ride_length)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##       0     382     680    1241    1236 3356649

### Comparing Annual Members and Casual Riders

``` r
aggregate(all_trips_v2$ride_length ~ all_trips_v2$member_casual, FUN = mean)
```

    ##   all_trips_v2$member_casual all_trips_v2$ride_length
    ## 1                     casual                 1833.083
    ## 2                     member                  782.695

``` r
aggregate(all_trips_v2$ride_length ~ all_trips_v2$member_casual, FUN = median)
```

    ##   all_trips_v2$member_casual all_trips_v2$ride_length
    ## 1                     casual                      916
    ## 2                     member                      547

``` r
aggregate(all_trips_v2$ride_length ~ all_trips_v2$member_casual, FUN = max)
```

    ##   all_trips_v2$member_casual all_trips_v2$ride_length
    ## 1                     casual                  3356649
    ## 2                     member                    89998

``` r
aggregate(all_trips_v2$ride_length ~ all_trips_v2$member_casual, FUN = min)
```

    ##   all_trips_v2$member_casual all_trips_v2$ride_length
    ## 1                     casual                        0
    ## 2                     member                        0

### Seeing the average ride time by each day for members vs casual users

``` r
aggregate(all_trips_v2$ride_length ~ all_trips_v2$member_casual + all_trips_v2$day_of_week, FUN = mean)
```

    ##    all_trips_v2$member_casual all_trips_v2$day_of_week all_trips_v2$ride_length
    ## 1                      casual                   Friday                1726.7447
    ## 2                      member                   Friday                 766.9394
    ## 3                      casual                   Monday                1831.6679
    ## 4                      member                   Monday                 758.7213
    ## 5                      casual                 Saturday                2010.4394
    ## 6                      member                 Saturday                 877.4190
    ## 7                      casual                   Sunday                2121.2888
    ## 8                      member                   Sunday                 887.9070
    ## 9                      casual                 Thursday                1662.4662
    ## 10                     member                 Thursday                 746.5689
    ## 11                     casual                  Tuesday                1574.5123
    ## 12                     member                  Tuesday                 736.7175
    ## 13                     casual                Wednesday                1599.3681
    ## 14                     member                Wednesday                 738.5552

The week days are out of order, so to list them in order (starting w/
Sunday)

``` r
all_trips_v2$day_of_week <- ordered(all_trips_v2$day_of_week, levels=c("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"))
```

Running the aggregate() function again.

``` r
aggregate(all_trips_v2$ride_length ~ all_trips_v2$member_casual + all_trips_v2$day_of_week, FUN = mean)
```

    ##    all_trips_v2$member_casual all_trips_v2$day_of_week all_trips_v2$ride_length
    ## 1                      casual                   Sunday                2121.2888
    ## 2                      member                   Sunday                 887.9070
    ## 3                      casual                   Monday                1831.6679
    ## 4                      member                   Monday                 758.7213
    ## 5                      casual                  Tuesday                1574.5123
    ## 6                      member                  Tuesday                 736.7175
    ## 7                      casual                Wednesday                1599.3681
    ## 8                      member                Wednesday                 738.5552
    ## 9                      casual                 Thursday                1662.4662
    ## 10                     member                 Thursday                 746.5689
    ## 11                     casual                   Friday                1726.7447
    ## 12                     member                   Friday                 766.9394
    ## 13                     casual                 Saturday                2010.4394
    ## 14                     member                 Saturday                 877.4190

### Analyzing ridership data by type and weekday

``` r
all_trips_v2 %>% mutate(weekday = wday(started_at, label = TRUE)) %>% group_by(member_casual, weekday) %>% summarize(number_of_rides = n(), average_duration = mean(ride_length)) %>% arrange(member_casual, weekday)
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

    ## # A tibble: 14 × 4
    ## # Groups:   member_casual [2]
    ##    member_casual weekday number_of_rides average_duration
    ##    <chr>         <ord>             <int>            <dbl>
    ##  1 casual        Sun              470157            2121.
    ##  2 casual        Mon              302073            1832.
    ##  3 casual        Tue              287018            1575.
    ##  4 casual        Wed              285769            1599.
    ##  5 casual        Thu              308614            1662.
    ##  6 casual        Fri              360007            1727.
    ##  7 casual        Sat              546158            2010.
    ##  8 member        Sun              394686             888.
    ##  9 member        Mon              466109             759.
    ## 10 member        Tue              524804             737.
    ## 11 member        Wed              512600             739.
    ## 12 member        Thu              501807             747.
    ## 13 member        Fri              459798             767.
    ## 14 member        Sat              441037             877.

## Initial Visualizations

### Number of Rides by Rider Type and Weekday

``` r
all_trips_v2 %>% mutate(weekday = wday(started_at, label = TRUE)) %>% group_by(member_casual, weekday) %>% summarize(number_of_rides = n(), average_duration = mean(ride_length)) %>% arrange(member_casual, weekday) %>% ggplot(aes(x=weekday, y=number_of_rides, fill=member_casual)) + geom_col(position = "dodge")
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

![](Cyclistic--Casual-Riders-and-Annual-Members_files/figure-gfm/Number%20of%20Rides%20by%20Rider%20Type%20and%20Weekday-1.png)<!-- -->

### Average Duration by Rider Type and Weekday

``` r
all_trips_v2 %>% mutate(weekday = wday(started_at, label = TRUE)) %>% group_by(member_casual, weekday) %>% summarize(number_of_rides = n(), average_duration = mean(ride_length)) %>% arrange(member_casual, weekday) %>% ggplot(aes(x=weekday, y=average_duration, fill=member_casual)) + geom_col(position = "dodge")
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

![](Cyclistic--Casual-Riders-and-Annual-Members_files/figure-gfm/Average%20Duration%20by%20Rider%20Type%20and%20Weekday-1.png)<!-- -->

## Exporting Data

Exporting .csv files so that visualizations can be created in Tableau.

### Rides and Duration By Weekday

``` r
rides_and_dur_wd <- all_trips_v2 %>% mutate(weekday = wday(started_at, label = TRUE)) %>% group_by(member_casual, weekday) %>% summarize(number_of_rides = n(), average_duration = mean(ride_length)) %>% arrange(member_casual, weekday)
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

``` r
write.csv(rides_and_dur_wd, file= "~/Desktop/Projects- PUBLIC/Cyclistic-Casual-Riders-and-Annual-Members/rides_and_dur_wd.csv")
```

### Rides and Duration By Month

``` r
rides_and_dur_m <- all_trips_v2 %>% mutate(month = month(started_at, label = TRUE)) %>% group_by(member_casual, month) %>% summarize(number_of_rides = n(), average_duration = mean(ride_length)) %>% arrange(member_casual, month)
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

``` r
write.csv(rides_and_dur_m, file= "~/Desktop/Projects- PUBLIC/Cyclistic-Casual-Riders-and-Annual-Members/rides_and_dur_m.csv")
```

### Links to Tableau and Presentation

Tableau link
[here](https://public.tableau.com/app/profile/vanessa4875/viz/Cyclistic-CasualRidersandAnnualMembers/RidesandDurationbyMonth).

Presentation on 
[Google Slides](https://docs.google.com/presentation/d/1ejTlAbq0jKHqehNl-xy3gvIxocrw75MamVRbOUkZxnQ/edit#slide=id.g13b90827ecf_0_147).
