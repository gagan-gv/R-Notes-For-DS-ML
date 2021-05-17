# Data Types and Structures in R 
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

#Concatenation of Vectors, consider 2 vectors x and y as follows
x <- 1:3
y <- 4:7
z <- c(x,y) # vectors get concatenated here and can be done similarly for n vectors
z #output 1 2 3 4 5 6 7
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

## Matrices
- Can create a matrix using matrix(data=, nrow=, ncol= byrow=, dimnames=)
  - data = is the data to be filled in matrix, default is NA
  - nrow, ncol = No. of rows and columns respectively, default is 1
  - byrow = How to fill the matrix, i.e., by row or by column, default is FALSE so it fills by column
  - dimnames = To name rows and columns, default is NULL
```r
x <- matrix(data = c(1,2,3,4,5,6), nrow = 3, ncol = 2, byrow = TRUE)
x
#Output as follows
#1 2
#3 4
#5 6
y <- matrix(data = c(1,2,3,4,5,6), nrow = 3, ncol = 2, byrow = FALSE)
y
#output as follows
#1 4
#2 5
#3 6

#dim() is used to find dimension of matrix
dim(x) #output ->3 2
# To change dimension of matrix do the following
dim(x) <- x(2,3)
x
#output as follows
#1 2 3
#4 5 6

#To convert vectors to matrices we can use cbind or rbind
a <- c(1,2,3)
b <- c(4,5,6)
z <- cbind(a,b)
#output as follows
#1 4
#2 5
#3 6
# NOTE: when using cbind the columns get the name of vectors variables
rbind(a,b)
#output as follows
#1 2 3
#4 5 6
# NOTE: when using rbind the rows get the name of vector variables

#Check colnames using colnames() and row names using rownames()

z[1, 1:3] #output would be 1st row completely
```

## Lists
- Can be defined by list()
- Every element in a list is considered as a vector or in simple words list is a collection of vectors
- Refer the notes mentioned above under theory section
```r
x <- list(1, "a", TRUE, 9L)
x
#output would look like the following
#[[1]]
#[1] 1
#
#[[2]]
#[1] "a"
#
#[[3]]
#[1] TRUE
#
#[[4]]
#[1] 9

x[2]#output -> "a" in a list format
x[[2]] #output -> "a" in a vector format

# To Nest: list(..., ,list(), ,...)

#To find class of each element with using loops can be done using lapply(X, class)
lapply(x, class) #output -> class of each element in a list format
```
### List Naming
- Order of naming doesn't matter it can be like a b c d or b a d c
```r
x <- list(a = "a", b = 2, c = c(1L,2L,3L), d = list(T,F,T))
x
#output as follows
#$a
#[1] "a"
#
#$b
#[1] 2
#
#$c
#[1] 1 2 3
#
#$d
#$d[[1]]
#[1] TRUE
#
#$d[[2]]
#[1] FALSE
#
#$d[[3]]
#[1] TRUE

# To access list elements via name, we do list name $ list element name
x$a #output-> "a"
```

## Data Frames
- Refer Theory Section
- Data frames are created using data.frames()
- To refernce data frame we use $ symbol in a similar manner of lists
```r
people <- data.frame(Name = c("Ram", "Shyam"), Age = c(32, 26), Address = c("A1", "A2")) #eg dataframe
people #output would be tabular format
people$Age #output -> 32 26

people[2:3] #output 2nd and 3rd column in dataframe format
people[1, 2:3] #output 1st row of 2nd and 3rd column in dataframe format

class(people) #output -> data.frame
class(people[[2]]) #output -> numeric would give same output for class(people$Age)
class(people[2]) #output -> data.frame ...Why? because a single square brackets used for referenceing a data frame gives a data frame
```
### Data Frames: Helper Functions
```r
df <- data.frame(id = letters[1:15], x = 1:15, y = 16:30)
head(df) #outputs first 6 rows
head(df,8) #outputs first 8 rows
tail(df) #outputs last 6 rows
tail(df,8) #outputs last 8 rows

View(df) #shows the complete dataframe

dim(df) #gives the dimensions of data frame here output -> 15 3

nrow(df) #gives number of rows
ncol(df) #gives number of columns

str(df) #gives the structure of dataframe

summary(df) #gives the statistical + structural summary of data frame

names(df) #gives names of rows and columns NOTE: Check below what happens if names are not given to rows and columns
rownames(df) #gives rownames #if not defined gives numbers from 1 to total rows
colnames(df) #gives colnames #if not defined gives names of values assigned
# Can changes row and column names by and they should be vectors of equal length of row and columns respectively
rownames(df) <- "Name you want to give"
colnames(df) <- "Name you want to give" 
```
## Tibbles
