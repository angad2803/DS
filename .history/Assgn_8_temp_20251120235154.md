# Assignment 8: Basics of Plotting and ggplot
*Lab II - Data Visualization in R*

---

### Step 1: Random Number Generation and Basic Plotting

```r
# Generate random data
x <- runif(100, min = 1, max = 5)
y <- x^2 + runif(100)
```

**1.1 Simple Plot**
```r
plot(x)
plot(x, main = "X data")
plot(x, main = "X data", xlab = "X Axis", ylab = "Y Axis")
```

**1.2 Scatter Plot: x vs y**
```r
plot(x, y, main = "Scatter plot", xlab = "X Axis", ylab = "Y Axis")
```

**1.3 Save Plot to File**
```r
png(filename = "MyPlot.png")
plot(x, y, main = "Scatter plot", xlab = "X Axis", ylab = "Y Axis")
dev.off()
getwd()  # Get the Current Working Directory
```

---

### Step 2: The Normal Distribution

```r
x1 <- rnorm(10, sd = 2)
x2 <- rnorm(10, sd = 3)
x3 <- rnorm(10, sd = 4)

# Plot x1, x2, x3 together
df <- data.frame(x1, x2, x3)
plot(df[, 1:3])
```

---

### Step 3: Statistical Functions

**Min, Max, Sum, Standard Deviation**
```r
x <- c(2, 7, 3, 2, 4, 1, 8, 2, 4, 2, 8, -5, 4)
min(x)
max(x)
sum(x)
sd(x)
```

**Mean, Median, Mode**
```r
mean(x)
median(x)

# Function to get mode (most occurred element)
getmode <- function(v) {
  uniqv <- unique(v)
  uniqv[which.max(tabulate(match(v, uniqv)))]
}

getmode(x)
```

---

### Step 4: Correlation, Variance and Covariance

```r
x <- c(2, 7, 3, 2, 4, 1, 8, 2, 4, 2, 8, -5, 4)
y <- c(6, 3, 8, 1, 3, 6, 8, 2, 3, 5, 8, 4, -6)
z <- round(runif(13, min = -10, max = 10), 0)
```

**Variance and Covariance**
```r
var(x, y)
cov(x, y, method = "pearson")
cov(x, y, method = "kendall")
cov(x, y, method = "spearman")
```

**Correlation**
```r
cor(x, y, method = "pearson")
cor(x, y, method = "kendall")
cor(x, y, method = "spearman")
```

**Pairwise Correlation and Visualization**
```r
df <- data.frame(x, y, z)
pairCor <- cor(df, use = "pairwise", method = "pearson")
print(pairCor)

# Visualize correlation matrix
install.packages("corrplot")
library(corrplot)
corrplot(pairCor)
```

---

### Step 5: Linear Regression

```r
x <- c(173, 169, 176, 166, 161, 164, 160, 158, 180, 187)
y <- c(80, 68, 72, 75, 70, 65, 62, 60, 85, 92)

linearModel <- lm(y ~ x)
plot(x, y)
abline(linearModel, lwd = 2)
predicted <- predict(linearModel)
segments(x, y, x, predicted, col = "red")
```

---

### Step 6: Basic Plots using ggplot2

```r
install.packages("ggplot2")
library(ggplot2)

data(diamonds)  # Load built-in dataset
head(diamonds)
summary(diamonds)
```

**6.1 Histogram**
```r
hist(diamonds$carat, main = "Carat Histogram", xlab = "Carat")
plot(price ~ carat, data = diamonds)
plot(diamonds$carat, diamonds$price)
```

**6.2 Boxplots**
```r
boxplot(diamonds$carat)

# Boxplot explanation: The thick middle line represents the median,
# the box bounds the first and third quartiles (middle 50% of data - IQR).
# Lines extend to 1.5*IQR in both directions. Outliers plotted beyond that.

boxplot(diamonds)
boxplot(diamonds[, -c(7)])  # Dropping carat column
```

