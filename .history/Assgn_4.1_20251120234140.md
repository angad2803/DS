# -------------------------------------------------------

# UCS 548 – Foundations of Data Science

# Assignment 4 – COMPLETE SOLUTION IN ONE BLOCK

# -------------------------------------------------------

# -------------------------------------------------------

# Q1. Vector Creation using seq() and rep()

# -------------------------------------------------------

# Q1.1 Generate vector: 1.3 1.6 1.9 ... 4.9

vec1 <- seq(1.3, 4.9, by = 0.3)
vec1

# Q1.2 Generate vector: 1 2 3 4 repeated 5 times

vec2 <- rep(1:4, times = 5)
vec2

# Q1.3 Generate vector: 14 12 10 8 6 4 2 0

vec3 <- seq(14, 0, by = -2)
vec3

# Q1.4 Generate vector: 5 5 12 12 13 13 20 20

vec4 <- rep(c(5, 12, 13, 20), each = 2)
vec4

# -------------------------------------------------------

# Q2. Loading and exploring iris dataset

# -------------------------------------------------------

data(iris)

# Q2.A What sort of data type is iris?

class(iris)

# Q2.B How many rows and columns?

dim(iris)

# Q2.C Which variable is a factor and how many levels?

str(iris)

# Correct Answer: Species is a factor with 3 levels → option (b)

# -------------------------------------------------------

# Q3. Using iris dataset

# -------------------------------------------------------

# Q3.a Mean and SD of Sepal.Length and Sepal.Width by Species

aggregate(Sepal.Length ~ Species, data = iris, FUN = mean)
aggregate(Sepal.Width ~ Species, data = iris, FUN = mean)

aggregate(Sepal.Length ~ Species, data = iris, FUN = sd)
aggregate(Sepal.Width ~ Species, data = iris, FUN = sd)

# Q3.b Create iris.class with Calyx.Width = "short" or "long"

iris.class <- iris
iris.class$Calyx.Width <- ifelse(iris$Sepal.Length < 5, "short", "long")
head(iris.class)

# -------------------------------------------------------

# Q4. Explore mtcars dataset

# -------------------------------------------------------

data(mtcars)

# Q4.A Select cars whose cyl >= 5

subset_A <- mtcars[mtcars$cyl >= 5, ]
subset_A

# Q4.B Show all columns of the first 10 cars

subset_B <- mtcars[1:10, ]
subset_B

# Q4.C Find all cars matching “Honda”

subset_C <- mtcars[grep("Honda", rownames(mtcars), ignore.case = TRUE), ]
subset_C
