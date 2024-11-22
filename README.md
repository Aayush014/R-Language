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

