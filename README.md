# HR-AD-2024
#Usuwanie zbędnych kolumn: EmployeeCount, Over18, StandardHours

library(dplyr)
HR <- HR %>%
select(-EmployeeCount, -Over18, -StandardHours)
HR
View(HR)
duplikaty <- HR[duplicated(HR) | duplicated(HR, fromLast = TRUE), ]
install.packages("naniar")
library(naniar)
vis_miss(HR)
miss_var_summary(HR)
#jak możemy zauważyć, braki danych występują w kolumnach Age (7%), Attrition(10%) oraz Monthly Income(10%)
gg_miss_upset(HR)
gg_miss_var(HR)

install.packages("dlookr")
library(dlookr)
HR$MonthlyIncome1<-imputate_na(HR, MonthlyIncome, Attrition, Age method ="mice")

