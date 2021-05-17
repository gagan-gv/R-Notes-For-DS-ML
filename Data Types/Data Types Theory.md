# Data Types and Structures in R 
## Theory
### Common Data Types
```
Character --> 'a', 'Hello World'
Numeric --> 123, 1.2, -5
Integer --> 3L, 1000000L
Logical --> TRUE, FALSE, T, F
```

### Coercion
- Other name for type casting
- Is of 2 types: Implicit and Explicit
- Implicit occurs when 1 data type is casted to other data type due to circumstances or context
- Explicit occurs when the user converts the data type

### Atomic Vectors
- Only Holds data of single type
- Can hold only common data types
- R supports missing data in vectors as NA which can be used for all data types
- Special Values
    Inf: Infinity
    NaN: Not a Number or undefined value

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
- Some helper functions are as follows:
  - head() gives first 5 rows
  - tail() gives last 5 rows
  - dim() gives dimension
  - nrow() gives number of rows
  - ncol() gives number of columns
  - names()/rownames()/colnames() gives name of both, row and columns respectively
  - str() returns structural summary
  - summary() returns statistical + structural summary of data
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

