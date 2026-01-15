# multivariable-logistic-regression-stata
These files contains commands, output, and interpretation of multivariable logistic regression in stata using both categorical and numeric independent variables.
[github multivariable logistic regression stata log file.pdf](https://github.com/user-attachments/files/24638395/github.multivariable.logistic.regression.stata.log.file.pdf)
[Github Multivariable logistic regression step by step commands.docx](https://github.com/user-attachments/files/24638382/Github.Multivariable.logistic.regression.step.by.step.commands.docx)
Data used can be assessed from kaggle using the link https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset
use "C:\Users\USER\Downloads\heart disease\stroke.dta"
log using "C:\Users\USER\Downloads\heart disease\multivariate logistics.smcl"
*****multivariable logistic regression.
*****describe each variable to check which are numeric and which are categorical
describe gender
****transform gender to numeric
encode gender, generate (gender_num)
describe gender_num
describe age
describe hypertension
describe heart_disease
describe avg_glucose_level
describe bmi
****now that the relevant variables have been inspected and transformed, logistic regression can be performed
logistic stroke i.smoke_num i.gender_num bmi avg_glucose_level i.heart_disease i.hypertension age
tabulate gender_num
logistic stroke ib3.smoke_num i.gender_num bmi avg_glucose_level i.heart_disease i.hypertension age
*****used the code ib3.smoke_num to specify the category (never smoked) i wanted as my reference category for the variable smoke_num
****permanently set category 3 as reference category for variable smoke_num
fvset base 3 smoke_num
*****interpretation: when all other variables are held constant, a one unit increase average glucose level, increases the odds of stroke by 0.5%. when all other variables are held constant, the odds of stroke in individuals with hypertension is increased by 67.8% compared to those without hypertension. an additional year of age increases the odds of stroke by 7.1%. average blood glucose, hypertension, and age have p-valus <0.05, thus these finndings are not a result of chance. They are statistically significant.
****adjusting for gender, bmi, average glucose level, presence of heart disease, hypertension, and age, there was statistically significant relationship betweensmokers/former smokers and stroke when compared with individuals who had never smoked.
log close
