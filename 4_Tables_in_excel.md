### Tables Intro
  
  # What are Tables in Excel?
   <!-- 
   1. A table in Excel is a structured layout for data where rows act like individual records and columns act like fields. 
   2. When you convert a normal range into a table, Excel treats it as a single, organized object instead of loose cells. 
   3. The table automatically carries its own name, headers, formatting, and internal logic. 
   -->

  # Why Use Tables Instead of Normal Named Ranges?
  <!-- 
  1. Named ranges let you label a group of cells,  but they stay fixed unless you manually resize them. 
  2. This causes problems when new data is added, because formulas won’t automatically pick up new rows or columns. 
  3. Tables solve these limits. A table grows on its own when new data is entered, and every formula connected to it updates instantly. Excel also applies consistent formatting, filters, and formula fill without any extra work from the user. 
  4. Even someone with no Excel background can type into the next row or make a new column and the table will apply all rules, formatting, and formulas automatically.
  -->

  # Creating a table
   <!-- 
      1. For creating a table just select any cell from that part and click on insert table from the ribbon tab. 
      2. The only restriction is that table could only be create if every column is a single attribute of the data that means all the cells in that columns have a particular data atribute and every row is a single entry there's no mashup.
      3. Creating a table provides you an extra ribbon tab Table design but be careful as soon as you will click a cell outside your table you won't be able to see this tab as it works exclusively on table. 
   -->
  # Changing name 
   <!-- Go to Table Design tab there would be a Name cell and simply rename your file according to your requiremnt in that cell  -->

  # Removing the table
   <!-- 
    1. Before removing the table just be carefull that removing the table won't remove the formating so if you want to remove formating as well go to: 
           table design > tablestyles
           and select the light formating 
    To remove the table just go to table design and select convert to range from the tools section
    -->


### Customising the tables
  
  # Styling
   <!-- Now if you want do fun styling stuff with your table you can choose one of the many Table style options -->
   # Header row(distinguish header row) 
   # First/ column(distinguishes first/last column)
   # Filter button(adds or remove filter buttons) 
   # Total row with inbuilt aggregate functions and time to time you can remove and add this row, even after removing if you will add it back you will get the same computations you made in past unaffected 
   # Banded rows/columns
  
  # Selecting a column
   <!-- No need of ctrl+shift+down arrow instead go at the top of the attribute cell cursor will change into a black arrow click once all cells except the header would be selected click once again header will also be selected-->
  
  # Moving a column
   <!-- Just select a column go to the left edge of it, you will get a four arrow black mover drag and drop at whichever position you want to take it  -->
 
  # Similarly we can select and move rows as well

  # We can delete multiple rows in a table without stressing about the data at right of the table it won't move a bit. Only the botom rows will move upwards automaticaly without even choosing (move right, move left or any shit of that sort)

### Sorting and Filtering the table
  
  1. We can simply click on the arrow next to column heading and perform sorting and filtering in our data
  2. But there's a limitation of this functionality once you do auto sort in second attribute the first attribute based sorting will automatically reset this is not the case with filter filters don't create this problem
  3. You can simply go to Sort and filter in the editing tab of home section and select custom sort and add as many levels you want 
  4. For removing filter/sort click on the attribute you want to remove filter for and select clear filter from 
  5. But if you have multiple sorts and filters and you want to remove all of these just go to Data tab>sort & filter>select clear

### Slicer
   1. Till now whatever we have discussed could be done with ranges as well but it's not the case with slicer
   # 2. Go to Table Design > Insert Slicer> Select the attributes for which you want slicer
   3. You will be able to see the slicers on your display 
 
  # Selecting slicers together
   1. Shortcut to select all the slicers together just press the shift key and select the bottom most slicer and now you can resize or move all the slicers simultaneously 
  
  # Now you can use the slicers to sort and filter data in the table