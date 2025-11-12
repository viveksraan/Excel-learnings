### Logical and Lookup function introduction
    
  # IF ELSE function(Logical function)
   <!-- 
     -> Exactly similar to conditionals in programming
     IF(logical expression, task to perform if expression evaluate to true, task to perform if expression evaluates to false )
    -->
  # VLOOKUP (Lookup function)
   <!-- 
    1. Widely used by businesses to connect the data sets and for error checking 
    2. But downside is that they are ofter criticized for being inefficient
    3. But still it's really imp. to learn them as they are highly efficient in particular usecases and are very easy to implement
    4. Two types 
       i) range lookups: used to categorize data, for ex. if students fall in 70 to 79%
       ii)  match vlookup: more commonly used one, it helps look for a specific thing like a customer id and return corresponding like customer name.
    -->
  # X Lookup function 
   <!-- are a new upgrade over V lookup functions. If fullfils all the shortcoming of V lookups, works vertically as well as horizontally and evne allows a serch on wildcard characters 
    -->
   # Only office 365 uses it at this stage 

  # INDEX and MATCH lookup functions
   <!-- 
        1. These function are also a good replacement of Vlookup functions.
        2. Although two independent functions but generally MATCH function is nested inside the INDEX
    -->

### Logical operations IF ELSE
 <!-- 
    IF takes three args condition, to be returned if condition is true, to be returned if condition is false
  -->
 # Using IF ELSE to add debits and subtract credits 
  =IF([@[Payment Date]]>[@[Due Date]], "Yes", "No")

  <!-- 
    1. Similar to general programming we can nest IF's as well 
    2. Max 64 IF's could be nested
    -->

### VLOOKUP/HLOOKUP function
  1. References a vetical table to find and return values
  2. Understand it like you have one piece of info for a person and now you want to look for some other
  3. for ex if you have someone's name and you want to look for their telephone number in a phone directory. VLOOKUP automates this type of process 
  4. V lookup is heavily used for matching data of two tables which share a relation so that you can verify that the secondary table is not having entries whose primery link doesn't exist and secondaly are the balances of primary and secondary matching.

  # Syntax
   VLOOKUP(lookup value, /table/array(the full table with the first col. to be matched), col index(for the column whose value will be returned depending upon the row match), [range(approximate match)])
   <!-- 
     1. VLOOKUP function is very good at categorising data and it was designed particularly for this usecase 
     2. Although in modern data analysis this is not the most typical use of it.
     3. We can solve most of the categorising problems with IF ELSE also but it would need a huge formula with multiple IF ELSE's and that would lead too a very messy formula.
    -->
   # NOTE: ALWAYS REMEMBER THAT TABLE DATA SHOULD BE ALWAYS SORTED IN ASCENDING ORDER TO USE VLOOKUP/HLOOKUP  

### XLOOKUP
  1. VLOOKUP has huge limitations the column to be matched from the table should always be first one which could be tackled by XLOOKUP
  2. Finds values in a range with advvanced functionality. Supports vetical and horizontal ranges
  3. It doesn't works with entire tables it just look up at the individual columns/rows
 
  # Syntax
   =XLOOKUP(lookup value, lookup array, return array, [value to be returned if lookup value not found], match mode, search mode )
  
  # MATCH MODE
   1. 0 for exact match 
   2. -1 for exact or smaller match
   3. 1 for exact or larger match
   4. 2 for wildcard match

  # SEARCH MODE
   1. 1 First to last
   2. -1 Last to first 
   3. 2 Binary search Ascending order
   4. -2 Binary Search Descending order

### Performing advanced lookups with INDEX and MATCH functions
  
  # INDEX
   # SYNTAX
   =INDEX(column/row name, index)
   <!-- will return the value at that particular index in the column/row passed -->
   # NOTE: Index can be used to lookup a value based on a 2 dimensional lookup_array also for ex. 
     =INDEX(B7:E201, C4, D4)
  
  # MATCH
   # Syntax
   =MATCH(lookup value, lookup array(it should be a single row or column unlike VLOOKUP where we can give whole table), do we want range lookup(1) or exact match(0))
   # NOTE: MATCH doesn't care if lookup_array is vertical or horizontal because of which you don't have to switch between two different functions for vertical and horizontal as you have to do with VLOOKUP and HLOOKUP
   <!-- will return the position of the lookup value -->
   <!-- Always be cautious it returns at what position the value was in terms of 1 for the first value to be matched 2 for second value to be matched it doesn't care about  column index row index, or even the starting element of the column  -->
   =INDEX(Population, MATCH(A4, Ctry, 0))
   <!-- Now here MATCH is looking for the country name in A4 starting from the first cell in Ctry range and if first value in the range matches it returns 1, so and so on, irrespective of that is it the first cell in that column or not -->
  
  # Power of INDEX and MATCH is combining together where they can create a really easy to use search bar option for a huge table for example searching population of a country from a table we can simply provide a drop down for country where user can select one of the available countries and population cell will find the index of Country using MATCH and then will ask INDEX function to return the value at that index in the population column