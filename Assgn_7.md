# -------------------------------

# Assignment 7

# -------------------------------

set.seed(123)

# 1. Create MARKS matrix of 20 students in 3 subjects

MARKS <- matrix(sample(40:60, 60, replace = TRUE), nrow = 20, ncol = 3)
colnames(MARKS) <- c("SUB1", "SUB2", "SUB3")

# a. Total marks of each student

grand_total <- apply(MARKS, 1, sum)

# b. Append total to dataset

MARKS_df <- as.data.frame(MARKS)
MARKS_df$Total <- grand_total

# c. Standard error function

st.err <- function(x) sd(x) / sqrt(length(x))
stderr_SUBS <- apply(MARKS_df[, 1:3], 2, st.err)

# d. Add 0.25 bonus marks

MARKS_df[, 1:3] <- MARKS_df[, 1:3] + 0.25

# 2. Create vectors and use lapply

V1 <- MARKS_df$SUB1
V2 <- MARKS_df$SUB2
V3 <- MARKS_df$SUB3
lapply(list(V1, V2, V3), sum)

# 3. TOTAL_SUM using sapply

sapply(list(V1, V2, V3), sum)

# 4. Square values using sapply

sapply(list(V1, V2, V3), function(x) x^2)

# 5. Add index I and use tapply

I <- rep(1:4, each = 5)
tapply(V1, I, mean)
tapply(V1, I, sd)

# 6. mapply function f(x, y) = x/y

f <- function(x, y) x / y
mapply(f, V1, V2)

# 7. Apply functions on Seatbelts dataset

data(Seatbelts)
apply(Seatbelts, 2, summary)
