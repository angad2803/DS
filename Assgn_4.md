# Assignment 4: Data Manipulation in R
**UCS 548 – Foundations of Data Science**

---

## Question 1: Vector Creation using seq() and rep()

### 1) Create vector: 1.3, 1.6, 1.9, ..., 4.9
```r
vec1 <- seq(1.3, 4.9, by = 0.3)
print(vec1)
```

---

### 2) Create vector: 1, 2, 3, 4 repeated 5 times
```r
vec2 <- rep(1:4, times = 5)
print(vec2)
```

---

### 3) Create vector: 14, 12, 10, 8, 6, 4, 2, 0
```r
vec3 <- seq(14, 0, by = -2)
print(vec3)
```

---

### 4) Create vector: 5, 5, 12, 12, 13, 13, 20, 20
```r
vec4 <- rep(c(5, 12, 13, 20), each = 2)
print(vec4)
```

---

## Question 2: Loading and Exploring iris Dataset

```r
# Load iris dataset
data(iris)
```

### A. What sort of data type is iris?
```r
class(iris)
# Output: "data.frame"
```

---

### B. How many rows and columns?
```r
dim(iris)
# Output: 150 rows, 5 columns
```

---

### C. Which variable is a factor and how many levels?
```r
str(iris)
# Species is a factor with 3 levels
```

**Answer:** Species is a factor with 3 levels (setosa, versicolor, virginica)

---

## Question 3: Using iris Dataset

### a) Calculate Mean and SD of Sepal Measurements by Species

#### Mean of Sepal Length by Species
```r
aggregate(Sepal.Length ~ Species, data = iris, FUN = mean)
```

#### Mean of Sepal Width by Species
```r
aggregate(Sepal.Width ~ Species, data = iris, FUN = mean)
```

#### Standard Deviation of Sepal Length by Species
```r
aggregate(Sepal.Length ~ Species, data = iris, FUN = sd)
```

#### Standard Deviation of Sepal Width by Species
```r
aggregate(Sepal.Width ~ Species, data = iris, FUN = sd)
```

---

### b) Create iris.class Dataset with Calyx.Width Variable

Create a new variable that classifies sepal length as "short" (< 5) or "long" (≥ 5).

```r
iris.class <- iris
iris.class$Calyx.Width <- ifelse(iris$Sepal.Length < 5, "short", "long")
head(iris.class)
```

---

## Question 4: Explore mtcars Dataset

```r
# Load mtcars dataset
data(mtcars)
```

### A. Select Cars with Cylinders >= 5
```r
subset_A <- mtcars[mtcars$cyl >= 5, ]
print(subset_A)
```

---

### B. Show All Columns of First 10 Cars
```r
subset_B <- mtcars[1:10, ]
print(subset_B)
```

---

### C. Find All Cars Matching "Honda"
```r
# Car names are stored as row names
subset_C <- mtcars[grep("Honda", rownames(mtcars), ignore.case = TRUE), ]
print(subset_C)
```
