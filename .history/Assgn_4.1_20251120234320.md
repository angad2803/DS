# -------------------------------------------------------

# UCS 548 – Foundations of Data Science

# Assignment 4.1 – COMPLETE SOLUTION IN ONE BLOCK

# -------------------------------------------------------

# -------------------------------------------------------

# Q1. Create a Data Frame (DF) for the patient dataset

# -------------------------------------------------------

DF <- data.frame(
PatientID = c(1, 2, 3, 4),
AdmDate = as.Date(c("2009-10-15", "2009-11-01", "2009-10-21", "2009-10-28")),
Age = c(25, 34, 28, 52),
Diabetes = c("Type1", "Type2", "Type1", "Type1"),
Status = c("Poor", "Improved", "Excellent", "Poor")
)

DF

# -------------------------------------------------------

# Q2. Perform operations on DF

# -------------------------------------------------------

# Q2.a Extract PatientID and Age in Subset 1

Subset1 <- DF[, c("PatientID", "Age")]
Subset1

# Q2.b Identify Type1 patients

Type1_patients <- DF[DF$Diabetes == "Type1", ]
Type1_patients

# Q2.c Count the patients of Poor status

Poor_count <- sum(DF$Status == "Poor")
Poor_count

# Q2.d Print summary of DF

summary(DF)

# Q2.e Find average age of patients having Diabetes (any type)

avg_age <- mean(DF$Age)
avg_age

# Q2.f Input more patient data from Keyboard (interactive)

# Uncomment only when needed:

# new_patient <- data.frame(

# PatientID = as.integer(readline("Enter PatientID: ")),

# AdmDate = as.Date(readline("Enter Admission Date (YYYY-MM-DD): ")),

# Age = as.integer(readline("Enter Age: ")),

# Diabetes = readline("Enter Diabetes Type: "),

# Status = readline("Enter Status: ")

# )

# DF <- rbind(DF, new_patient)

# DF

# -------------------------------------------------------

# Q3. Create a list named MyList

# -------------------------------------------------------

# Q3.a Age vector

a <- c(12, 14, 16, 20)

# Q3.b Two-dimensional matrix with 5 rows

mat <- matrix(1:10, nrow = 5, ncol = 2)

# Q3.c Score vector

s <- c("First", "Second", "Third")

# Creating the list

MyList <- list(
Title = "My First List",
Criteria = list(
Age_Vector = a,
Matrix_2D = mat,
Score_Vector = s
)
)

# Print list, criteria, and vector a

MyList
MyList$Criteria
a
