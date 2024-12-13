# MedianImputer
Introduction to Function
`MedianImputer` is an R package that provides a function to perform median imputation for missing values in numeric columns of a data frame.


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
