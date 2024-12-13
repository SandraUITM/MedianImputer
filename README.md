# MedianImputer
Introduction to Function
`MedianImputer` is an R package that provides a function to perform median imputation for missing values in numeric columns of a data frame.

To install the package from GitHub:

```
In R
install.packages("devtools")

devtools::install_github("<your-github-username>/MedianImputer")

How to use in R
library(MedianImputer)
data <- data.frame(a = c(1, 2, NA, 4), b = c("x", "y", "z", "w"))
data <- median_impute(data)
print(data)


median_impute <- function(data) {
  if (!is.data.frame(data)) {
    stop("Input must be a data frame")
  }
  
  numeric_cols <- sapply(data, is.numeric)
  
  for (col in names(data)[numeric_cols]) {
    median_value <- median(data[[col]], na.rm = TRUE)
    data[[col]][is.na(data[[col]])] <- median_value
  }
  
  return(data)
}
