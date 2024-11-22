# <p align="center"> **Unit-3: Subsetting and Data Manipulation in R** </p>

### 1. What is Data Analysis?
Data analysis is the process of inspecting, cleaning, transforming, and modeling data with the goal of discovering useful information, drawing conclusions, and supporting decision-making. It involves various techniques and tools to extract meaningful patterns and insights from raw data, helping organizations to make data-driven decisions.

---

### 2. What is Statistical Data Analysis?
Statistical data analysis refers to the process of collecting, reviewing, analyzing, and drawing conclusions from data using statistical methods. This includes measures of central tendency (mean, median, mode), variability (standard deviation, variance), correlations, regressions, and hypothesis testing. The goal is to understand the data and its underlying patterns, relationships, and significance.

---

### 3. How R is Useful in Data Analysis and Statistical Analysis of Data?
R is a powerful language and environment for statistical computing and graphics. It provides a wide range of statistical and graphical techniques that make it useful for both data analysis and statistical analysis:
- **Data manipulation**: It allows easy manipulation of data with packages like `dplyr` and `tidyr`.
- **Visualization**: R has powerful tools for creating visualizations such as histograms, scatter plots, and box plots using `ggplot2`.
- **Statistical techniques**: R supports a wide variety of statistical techniques like linear regression, hypothesis testing, time series analysis, and more.
- **Reproducibility**: R allows you to create reproducible reports using RMarkdown.

---

### 4. Basic commands of R
Here is another explanation of basic R commands:

1. **Assignment**:
   - You assign values to variables using the `<-` operator or `=`:
     ```R
     x <- 10   # assigns 10 to x
     y = 20    # assigns 20 to y
     ```

2. **Basic Arithmetic Operations**:
   - Arithmetic operations are performed using symbols:
     ```R
     sum_result <- 5 + 3      # Addition
     diff_result <- 10 - 4    # Subtraction
     prod_result <- 6 * 7    # Multiplication
     div_result <- 20 / 4    # Division
     power_result <- 2^3    # Exponentiation
     ```

3. **Creating Vectors**:
   - Vectors can be created using the `c()` function:
     ```R
     numbers <- c(1, 2, 3, 4, 5)   # A vector of numbers
     ```

4. **Accessing Vector Elements**:
   - You can access individual elements of a vector using square brackets:
     ```R
     numbers[1]   # Accesses the first element (1)
     ```

5. **Basic Functions**:
   - R has a set of built-in functions for common operations:
     ```R
     sum_value <- sum(c(1, 2, 3))    # Sum of elements
     mean_value <- mean(c(10, 20, 30)) # Mean of elements
     sd_value <- sd(c(10, 20, 30))    # Standard deviation
     ```

6. **Creating Data Frames**:
   - Data frames store data in a tabular format (rows and columns). You can create one like this:
     ```R
     df <- data.frame(Name = c("Alice", "Bob"),
                      Age = c(25, 30))
     ```

7. **Accessing Data Frame Elements**:
   - Access columns using the `$` operator:
     ```R
     df$Name   # Accesses the Name column
     df[1,]    # Accesses the first row
     df[,2]    # Accesses the second column (Age)
     ```

8. **Control Structures**:
   - R supports `if`, `else`, and `for` loops:
     ```R
     # if-else statement
     if (x > 5) {
       print("Greater than 5")
     } else {
       print("Less than or equal to 5")
     }
     
     # for loop
     for (i in 1:3) {
       print(i)
     }
     ```

9. **Functions in R**:
   - You can define your own functions using the `function` keyword:
     ```R
     square <- function(x) {
       return(x^2)
     }
     square(4)   # Returns 16
     ```

10. **Basic Plotting**:
    - You can create simple plots using `plot()`:
      ```R
      plot(1:10)   # Plots numbers from 1 to 10
      ```

11. **Loading External Libraries**:
    - R allows you to install and load external libraries for extended functionality:
      ```R
      install.packages("ggplot2")   # Install a package
      library(ggplot2)              # Load the package
      ```

These are some of the basic commands and functionalities in R. R is a powerful tool for data analysis and statistical computing, offering a wide range of commands for manipulating, analyzing, and visualizing data.
  
---

### 5. How to use the `cut()` function? Explain with an example.
The `cut()` function in R is used to divide a continuous variable into discrete intervals or categories. It's useful when you want to group continuous data into factors.

