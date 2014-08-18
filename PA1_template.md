# Reproducible Research: Peer Assessment 1
This  assumes that the data file is unzipped as activity.csv 

## Loading and preprocessing the data

```r
acts<-read.csv("activity.csv")
```


## What is mean total number of steps taken per day?
See below for histogram, mean and median

```r
act_agg<-aggregate( steps~date, act, sum)
hist(act_agg$steps) 
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

```r
mean(act_agg$steps)
```

```
## [1] 10766
```

```r
median(act_agg$steps)
```

```
## [1] 10765
```

## What is the average daily activity pattern?
See below for plot of intervals and the interval with most activity. 


```r
act_interval_agg<-aggregate( steps~interval, act, mean)
plot(act_interval_agg$interval,act_interval_agg$steps, type="l", ylab="Average Number of Steps Taken", xlab="")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

```r
act_interval_agg[order(act_interval_agg[,2], decreasing=T)[1],1]
```

```
## [1] 835
```

## Imputing missing values
These are the number of complete cases. 


```r
sum(complete.cases(act)==TRUE)
```

```
## [1] 15264
```

## Are there differences in activity patterns between weekdays and weekends?
