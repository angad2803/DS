# Assignment 4.1: Data Frames and Lists in R

**UCS 548 – Foundations of Data Science**

---

## Question 1: Create a Data Frame for Patient Dataset

```r
DF <- data.frame(
  PatientID = c(1, 2, 3, 4),
  AdmDate = as.Date(c("2009-10-15", "2009-11-01", "2009-10-21", "2009-10-28")),
  Age = c(25, 34, 28, 52),
  Diabetes = c("Type1", "Type2", "Type1", "Type1"),
  Status = c("Poor", "Improved", "Excellent", "Poor")
)

print(DF)
```

---

## Question 2: Perform Operations on the Data Frame

### 2.a Extract PatientID and Age in Subset 1

```r
Subset1 <- DF[, c("PatientID", "Age")]
print(Subset1)
```

---

### 2.b Identify Type1 Diabetes Patients

```r
Type1_patients <- DF[DF$Diabetes == "Type1", ]
print(Type1_patients)
```

---

### 2.c Count Patients with Poor Status

```r
Poor_count <- sum(DF$Status == "Poor")
print(Poor_count)
```

---

### 2.d Print Summary of Data Frame

```r
summary(DF)
```

---

### 2.e Find Average Age of All Patients with Diabetes

```r
avg_age <- mean(DF$Age)
print(avg_age)
```

---

### 2.f Input More Patient Data from Keyboard (Interactive)

```r
# Uncomment and run interactively when needed:

# new_patient <- data.frame(
#   PatientID = as.integer(readline("Enter PatientID: ")),
#   AdmDate = as.Date(readline("Enter Admission Date (YYYY-MM-DD): ")),
#   Age = as.integer(readline("Enter Age: ")),
#   Diabetes = readline("Enter Diabetes Type: "),
#   Status = readline("Enter Status: ")
# )

# DF <- rbind(DF, new_patient)
# print(DF)
```

---

## Question 3: Create a List Named MyList

### 3.a Create Age Vector

```r
a <- c(12, 14, 16, 20)
```

---

### 3.b Create Two-Dimensional Matrix with 5 Rows

```r
mat <- matrix(1:10, nrow = 5, ncol = 2)
print(mat)
```

---

### 3.c Create Score Vector

```r
s <- c("First", "Second", "Third")
```

---

### Create the Complete List Structure

```r
MyList <- list(
  Title = "My First List",
  Criteria = list(
    Age_Vector = a,
    Matrix_2D = mat,
    Score_Vector = s
  )
)
```

---

### Display List Components

```r
# Print entire list
print(MyList)

# Print Criteria component
print(MyList$Criteria)

# Print Age vector
print(a)
```