#### Example:
```r
# Creating a vector of numbers
ages <- c(25, 30, 35, 40, 45, 50, 55, 60, 65)

# Using cut() to create age groups
age_groups <- cut(ages, breaks = c(20, 30, 40, 50, 60, 70), labels = c("20-30", "30-40", "40-50", "50-60", "60-70"))

# Display the result
print(age_groups)
```
This divides the ages into 5 groups: 20-30, 30-40, etc.

---

### 6. Create a CSV containing around 20 records using R/Python code.
Here’s an R example to create a CSV with 20 records:
```r
# Create a data frame with 20 records
data <- data.frame(
  ID = 1:20,
  Name = c("Alice", "Bob", "Charlie", "David", "Eva", "Frank", "Grace", "Hannah", "Ivy", "Jack", 
           "Kim", "Liam", "Mona", "Nancy", "Oscar", "Paul", "Quincy", "Rita", "Sam", "Tina"),
  Age = sample(18:60, 20, replace = TRUE),
  Score = sample(50:100, 20, replace = TRUE)
)

# Write the data to a CSV file
write.csv(data, "data.csv", row.names = FALSE)
```
This creates a CSV file with columns `ID`, `Name`, `Age`, and `Score`.

---

### 7. Write an R code to read records from the CSV file in a folder on your desktop and display the records one by one.
Here’s how you can read and display records from a CSV file:
```r
# Set the path to the CSV file
file_path <- "C:/Users/YourUsername/Desktop/data.csv"

# Read the CSV file into a data frame
data <- read.csv(file_path)

# Loop through the rows and print them
for (i in 1:nrow(data)) {
  print(data[i, ])
}
```
Make sure to replace `"C:/Users/YourUsername/Desktop/data.csv"` with the actual path to your CSV file.

---

### 8. Explain Data Filtering and Data Cleaning, giving appropriate examples.
- **Data Filtering**: Data filtering is the process of selecting a subset of data based on certain conditions or criteria.
  - Example: If you have a dataset of ages and want to filter out those older than 40, you can do:
    ```r
    filtered_data <- data[data$Age > 40, ]
    print(filtered_data)
    ```
  
- **Data Cleaning**: Data cleaning involves identifying and rectifying errors or inconsistencies in the dataset, such as missing values, incorrect entries, or duplicates.
  - Example: If a dataset has missing values in the `Age` column, you can clean it by removing rows with missing values:
    ```r
    cleaned_data <- na.omit(data)
    print(cleaned_data)
    ```

Data cleaning might also include correcting spelling errors, handling outliers, or standardizing formats.

---

<br>
<br>
<br>

# <p align="center"> **Unit-4: Subsetting and Data Manipulation in R** </p>


### 1. **Various Methods for Subsetting in R**
In R, subsetting allows you to extract specific parts of data from vectors, matrices, lists, or data frames. Common methods include:

- **Using `[ ]`**: Extracts rows, columns, or elements from data structures.
- **Using `[[ ]]`**: Extracts single elements from lists or columns from data frames.
- **Using `$`**: Extracts specific columns or elements by name in data frames and lists.
- **Using `slice()` from `dplyr`**: Selects rows by specifying row indices.
- **Using `select()` from `dplyr`**: Selects columns from data frames.

---

### 2. **Subsetting Using `[ ]`**
The `[ ]` operator extracts parts of data like specific elements or rows/columns from vectors, matrices, or data frames.

#### Example:
```r
# Subsetting a vector
vec <- c(1, 2, 3, 4, 5)
vec[2:4]  # Extracts elements from 2nd to 4th
```

```r
# Subsetting a data frame
df <- data.frame(a = 1:5, b = letters[1:5])
df[1:3, ]  # Extracts the first 3 rows
```

---

### 3. **Subsetting Using `[[ ]]`**
The `[[ ]]` operator is used to extract single elements from lists or data frames, accessed by index or column name.

#### Example:
```r
# Subsetting a list
my_list <- list(a = 1:5, b = "hello")
my_list[["b"]]  # Extracts the element 'b'
```

```r
# Subsetting a data frame (column)
df <- data.frame(a = 1:5, b = letters[1:5])
df[["b"]]  # Extracts column 'b'
```

---

### 4. **Subsetting Using `$`**
The `$` operator extracts elements or columns by their name from data frames and lists, simplifying access.

#### Example:
```r
# Subsetting a data frame
df <- data.frame(a = 1:5, b = letters[1:5])
df$b  # Extracts the column 'b'
```

```r
# Subsetting a list
my_list <- list(a = 1:5, b = "hello")
my_list$b  # Extracts element 'b'
```

---

### 5. **Factor Subsetting**
Factors represent categorical data in R. Subsetting factors is similar to subsetting vectors but requires attention to factor levels.

