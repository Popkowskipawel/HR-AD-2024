# HR-AD-2024

#Identyfikowanie wartości odstających metodą IQR
library(dplyr)
HR_numeric <- HR_cleaned %>%
  select(where(is.numeric))

find_outliers <- function(column) {
q1 <- quantile(column, 0.25, na.rm = TRUE)
q3 <- quantile(column, 0.75, na.rm = TRUE)
iqr <- q3 - q1
  
bottom_limit <- q1 - 1.5 * iqr
upper_limit <- q3 + 1.5 * iqr
  
outliers <- column[column < bottom_limit | column > upper_limit]

 if (length(outliers) == 0) {
    return(FALSE)
 }

return(outliers)
}

#FALSE = OK - żadnych wartości odstających
outliers_results <- lapply(HR_numeric, find_outliers)
print(outliers_results)

