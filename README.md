# HR-AD-2024
#Usuwanie zbędnych kolumn: EmployeeCount, Over18, StandardHours

library(dplyr)
HR <- HR %>%
select(-EmployeeCount, -Over18, -StandardHours)
HR
View(HR)
