# Assignment 3: Arrays and Matrices in R
**UCS 548 – Foundations of Data Science**

---

## Question 1: Create Array A and Display Elements

```r
A <- c(12, 13, 14, 15, 16)
print(A)
```

---

## Question 2: Find Sum of All Elements

```r
sum_A <- sum(A)
print(sum_A)
```

---

## Question 3: Find Product of All Elements

```r
prod_A <- prod(A)
print(prod_A)
```

---

## Question 4: Find Maximum and Minimum Elements

```r
max_A <- max(A)
min_A <- min(A)

print(paste("Maximum:", max_A))
print(paste("Minimum:", min_A))
```

---

## Question 5: Find Range of Array A

```r
range_A <- range(A)
print(range_A)
```

---

## Question 6: Calculate Statistical Measures

Find mean, variance, standard deviation, and median of array A.

```r
mean_A <- mean(A)
var_A <- var(A)
sd_A <- sd(A)
median_A <- median(A)

print(paste("Mean:", mean_A))
print(paste("Variance:", var_A))
print(paste("Standard Deviation:", sd_A))
print(paste("Median:", median_A))
```

---

## Question 7: Sort Array in Increasing and Decreasing Order

Store sorted arrays in B (increasing) and C (decreasing).

```r
B <- sort(A)                        # Increasing order
C <- sort(A, decreasing = TRUE)     # Decreasing order

print("B (Increasing):")
print(B)

print("C (Decreasing):")
print(C)
```

---

## Question 8: Create 3x4 Matrix with Natural Numbers

```r
M <- matrix(1:12, nrow = 3, ncol = 4)
print(M)
```

---

## Question 9: Combine A, B, C Row-wise and Column-wise

Create matrices RW (row-wise) and CW (column-wise) by combining arrays A, B, and C.

```r
RW <- rbind(A, B, C)    # Row-wise combination
CW <- cbind(A, B, C)    # Column-wise combination

print("RW (Row-wise):")
print(RW)

print("CW (Column-wise):")
print(CW)
```

---

## Question 10: Extract 2nd and 3rd Rows from RW

```r
RW_rows_2_3 <- RW[2:3, ]
print(RW_rows_2_3)
```

---

## Question 11: Extract 1st and 4th Columns from CW

```r
CW_cols_1_4 <- CW[, c(1, 4)]
print(CW_cols_1_4)
```

---

## Question 12: Find Sub-matrices with Elements at Positions [2,3] and [2,4]

### From RW Matrix

```r
RW_sub_23 <- RW[2, 3]    # Element at row 2, column 3
RW_sub_24 <- RW[2, 4]    # Element at row 2, column 4

print(paste("RW[2,3]:", RW_sub_23))
print(paste("RW[2,4]:", RW_sub_24))
```

---

### From CW Matrix

```r
CW_sub_23 <- CW[2, 3]    # Element at row 2, column 3
CW_sub_24 <- CW[2, 4]    # Element at row 2, column 4

print(paste("CW[2,3]:", CW_sub_23))
print(paste("CW[2,4]:", CW_sub_24))
```
