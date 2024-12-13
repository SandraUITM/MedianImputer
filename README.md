# MedianImputer
Introduction to Function

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