#### Example:
```r
# Creating a factor
factor_var <- factor(c("low", "medium", "high", "medium", "low"))
factor_var[factor_var == "medium"]  # Subsetting the factor by level 'medium'
```

---

### 6. **Slice Function with Syntax and Example**
The `slice()` function from the `dplyr` package selects rows by specifying row indices.

#### Syntax:
```r
slice(data, row_indices)
```

#### Example:
```r
library(dplyr)
df <- data.frame(a = 1:5, b = letters[1:5])
slice(df, 2:4)  # Extracts rows 2 to 4
```

---

### 7. **Using `select()` Function for Subsetting in R**
The `select()` function from the `dplyr` package selects columns from data frames by name or index.

#### Example:
```r
library(dplyr)
df <- data.frame(a = 1:5, b = letters[1:5], c = 6:10)
select(df, a, c)  # Selects columns 'a' and 'c'
```

---

### 8. **Adding, Removing, and Renaming Variables in a Data Frame**
You can add, remove, or rename variables (columns) in a data frame using various methods.

#### Example:
```r
# Adding a column
df$new_col <- c(10, 20, 30, 40, 50)

# Removing a column
df$removed_col <- NULL  # Removes the column

# Renaming a column
names(df)[names(df) == "old_col_name"] <- "new_col_name"
```

---

### 9. **Data Cleaning in R**
Data cleaning involves handling missing values, duplicates, and correcting data types.

- **Remove missing values**: `na.omit(data)`
- **Replace missing values**: `data[is.na(data)] <- 0`
- **Handle duplicates**: `unique(data)`
- **Convert data types**: `as.numeric(data)`

---

### 10. **Data Type Conversion in R**
R provides functions to convert data between different types, such as character to numeric or factor to character.

#### Example:
```r
# Convert character to numeric
num_data <- as.numeric(char_data)

# Convert factor to character
char_data <- as.character(factor_data)
```

---

### 11. **Recoding Variables in a Data Frame**
Recoding involves changing the values of a variable based on specific rules, using `ifelse()` or `dplyr::mutate()`.

#### Example:
```r
# Recoding with ifelse
df$recoded_col <- ifelse(df$col == "old_value", "new_value", df$col)

# Recoding with mutate
library(dplyr)
df <- df %>% mutate(recoded_col = recode(col, "old_value" = "new_value"))
```

---
<br>
<br>
<br>

# <p align="center"> **Unit-5: Working with data in R** </p>

### 1. **Reordering Rows in a Data Frame using `order()` and `arrange()` in R**

- **`order()`**: It returns the indices that would sort a vector or column. To reorder rows of a data frame, you can apply `order()` to a column and use it to index the rows.
  ```R
  df <- data.frame(a = c(3, 1, 2), b = c(2, 3, 1))
  df <- df[order(df$a), ]
  ```
  This sorts `df` by column `a` in ascending order.

- **`arrange()`** (from `dplyr`): It’s a part of the `dplyr` package that makes sorting easier and more intuitive.
  ```R
  library(dplyr)
  df <- data.frame(a = c(3, 1, 2), b = c(2, 3, 1))
  df <- arrange(df, a)
  ```

---

### 2. **Reordering Columns in a Data Frame**

- **`dplyr`**: You can reorder columns using the `select()` function.
  ```R
  library(dplyr)
  df <- data.frame(a = 1:3, b = 4:6, c = 7:9)
  df <- select(df, c, a, b)
  ```

- **`data.table`**: You can reorder columns by directly specifying the desired column order.
  ```R
  library(data.table)
  dt <- data.table(a = 1:3, b = 4:6, c = 7:9)
  setcolorder(dt, c("c", "a", "b"))
  ```

---

### 3. **`setorder()` Function in `data.table` for Data Sorting**

`setorder()` sorts a `data.table` in-place, which means it doesn’t return a new object but modifies the original `data.table`.

```R
library(data.table)
dt <- data.table(a = c(3, 1, 2), b = c(2, 3, 1))
setorder(dt, a)  # sorts by column 'a'
```

---

### 4. **Importance of Reshaping Data Frames and Techniques**

Reshaping is important when preparing data for analysis or modeling. You can pivot data to better fit analysis needs.

- **`pivot_longer()` and `pivot_wider()`** (from `tidyr` package) reshape data between long and wide formats.
- **`melt()` and `dcast()`** (from `reshape2`) allow reshaping data into different formats.

---

### 5. **Transposing a Matrix in R Using `t()` Function**

`transpose()` flips rows into columns and vice versa.

```R
m <- matrix(1:9, nrow = 3)
t(m)
```

