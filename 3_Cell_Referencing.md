### CELL REFERENCING
  # NOTE: To select all the cells in a row/column press ctrl+shift+arrow depending upon the direction you are approaching
  <!-- 
     Instead of using cell referencing we can also use the constant value, but we have two solid reasons for not doing that:
     1. That way, if later we have to change the constant then we have to make change everywhere which is not at all convinient
     2. We also detailed documentation. When at top of our sheet we add a cell with value let's say 0.36 and a label for it Penalty Rate: so it's very clear that wherever this value is used we are charging penalty rate which would become unclear if we will use constants. 
  -->
  =G4+$F$1*A4

### Named range
  <!-- 
   1. Named ranges are very useful at place of  using absolute cell referencing as it could be more descriptive
   2. Just select the cell go to formula tab and then on name manager link
   4. We can also select a range of cells now let's say I need the whole range of cells I can use range name instead of passing starting_address:ending_address or else if you need one cell from the named range use INDEX(Range_Name, index) and remember indexing starts from zero in this case even in most of the cases with excel
   5. Here according to your requirement you can create edit or delete a named reference
    -->
    
  # NOTE: most of the proramming variable declaration rules also apply on Named ranges
  
  # Create from Selection
   <!-- 
   1. Allows us to create multiple named ranges from the selected cells
   2. For example if I would just select multiple columns headings with their multiple cells and press Ctrl+Shift+F3 or go to formula tab and select create from selection option I would get multiple named tags created 
    -->

  # Name manager
   <!--
   1. Excel provide us option to edit and delete our already created named ranges also by just going at the name manager
   2. A user using our excel sheet might not be aware about our named ranges so they can paste it in the spreadsheet to be able to work with them more easily by going at the same use in the formula and selecting paste names 
     -->

### Calculating using Named ranges and functions  COUNTIFS & SUMIFS
  
  # Constants
   <!-- Let's say I want to charge a fixed proportion of fine on all the late paid installments of 2.5%, and I want it to be stored at a fixed source to avoid manually changing all the entries with change in rates  but I don't want to store it anywhere in the sheet so I can create a named range but instead of storing cell reference in refers to i can give a constant value of 2.5  -->

  # The major adavantage of Named Ranges
   <!--
      1. The biggest use of it is when you have multiple data sheets and lets say you have to compute these in the final report sheet.
      2. Now in this scenario Named ranges really shine.
      3. Just create the Named range for the whole column 
      4 Use =FORMULA(range_name) that's it. For example let's say =SUM(amount_paid)
    -->

  # COUNTIF/COUNTIFS
   <!-- 
    1. If we want to count all the entries matching a certain condition in a range we can use COUNTIF(just single range criterion allowed), or COUNTIFS(multiple range criterions allowed)
    2. =COUNTIFS(range_name, cell_address/value...)
    -->
   # let's say value at A8 is Sydney so then only entries matching with that value will be counted 
    =COUNTIFS(Location, A8) 

  # SUMIF/SUMIFS
   <!-- 
    1. If we want to sumup all the entries matching a certain condition in a range we can use SUMIF(just single range criterion allowed), or SUMIFS(multiple range criterions allowed)
    2. =SUMIFS(range_name, criterior range, cell_address/value ...)
    -->
   # let's say value at A8 is Sydney so then only entries matching with that value will be summed up 
    =SUMIFS(Amount_Paid, Location, A8) 

  # Similarly we alos have AVERAGEIFS, MAXIFS & MINIFS

### Using Named ranges to automate workbooks & data validation with Named ranges COUNTA OFFSET
  
  # Data Validation
   <!-- 
   1. A feature designed to control what a user can enter into a cell 
   2. Usecases are setting a range so that user enters a number in that range only
   3. Or creating a drop down list
   4. Just go to to data and data validation
   5. For a data validation list you can enter all the options manually but then whenever a new option will be created you have to enter it in the data validation list manaully
   6. So it's better to give a range to it by going to the formulas>use in formula and select the range you want to use
   7. Keyboard shortcut for use in formula is F3
   -->
  
  # COUNTA
   <!-- similar to COUNT but counts everything excepn non empty cells while COUNT counts only numerals -->


  # OFFSET
  <!-- Returns a cell or range that is a specified number of rows and columns from a cell or range -->

  # Making named ranges more dynamic
   <!-- 
    1. Select a named range from the name manager 
    2. Now change the refers to menu option use OFFSET(starting_cell_address, 0, 0, COUNTA(range of cells you are selecting))
    3. Remember first 0 indicates rows away from the selected cell and second 0 indicates columns away from the selected cell 
   -->
   =OFFSET('Recon Analysis'!$A$8,0,0,COUNTA('Recon Analysis'!$A$8:$A$18))

