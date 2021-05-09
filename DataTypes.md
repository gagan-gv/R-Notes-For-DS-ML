## Basic Data Types

```
class("a") output -> character
class(12)  output -> numeric
class(-1)  output -> numeric
class(1.2) output -> numeric
class(3L)  output -> integer
class(FALSE) output -> logical
class(T) output -> logical

as.integer(12.7) output -> floors the value to 12
as.integer(FALSE) output -> 0
as.integer(TRUE) output -> 1
```
## Vectors
- A vector can be created using vector() or c()
- You can check a class of each vector too.
```
vector(mode = "character", length = 10) output -> "" "" "" "" "" "" "" "" "" "", as "" is default value
vector(mode = "numeric", length = 5) output -> 0 0 0 0 0, as 0 is default value
vector(mode = "integer", length = 5) output -> 0 0 0 0 0, as 0 is default value
vector(mode = "logical", length = 5) output -> FALSE FALSE FALSE FALSE FALSE, as FALSE is default value

vector(mode = "character", 5) == character(5) output -> TRUE TRUE TRUE TRUE TRUE

character(2) output -> "" ""
numeric(2) output -> 0 0
integer(2) output -> 0 0
logical(2) output -> FALSE FALSE

c(1,2) output -> 1 2 NOTE: Works similarly for all data types
length(c(1,2,3)) output -> 3 Gives length of vector
str(c(1,2,3)) output -> num [1:3] 1 2 3 i.e., it gives structural summary
```