**6.3 Histograms and Densities with ggplot2**
```r
ggplot(data = diamonds) + geom_histogram(aes(x = carat))
ggplot(data = diamonds) + geom_density(aes(x = carat), fill = "grey50")
```

**Scatter Plots with ggplot2**
```r
ggplot(diamonds, aes(x = carat, y = price)) + geom_point()

g <- ggplot(diamonds, aes(x = carat, y = price))
g + geom_point(aes(color = color))
g + geom_point(aes(color = color)) + facet_wrap(~color)
g + geom_point(aes(color = color)) + facet_grid(cut ~ clarity)
```

**More ggplot2 Visualizations**
```r
ggplot(diamonds, aes(x = carat)) + geom_histogram() + facet_wrap(~color)
ggplot(diamonds, aes(y = carat, x = 1)) + geom_boxplot()
ggplot(diamonds, aes(y = carat, x = cut)) + geom_boxplot()
ggplot(diamonds, aes(y = carat, x = cut)) + geom_violin()
ggplot(diamonds, aes(y = carat, x = cut)) + geom_point() + geom_violin()
ggplot(diamonds, aes(y = carat, x = cut)) + geom_violin() + geom_point()

ggplot(economics, aes(x = date, y = pop)) + geom_line()
```

**Time Series Plot with Custom Formatting**
```r
install.packages("lubridate")
install.packages("scales")

library(lubridate)
library(scales)

economics$year <- year(economics$date)
economics$month <- month(economics$date, label = TRUE)
econ2000 <- economics[which(economics$year >= 2000), ]

# Build the plot
g <- ggplot(econ2000, aes(x = month, y = pop))
g <- g + geom_line(aes(color = factor(year), group = year))
g <- g + scale_color_discrete(name = "Year")
g <- g + scale_y_continuous(labels = comma)
g <- g + labs(title = "Population Growth", x = "Month", y = "Population")
g
```

**6.4 ggplot2 Themes**
```r
install.packages("ggthemes")
library(ggthemes)

g2 <- ggplot(diamonds, aes(x = carat, y = price)) + 
      geom_point(aes(color = color))

# Apply different themes
g2 + theme_economist() + scale_colour_economist()
g2 + theme_excel() + scale_colour_excel()
g2 + theme_tufte()
g2 + theme_wsj()
```

---

### Step 7: Grid and Curve Plotting

```r
x <- round(runif(13, min = -5, max = 5), 0)
y <- round(runif(13, min = -5, max = 5), 0)
z <- round(runif(13, min = -5, max = 5), 0)

plot(z, type = "n")
grid(lty = 1, lwd = 2)
curve(x^2, col = "blue", add = TRUE)
curve(x^2 + 1, col = "blue", add = TRUE)
points(z^2, pch = 20)
```

---

### Step 8: Graphical Parameters

```r
plot(z, type = "o", col = "red", pch = 16, cex = 2)
plot(z, col = c("red", "blue"), pch = "+", cex = 2)
```

---

### Step 9: Colors in Plotting

```r
colors()
palette()  # Default palette
palette(sample(colors(), 10))  # Change palette
plot(runif(50), col = rep(1:10, each = 5), pch = 16, cex = 2)
```

---

### Step 10: Histogram - Frequency Plotting

```r
# Create a grouping variable
a <- factor(sample(1:5, 13, replace = TRUE), levels = 1:5)
levels(a) <- LETTERS[1:5]
print(a)

plot(a)
plot(y ~ a)  # Box Plot
```

---

### Step 11: Plotting Data Frames

Scatterplot matrix: a matrix of all pairwise bivariate scatterplots.

```r
data(iris)
head(iris)
class(iris)

plot(iris)
plot(iris[1:4], col = as.numeric(iris$Species))  # Color by Species
```

---

### Step 12: Function Plotting

```r
plot(sin, from = -2 * pi, to = 2 * pi)
plot(cos, from = -2 * pi, to = 2 * pi)

# Custom damped sine function
damped.sin <- function(x) sin(5 * x) * exp(-x^2)
class(damped.sin)
plot(damped.sin, from = -pi, to = pi)
```
