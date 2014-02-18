--- 
courseTitle       : Introduction to R v3
chapterTitle      : Factors
description       : Data falls into a limited number of categories very often. For example, humans are either male or female. In R, categorical data is stored in factors. Given the importance of factors in data analysis, start learning how to create, subset and compare factors now!
framework : datamind
mode: selfcontained
--- 

## What's a factor and why would you use it?

In this chapter you dive into the wonderful world of **factors**. 

The term factor refers to a statistical data type used to store categorical variables. The difference between a categorical variable and a continuous variable is that a categorical variable can belong to a **limited number of categories**. A continuous variable on the other hand, can correspond to an infinite number of values. 

It is important that R knows whether it's dealing with a continuous or a categorical variable. This, since the statistical models you will develop in the future treat both in a different way. (You will see later why this is the case.)

A good example of a categorical variable, is the variable 'Gender'. As you hopefully know by now, a human individual can either be "Male" or "Female". So "Male" and "Female" are here the (only two) values of the categorical variable "Gender", and every observation can be assigned to either the value "Male" of "Female".

*** =instructions

1. Assign to variable `theory` the value `"R uses factors for categorical variables!"`

*** =hint
Just click the Submit Answer button and look at the console.

*** =sample_code


```r
# Assign to the variable theory what this chapter is about!
```


*** =solution


```r
# Assign to the variable theory what this chapter is about!
theory <- "R uses factors for categorical variables!"
```


*** =sct


```r
DM.result <- closed_test("theory", "c('R uses factors for categorical variables!')")
```


*** =pre_exercise_code




---

## What's a factor and why would you use it? (2)

To create factors in R you make use of the function `factor()`. First thing to do is create a vector that contains all the observations belonging to a limited number of categories. For example, `gender_vector` contains the sex of 5 different individuals: `gender_vector <- c("Male","Female","Female","Male","Male")`.

It is clear, that there are 2 categories, or in R-terms **'factor levels'**, here: "Male" and "Female". 

The function `factor()` will encode the vector as a factor: `factor_gender_vector <- factor(gender_vector)`. 

*** =instructions

1. Assign to `factor_gender_vector` the character vector `gender_vector` converted to a **factor**. Look at the console and note that R prints out the factor levels below the actual values.

*** =hint
Just click the Submit Answer button and look at the console.

*** =sample_code

```r
gender_vector <- c("Male", "Female", "Female", "Male", "Male")

factor_gender_vector <- 
factor_gender_vector
```


*** =solution

```r
gender_vector <- c("Male", "Female", "Female", "Male", "Male")

factor_gender_vector <- factor(gender_vector)

factor_gender_vector
```


*** =sct

```r
DM.result <- closed_test("factor_gender_vector", "factor(gender_vector)")
```


*** =pre_exercise_code



---

## What's a factor and why would you use it? (3)

There are two types of categorical variables: a **nominal categorical variable** and an **ordinal categorical variable**. 

A nominal variable is a categorical variable without an implied order. This means it is impossible to say that 'one is worth more than the other'. Think for example of the categorical variable `animals_vector`, with the categories `"Elephant"`, `"Giraffe"`, `"Donkey"` and `"Horse"`. Here, it is impossible to say one stands above or below the other. (Note: some of you might disagree ;-) ). 

In contrast, ordinal variables do have a natural ordering, consider for example the categorical variable `temperature_vector` with the categories: `"Low"`, `"Medium"` and `"High"`. Here it is obvious that `"Medium"` stands above `"Low"`, and `"High"` stands above `"Medium"`.

*** =instructions

1. Click Submit Answer to check how R constructs and prints nominal and ordinal variables. Don't worry if you don't understand all the code just yet, we'll get to that.

*** =hint
Just click the Submit Answer button and look at the console. Notice how R indicates the ordering of the factor levels for ordinal categorical variables.

*** =sample_code


```r
animals_vector <- c("Elephant", "Giraffe", "Donkey", "Horse")
temperature_vector <- c("High", "Low", "High", "Low", "Medium")

factor_animals_vector <- factor(animals_vector)
factor_temperature_vector <- factor(temperature_vector, order = TRUE, levels = c("Low", 
    "Medium", "High"))

factor_temperature_vector
factor_animals_vector
```


*** =solution


```r
# Just click the Submit Answer button and look at the console.
```


*** =sct


```r
DM.result <- TRUE
```


*** =pre_exercise_code




---

## Factor levels

