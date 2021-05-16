# Data Types and Structures in R 
## Theory
### Common Data Types
```
Character --> 'a', 'Hello World'
Numeric --> 123, 1.2, -5
Integer --> 3L, 1000000L
Logical --> TRUE, FALSE, T, F
```
### Atomic Vectors
- Only Holds data of single type
- Can hold only common data types
- R supports missing data in vectors as NA which can be used for all data types
- Special Values
    Inf: Infinity
    NaN: Not a Number or undefined value

### Coercion
- Other name for type casting
- Is of 2 types: Implicit and Explicit
- Implicit occurs when 1 data type is casted to other data type due to circumstances or context
- Explicit occurs when the user converts the data type

### Matrices
- Extension of numeric/character data types
- It's not a seperate type object
- An atomic vector with dimension
- Fill column wise by default
- Referenced by index respective of each dimension in single square matrix

### Lists
- They act as containers
- Not restriced to single type of data in single list, i.e., can encompass mixture of data types
- Can be referred as a generic vector
- Can be nested
- Referenced by index using double square brackets
- Can be extremely useful inside functions such that it helps to return multiple objects

### Dataframes
- Most Important Data Type in R
- It's a special type of list where every element of the list has same length otherwise called as rectangular list
- Used for tabular data
- Some helper functions as follows:
  - head() gives first 5 rows
  - tail() gives last 5 rows
  - dim() gives dimension
  - nrow() gives number of rows
  - ncol() gives number of columns
  - names()/rownames()/colnames() gives name of both, row and columns respectively
  - str() returns structural summary
  - summary() returns summary of data
- Referencing similar to matrices

### Tibbles
- A tidyverse package
- Can be called modern dataframes
- Does Less, Complains more, i.e, forces you to confront problems
- Leads to cleaner more expressive code
- Comes with enhanced print() thus making it easier to use large datasets containing complex objects
- Any function working with dataframes will work with tibbles
- #### Tibbles: The simple data frame?
  - Never changes type of inputs
  - Never changes the names of variables
  - Never create row names
  - Possible column names are available i.e., can rename column other than respective variable name and with variable rule bending by surroung then with backticks(`)

### Transposed Tibble or tribble
- function name tribble()
- customised for data entry in code like column headings defined by formulae or seperated by commas
- Makes it possible to lay out small amount of data in easy to read form
- Comes with refined print()
  - Shows only first 10 rows
  - Shows all columns that fit on the screen
  - Makes it easier to work with large data
  - Each column reports its name and type which is similar to str() in dataframes
  
### Resources for tibbles: 
  - https://r4ds.had.co.nz/tibbles.html
  - https://tibble.tidyverse.org

## Codes
### Basic Data Types 

```r
class("a") #output -> character
class(12)  #output -> numeric
class(-1)  #output -> numeric
class(1.2) #output -> numeric
class(3L)  #output -> integer
class(FALSE) #output -> logical
class(T) #output -> logical

as.integer(12.7) #output -> floors the value to 12
as.integer(FALSE) #output -> 0
as.integer(TRUE) #output -> 1
```
## Vectors
- A vector can be created using vector() or c()
- You can check a class of each vector too.
```r
vector(mode = "character", length = 10) #output -> "" "" "" "" "" "" "" "" "" "", as "" is default value
vector(mode = "numeric", length = 5) #output -> 0 0 0 0 0, as 0 is default value
vector(mode = "integer", length = 5) #output -> 0 0 0 0 0, as 0 is default value
vector(mode = "logical", length = 5) #output -> FALSE FALSE FALSE FALSE FALSE, as FALSE is default value
vector(mode = "character", 5) == character(5) #output -> TRUE TRUE TRUE TRUE TRUE

character(2) #output -> "" ""
numeric(2) #output -> 0 0
integer(2) #output -> 0 0
logical(2) #output -> FALSE FALSE

c(1,2) #output -> 1 2 NOTE: Works similarly for all data types
length(c(1,2,3)) #output -> 3 Gives length of vector
str(c(1,2,3)) #output -> num [1:3] 1 2 3 i.e., it gives structural summary

#if you want to generate a vector sequence for eg 1-10 you can do it using ':' like 1:5 where output -> 1,2,3,4,5 or you can use seq() like seq(1,5) giving the same output
#To get a seq of even numbers one can do seq(2,10,2) syntax(from=, to=, by=)
```
### Vector Arithmetics
```r
#consider a vector x <- c(1,2,3) and y <- c(4,5)
x + 5 #output -> 6,7,8 basically adds a vector of dimension 1 row and 3 columns of element 5
x + y #output -> 5,7,7 adds the first 2 columns of both vectors and to maintain dimension it the lower dimension vector repeats it self

#similarly all arithmetic operations or PEDMAS or BODMAS operations are performed
```
### Vectors Dealing with Missing Values (NA)
```r
x <- c(5, NA, 0.25) #This is of type numeric and goes the same for all basic data types

# To check if a value is NA or Not we use is.na()
is.na(NA) #output-> TRUE
is.na(x) #output -> FALSE, TRUE, FALSE

# To check if there exists a NA value in a vector we use anyNA()
anyNA(x) #output -> TRUE
```

### Vector Coercion
```r
# Just go through Coercion section above to get an idea
class(c(TRUE, 2 )) #output -> numeric ... Why? Because of implicit coercion TRUE is converted to 1 if FALSE it would be converted to zero
class(c("a", TRUE)) #output -> character ... due to implicit coercion

#Order of coercion character > numeric > integer > logical
```
### Vector Element Naming
- Done using names()
```r
#consider a vector x as c(1,2,3,4,5) and if you want a key value pair of this vector you can do it as follows
x <- c(1,2,3,4,5)
names(x) <- LETTERS[1:length(x)] 
x
#2 line output as follows
#A B C D E
#1 2 3 4 5
names(x) #output -> A B C D E

#NOTE: As there are only 26 LETTERS(A-Z) or letters(a-z), after 26 indices it will give NA as the name of vector element
#Also never consider this as a matrix

#ALTERNATIVE METHOD is while creating the vector
y <- c("a"=0, "b"=1)
names(y) #output-> a b
```
