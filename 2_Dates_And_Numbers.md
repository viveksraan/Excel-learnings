<!-- 
    Tasks covered in this module
    1. Converting data types (VALUE, TEXT)
    2. Understanding dates and basic date functions(TODAY, NOW, MONTH, DAY, YEAR)
    3. Generating valid dates(DATE)
    4. Calculating days between two dates(DAYS, NETWORKDAYS, WORKDAY)
    5. Calculating dates from a given date(EOMONTH, EODATE)
 -->

### VALUE
  # Always keep in mind that in excel numbers are always alligned to the right and text is always aligned to the left
  # Never use VALUE function with non numeric data type it's not going to work
  <!-- VALUE function Converts text that appears in a recognized format to a numeral -->
  VALUE(D4)
  =VALUE((SUBSTITUTE(SUBSTITUTE(F2,"S",""),MID(F2,2,1),"")))

### TEXT
  <!-- 
  -> It's exact opposite of VALUE converts numeric data to text 
  -> =TEXT(CellAddress, Format)
  -> Various format options are 
    -> D return date with no extra 0
    -> DD return date with extra 0 if it's one digit date
    -> DDD returns day name with three char format 
    -> DDD returns full day name
    -> Similarly M, MM, MMM, MMMM, YY, YYYY, H, HH, M, MM, S, SS are are also there 
   -->
   =TEXT(D2, "DD/MM/YYYY")
    27/11/2025

   =TEXT(D2, "DDDD/MM/YYYY")
   THURSDAY/11/2025

### Understanding dates and basic date functions(TODAY, NOW, MONTH, DAY, YEAR)
  # Dates are just numbers written in a particular format when we add a number in any cell by default the number format is general if you will change the number format to date you will automatically get a number according to the value you entered in the cell. For example if you enter 1 in a cell you and change the format to date you will get 1900 jan 1  since the dates start from 1900

  # NOW
  <!-- Now function returns the current time but for getting the correct result you have to set the number format to time -->
  =NOW()
  # TODAY
  <!-- TODAY function returns the current date but for getting the correct result you have to set the number format to date -->
  =TODAY()

  # DAY, MONTH & YEAR
  <!-- Similar to LEFT, RIGHT and MID functions we also have DAY, MONTH and YEAR functions  -->
  <!-- Just the number format of base cell should be correct and the number format of resultant cell should be general -->
  # if contenct of C2 is 02-03-2020
  # these function won't work on Dec/Nov/Jan...
  # But if you have 13Dec this format they work
  # so if sometimes if you are given month only that two in string use concatenation with some random date to get month for ex. if content in B2 is Apr use =MONTH(3&B2)
  =DAY(C2)   # will return 02
  =MONTH(C2) # will return 03
  =YEAR(C2)  # will return 2020

  # DAYS
  <!-- Returns the number of days btw two dates -->
  =DATES(C2, today)
  =DATES(C2, D2)

  # DATE 
  <!--
    1. If you want to create a date element in a cell we can use this function 
    2. But always remeber that all the three arguments for date month and year should be in numbers 
  -->
  =DATE(2025, 04, 17)
  <!-- it will result into 17-04-2025 -->


  # CALCULATIONS WITH DATES
   <!-- Finding number of days between any two dates -->
   =C4-D4
-
  # TEXT() Finding day of the week for a particular date
   <!-- Let's say you have a date for which you want to know the date you can use  -->
   =TEXT(D4, "DDD")

  # WORKDAY
   <!-- But now let's say you want to know the exact day after some days starting from a day but not considering weekend only workdays(Mon to Fri)   -->
   =TEXT(WORKDAY(the starting date, number of days), "DDD")
   =TEXT(WORKDAY(D5, 7), "DDD")
  
  # WORKDAY.INTL
   <!-- WORKDAY assumes it to be a 5 day week and doesn't allows you to add particual dates which are not working day so in that case you can use WORKDAY.INTL -->
   =TEXT(WORKDAY(the starting date, number of days, string of working/non-working days(1 being non working day)), "DDD")
   <!-- Let's say I want last three days friday saturday and sunday to be considered as offdays and also let's say that their are some public holidays as well which you have stored in a separate file you can pass those as well by writing 'file_name'!StartingRange:EndingRange -->
   =TEXT(WORKDAY.INTL(D5, 2, "1010111", 'NSW Holidays 2020'!A4:A15), "DDD")

  # NETWORKDAYS and NETWORKDAYS.INTL
  =NETWORKDAYS(startDate, endDate, [holidays])
  =NETWORKDAYS.INTL(startDate, endDate, workingdays"1101100" ,[holidays])
   <!-- Exact same as Workday but returns the count of working days till that day not the name of that day -->

   
### More sophisticated date calculation with EOMONTH and EDATE
  # EOMONTH(last date of month for x months after)
   <!-- It gives us the last date for the month we want for  -->
   <!-- =EOMONTH(current_date, how many months backward/forward) -->
   <!-- 0 means current month, -x means x months ago then the current month or x means x months later than this -->
   =EOMONTH(D5, -3)
     
   <!-- at first this function might seem bit useless but trust me it's really useful when accompanied with workday in an automated sheet -->

  # EOMONTH(D5,0) will return date for the last day of month 3 then workday use that same date and compute the fifth working day starting from that date which will be 07-04-2020 as value in D5 was 02-03-2025 and there are two non working days(sat, sun)   
   =WORKDAY(EOMONTH(D5,0), 5)
   <!-- For example if you simply wants to charge credit card bill on the fifth working day after the end of current month you can use abover formula -->

  # EDATE(date exact x months after from current date )
   <!-- 
   1- It's similar to EOMONTH in almost every aspect 
   2- =EDATE(current_date, how many months backward/forward) 
   3- Now the below used EDATE function will return a date exact two months back from the date in D5
    -->
   =EDATE(D5, 2)
 
  # NOTE: But be cautious a lot of times you will encounter a situation where you will be intersted in a working day but EDATE or even lot of other functions as well will return a non working day in those type of situations it's better to use it inside WORKDAY
  # NOTE: But if you will pass the second arg which is the no. of days after as 0 you won't get anything else than the same exact date returned by the internal function so we ofter use as follows subtracting one from the date returned by internal function and then checking the next working day after the date
  =WORKDAY(EDATE(D5, 2)-1, 1)

  # DATEDIF 
  <!-- 
  1. It's a very useful function when it comes to find the dif in dates such as finding the number of years/months/days between two dates 
  2. It's really useful for automating years service, age etc by using today() with it
  -->
  DATEDIF(startDate, endDate, [format("Y", "M", "D")])
  DATEDIF(D5, today(), "Y")

