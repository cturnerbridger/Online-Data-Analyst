# Online-Data-Analyst
Notes + code (using the R statistical package) from a online data analyst job application

Link to .csv file - n.b. this is dummy data:
https://www.dropbox.com/s/2worqbd25p9imx0/Online%20analyst%20test%20-%20Dummy%20data.csv?dl=0

###Work Flow / Process

1. View data variables and structure.
2. Use descriptive statistics to examine quantitative variables (using R)

###R Script

Load data
```R
> sdata  <- read.csv("Online analyst test - Dummy data.csv", header = T)
```

basic overview of the variables
```R
> str(sdata)
```

Visually look at the strucutre
```R
> view(sdata)
```

get some descriptive statistics!
```R
> require(psych)
> round(describe(sdata), 2)
```

There is a massive outlier in the variable 'sales_value' - with a skew of 502 and standard deviation of 60. Delete this outlier using MS Excel.

Create a frequency table for the catagorical variable: 'region'.
```R
> reg.freq  <- table(sdata$region)
> reg.freq
```

Create a basic bar plot to examine the distribution by category for the variable 'region'.
```R
> barplot(reg.freq, col = "lavender", main = "Barplot for Delivery Region", ylab = "Frequency")
> round(prop.table(reg.freq), 2) #just to have a quantitive look at the frequency...
```

Create a frequency table for the catagorical variable: 'date'.
```R
> date.freq  <- table(sdata$Transaction_Date)
> date.freq
```

Create a basic bar plot to examine the distribution by category for the variable 'date'.
```R
> barplot(date.freq, col = "lavender", main = "Barplot for Delivery Date", ylab = "Frequency")
```

Have a look at the descriptive statistics for the variable 'sales_value'
```R
> describe(sdata$sales_value)
```

Basic plot for the variable 'sales_value'
```R
> hist(sdata$sales_value)
```

As I there are no further outliers I value 1 SD either side of the mean equally and I can standardise the variable 'sales_value'
```R
> sales_value.z  <- scale(sdata$sales_value)
> hist(sales_value.z)
```

Now that the variable is standardised I can have a look at the log distribution
```R
> sales_value.ln  <- log(sdata$sales_value + 1)
> describe(sales_value.ln)
> hist(sales_value.ln)
```
Turns out that this has a log normal distrobution.

Look at the trend: formulate hypothesis', areas of opportunity and recommendations from this

##Overall points
(1) Sumary wk 26: 2% points w/w  acceleration in cart value (2) Opptertunities: Region 7 shows potential with a high avg. cart value (3) Threats: Region 5 has seen a higher than normal drop in cart value in wk 23 - we need to understand this.

Create a presentation!
