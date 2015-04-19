---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---


## Loading and preprocessing the data

```r
data <- read.csv("activity.csv", colClasses = c("numeric", "Date", "numeric"))
data1 <- data[complete.cases(data),]
```

## What is mean total number of steps taken per day?

```r
answer1 <- tapply(data1$steps, data1$date, FUN = sum)
hist(answer1)
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2-1.png) 

```r
m1 <- mean(answer1)
m2<- median(answer1)
```

The mean total number of steps taken per day is 1.0766189 &times; 10<sup>4</sup>.
The median total number of steps taken per day is 1.0765 &times; 10<sup>4</sup>.


## What is the average daily activity pattern?

```r
answer2 <- tapply(data1$steps, data1$interval, FUN = mean)
plot(row.names(answer2), answer2)
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png) 

```r
maxint <- row.names(answer2)[which.max(answer2)]
```

The 5 minute interval, on average, with the maximum number of steps is 835.

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
