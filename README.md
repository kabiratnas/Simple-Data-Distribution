1.	The student directory for a large university has 400 pages with 130 names per page, a total of 52,000 names. Using software, show how to select a simple random sample of 10 names. 
# Total number of names in the student directory is
 total_students_names <- 52000
# Number of names to sample (simple random sample)
  sample_student_size <- 10
# Generating a simple random sample with R
  simple_random_sample <- sample(x=total_students_names, size = sample_student_size)
# Print the sampled names (numbers in this case)
  print(simple_random_sample)
   [1] 13508 32403 19856 4311 19146 24634 4906 40604 47080 15939

2.	From the Murder data file, use the variable murder, which is the murder rate (per 100,000 population) for each state in the U.S. in 2017 according to the FBI Uniform Crime Reports. At first, do not use the observation for D.C. (DC). Using software:
> US_murder_data <- read.table ("C:/Users/kabir/OneDrive/Documents/Murder.dat.txt", header = TRUE)
> US_murder_without_DC <- subset(US_murder_data, state != "DC")
> mean_US_murder_without_DC <- mean(US_murder_without_DC$murder)
> print(mean_US_murder_without_DC)
[1] 4.874
> standard_deviation_US_murder_without_DC <- sd(US_murder_without_DC$murder)
> print(standard_deviation_US_murder_without_DC)
[1] 2.586291
> five_no_summary_without_dc <- summary(US_murder_without_DC$murder)
> print (five_no_summary_without_dc)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  1.000   2.625   4.850   4.874   6.175  12.400 
> boxplot(US_murder_without_DC$murder, main= "U.S. 2017 Murder Rates (Without Washington DC)", ylab = "Murder Rate (per 100,000 People)")





Figure 1
U.S. in 2017 according to the FBI Uniform Crime 
> #Calculate with DC
> US_murder_with_DC <- rbind(US_murder_without_DC, US_murder_data[US_murder_data$state == "DC", ])
> mean_US_murder_with_DC <- mean(US_murder_data$murder)
> print(mean_US_murder_with_DC)
[1] 5.252941
> median_US_murder_with_DC <- median(US_murder_data$murder)
> print(median_US_murder_with_DC)
[1] 5

3.	  The Houses data file lists the selling price (thousands of dollars), size (square feet), tax bill (dollars), number of bathrooms, number of bedrooms, and whether the house is new (1 = yes,0 = no) for 100 home sales in Gainesville, Florida. Let’s analyze the selling prices
a.	 Construct a frequency distribution and a histogram. Construct a frequency distribution and a histogram.
Florida_house_data <- read.table ("C:/Users/kabir/OneDrive/Documents/Houses.dat.txt", header = TRUE)
> price_range <- seq(min(Florida_house_data$price), max(Florida_house_data$price), length.out = 10)
> frequency_table <- table(cut(Florida_house_data$price, breaks = price_range, include.lowest = TRUE))
> hist(Florida_house_data$price, main = "Histogram of Florida House Selling Prices", xlab = "Selling Price (unit:thousands of Dollars)", ylab = "Frequency", breaks = 10)
> print(price_range)
 [1]  31.5000 125.8333 220.1667 314.5000 408.8333 503.1667 597.5000 691.8333
 [9] 786.1667 880.5000
> print(frequency_table)
[31.5,126]  (126,220]  (220,314]  (314,409]  (409,503]  (503,598]  (598,692] 
        14         49         22          5          3          3          1 
 (692,786]  (786,880] 
1	         2 
Figure 2
Histogram of Home Sales in Gainesville, Florida
 
b.	Find the percentage of observations that fall within one standard deviation of the mean.
> mean_selling_price <- mean(Florida_house_data$price)
> standard_deviation_selling_price <- sd(Florida_house_data$price)
> within_one_standard_deviation <- Florida_house_data$price[Florida_house_data$price > (mean_selling_price - standard_deviation_selling_price) & Florida_house_data$price < (mean_selling_price + standard_deviation_selling_price)]
> percentage_within <- length(within_one_standard_deviation) / length(Florida_house_data$price)*100
> cat("Percentage of observations that fall within one standard deviation of the mean:", percentage_within, "%\n")
Percentage of observations that fall within one standard deviation of the mean: 85 %
c.	Construct a boxplot.
> boxplot(Florida_house_data$price, main = "Florida House Selling Prices Boxplot", ylab = "Selling Price (unit:thousands of Dollars)")
Figure 3
Boxplot of Home Sales in Gainesville, Florida