When you first get a data set, you'll often notice that it contains factors with specific factor levels. However, sometimes you will want to change the names of these levels for clarity or other reasons. R allows you to do this with the function `levels()`:

`levels(factor_vector) <- c("name1","name2",...)`
    
A good illustration is the raw data provided to you by a survey. A standard question for every questionnaire is the gender of the respondent. You remember from the previous question this is a factor and when performing the questionnaire on the streets its levels are often coded as `"M"` and `"F"`. 

`survey_vector <- c("M","F","F","M","M")`

Next, when you want to start your data analysis your main concern is to keep a nice overview of all the variables and what they mean. At that point, you will often want to change the factor levels to `"Male"` and `"Female"` instead of `"M"` and `"F"` to make your life easier. 

*** =instructions

1. Convert the character vector `survey_vector` into a factor vector. Assign to `factor_survey_vector`
2. Change the factor levels of `factor_survey_vector` to `"Male"` and `"Female"`.

*** =hint
Mind the order in which you have to type in the factor levels. Hint: look at the order in which the levels are printed).

*** =sample_code

```r
survey_vector <- c("M","F","F","M","M")
factor_survey_vector <- factor( survey_vector )
factor_survey_vector # Print to console

levels(factor_survey_vector) <- # Your code here

factor_survey_vector
```


*** =solution

```r
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)
factor_survey_vector  # Print to console

levels(factor_survey_vector) <- c("Female", "Male")
factor_survey_vector
```


*** =sct

```r
names <- c("survey_vector", "factor_survey_vector", "levels(factor_survey_vector)")
values <- c("survey_vector", "factor_survey_vector", "c('Female','Male')")
DM.result <- closed_test(names, values, check.existence = c(T, T, F))
```


*** =pre_exercise_code



---

## Summarizing a factor

After finishing this course, one of your favourite functions in R will be `summary()`. This will give you a quick overview of `some_variable`: 

`summary(some_variable)` 

Going back to our survey, you would like to know how many `"Male"` responses you have in your study, and how many `"Female"`. The `summary()` function gives the answer to this question.

*** =instructions

1. Ask a `summary()` of the `survey_vector` and `factor_survey_vector`. Interpret the result for both vectors, are they both equally useful in this case?

The fact that you identified `"Male"` and `"Female"` as factor levels in `factor_survey_vector`, enables R to show the number of elements for each category.

*** =hint
Type this in the console: `summary(survey_vector)` `summary(factor_survey_vector)`

*** =sample_code

```r
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)
levels(factor_survey_vector) <- c("Female", "Male")
factor_survey_vector

# Type your code here for survey_vector

# Type your code here for factor_survey_vector
```


*** =solution

```r
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)
levels(factor_survey_vector) <- c("Female", "Male")
factor_survey_vector

summary(survey_vector)
summary(factor_survey_vector)
```


*** =sct

```r
DM.result <- code_test(c("summary(survey_vector", "summary(factor_survey_vector"))
```


*** =pre_exercise_code



---

## Battle of the sexes

> "All animals are equal, but some animals are more equal than others"
>--George Orwell 

In `factor_survey_vector` we have a factor with two levels: male & female. But how does R value these relatively to each other? In other words, who sees R to be worth more, males or females?

*** =instructions

1. Read the code in the editor and click Submit Answer to see whether males are worth more than females.

*** =hint
Just click Submit Answer.

*** =sample_code

```r
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)
levels(factor_survey_vector) <- c("Female", "Male")

# Battle of the sexes:
factor_survey_vector[1]  # Male
factor_survey_vector[2]  # Female
factor_survey_vector[1] > factor_survey_vector[2]  # Male larger than female?
```


*** =solution

```r
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)
levels(factor_survey_vector) <- c("Female", "Male")

# Battle of the sexes:
factor_survey_vector[1]  # Male
factor_survey_vector[2]  # Female
factor_survey_vector[1] > factor_survey_vector[2]  # Male larger than female?
```


*** =sct

```r
DM.result <- list(TRUE, "Phew, it seems that R is gender-neutral. Or maybe just wants to stay out of these discussions ;-).")
```


*** =pre_exercise_code




---

## Ordered factors

Since `"Male"` and `"Female"` are unordered (or nominal) factor levels, R returns an error message. As seen before, for such factors R attaches an equal value to the levels. 

This is not always the case! Sometimes you will deal with factors that do have a natural ordering between its categories. If this is the case, we have to make sure we pass this information to R... 