---

### 6. **Combining Vectors Using `cbind()` vs. Combining Data Frames Using `rbind()`**

- **`cbind()`**: Combines vectors, matrices, or data frames by columns.
  ```R
  cbind(1:3, 4:6)
  ```

- **`rbind()`**: Combines vectors, matrices, or data frames by rows.
  ```R
  rbind(c(1, 2), c(3, 4))
  ```

---

### 7. **Melting and Casting Data Frames Using `melt()` and `dcast()`**

- **`melt()`**: Converts wide data into long format.
  ```R
  library(reshape2)
  df <- data.frame(id = 1:3, x = c(1, 2, 3), y = c(4, 5, 6))
  melted_df <- melt(df, id.vars = "id")
  ```

- **`dcast()`**: Converts long data into wide format.
  ```R
  dcast(melted_df, id ~ variable)
  ```

---

### 8. **Advantages of Converting Pivot Data from Long to Wide Format**

- Long format is useful for time series or grouped data analysis.
- Wide format is better for individual comparisons or visualizations.

Example:
```R
df <- data.frame(id = c(1, 2, 3), var1 = c(10, 20, 30), var2 = c(40, 50, 60))
df_wide <- pivot_wider(df, names_from = "var1", values_from = "var2")
```

---

### 9. **Merging and Joining Data Frames in R**

- **Inner join**: Combines rows with common keys.
- **Outer join**: Combines all rows, filling missing values with NA.
- **Cross join**: Combines all possible pairs from two data frames.
  
```R
merged_df <- merge(df1, df2, by = "id", all.x = TRUE)  # Left join
```

---

### 10. **Performing Joins with `merge()` in R**

- **Natural join**: Matches by all common columns.
- **Left join**: Includes all rows from the left data frame.
- **Right join**: Includes all rows from the right data frame.

```R
merge(df1, df2, by = "id", all.x = TRUE)  # Left join
merge(df1, df2, by = "id", all.y = TRUE)  # Right join
```

---

### 11. **Calculating Summary Statistics**

Use functions like `mean()`, `median()`, `sd()`, etc., to calculate summary statistics.

```R
mean(df$column)
median(df$column)
sd(df$column)
```

---

### 12. **Calculating Variance and Standard Deviation**

```R
variance <- var(df$column)
std_dev <- sd(df$column)
```

---

### 13. **Importance of Frequency Tables and Cross-Tabulations**

They summarize categorical data. Use `table()` for frequency tables.

```R
table(df$column)
```

---

### 14. **One-Way and Two-Way Frequency Tables**

```R
table(df$column)  # One-way
table(df$column1, df$column2)  # Two-way
```

---

### 15. **Cumulative Frequency Tables with `cumsum()`**

```R
df$cumulative_freq <- cumsum(df$frequency)
```

---

### 16. **Frequency Tables with Intervals Using `cut()`**

```R
df$intervals <- cut(df$column, breaks = 5)
table(df$intervals)
```

---

### 17. **Cross-Tabulations for Categorical Variables**

```R
table(df$col1, df$col2)
```

---

### 18. **Row and Column Proportions of a Cross-Tabulation**

```R
prop.table(table(df$col1, df$col2), 1)  # Row proportions
prop.table(table(df$col1, df$col2), 2)  # Column proportions
```

---

### 19. **Three-Way Cross-Tabulation**

```R
table(df$col1, df$col2, df$col3)
xtabs(~ col1 + col2 + col3, data = df)
```

---

### 20. **Visualizing Two-Way Frequency Table with a Bar Chart**

```R
barplot(table(df$col1, df$col2))
```

---

### 21. **Measures of Central Tendency**

- **Mean**: Average of the data.
- **Median**: Middle value.
- **Mode**: Most frequent value.

```R
mean(df$column)
median(df$column)
mode(df$column)  # For mode, use a custom function
```

---

### 22. **Measures of Dispersion**

- **Range**: Difference between max and min.
- **Variance**: Measure of spread.
- **Standard Deviation**: Square root of variance.

```R
range(df$column)
var(df$column)
sd(df$column)
```

---

### 23. **Summarizing Data with Descriptive Statistics**

```R
summary(df)
mean(df$column)
sd(df$column)
```

---

### 24. **Significance of Normal Distribution and Plotting the Bell Curve**

Normal distribution is crucial in many statistical tests.

```R
# Generate normal distribution
data <- rnorm(1000, mean = 0, sd = 1)
hist(data, probability = TRUE, main = "Normal Distribution", xlab = "Value")
lines(density(data), col = "blue")
```

---