Let's say your leading a research team of 5 data analysts and want to evaluate their performance. To do this, you track their speed, evaluate each analyst as `"Slow"`, `"Fast"` or `"Ultra-Fast"`, and save the results in `speed_vector`.

*** =instructions

1. As a first step, assign `speed_vector` knowing that: 
 Analyst 1: Fast, 
 Analyst 2: Slow, 
 Analyst 3: Slow,  
 Analyst 4: Fast and  
 Analyst 5: Ultra-fast.
 Just as characters for now.

*** =hint
Assign to `speed_vector` : `c("Fast","Slow",...?`.

*** =sample_code

```r
# Create speed_vector
speed_vector
```


*** =solution

```r
# Create speed_vector
speed_vector <- c("Fast", "Slow", "Slow", "Fast", "Ultra-fast")
```


*** =sct

```r
names <- "speed_vector"
values <- "c(\"Fast\",\"Slow\",\"Slow\",\"Fast\",\"Ultra-fast\")"
DM.result <- closed_test(names, values)
```


*** =pre_exercise_code




---

## Ordered factors (2)

`speed_vector` should be converted to an ordinal factor since its categories have a natural ordening. By default, the function `factor()` transforms `speed_vector` into an unordered factor. To create an ordered factor, you have to add two additional arguments: 

`factor(some_vector,ordered=TRUE,levels=c("Level 1","Level 2"...))` 

By setting the argument `ordered=TRUE` in the function `factor()`, you indicate the factor is ordered. With the argument `levels` you give the values of the factor in the correct order, e.g. `levels = c("Low","Medium","High")`.

*** =instructions

1. Rewrite the code for `speed_factor_vector`, this time taking into account that there is a specific order for the factor levels.

*** =hint
Use the function `factor()` to create `speed_factor_vector` based on `speed_character_vector`. The argument order should be set to `TRUE` since there is a natural ordering. The factor levels are in this case: `c("Slow","Fast","Ultra-fast")`.

*** =sample_code

```r
speed_vector <- c("Fast", "Slow", "Slow", "Fast", "Ultra-fast")

# Add your code below:
factor_speed_vector

factor_speed_vector

summary(factor_speed_vector)  # R prints automagically in the right order
```


*** =solution

```r
speed_vector <- c("Fast", "Slow", "Slow", "Fast", "Ultra-fast")
factor_speed_vector <- factor(speed_vector, ordered = TRUE, levels = c("Slow", 
    "Fast", "Ultra-fast"))
factor_speed_vector
summary(factor_speed_vector)  # R prints automagically in the right order
```


*** =sct

```r
names <- "factor_speed_vector"
values <- "factor(speed_vector, ordered=TRUE,levels=c(\"Slow\",\"Fast\",\"Ultra-fast\") )"
DM.result <- closed_test(names, values)
```


*** =pre_exercise_code




---

## Comparing ordered factors

Having a bad day at work, 'data analyst number two' enters your office and starts complaining that 'data analyst number five' is slowing down the entire project. Since you know 'data analyst number two' has the reputation of being a smarty-pants, you first decide to check if his statement is true. 

The fact that `speed_factor_vector` is now ordered, enables us to compare different elements (i.e. data analysts in this case). You can simply do this by using the well-known operators.

*** =instructions

1. Check whether data analyst 2 is faster than data analyst 5 and assign the result to `compare_them`. Remember the `>` operator allows to check whether one element is larger than the other.

*** =hint
You can compare the elements of the vector with the `>` operator. Relevant for this case: `vector[1] > vector[2]` checks whether the first elements of vector is larger than the second element.

*** =sample_code

```r
speed_vector <- c("Fast", "Slow", "Slow", "Fast", "Ultra-fast")
speed_factor_vector <- factor(speed_vector, ordered = TRUE, levels = c("Slow", 
    "Fast", "Ultra-fast"))

# Your code below:
compare_them <- 
# Is data analyst 2 faster than data analyst 5?
compare_them
```


*** =solution

```r
speed_vector <- c("Fast", "Slow", "Slow", "Fast", "Ultra-fast")
speed_factor_vector <- factor(speed_vector, ordered = TRUE, levels = c("Slow", 
    "Fast", "Ultra-fast"))

compare_them <- speed_factor_vector[2] > speed_factor_vector[5]
# Is data analyst 2 faster than data analyst 5?
compare_them
```


*** =sct

```r
names <- "compare_them"
values <- "speed_factor_vector[2] > speed_factor_vector[5]"
DM.result <- closed_test(names, values)
```


*** =pre_exercise_code

