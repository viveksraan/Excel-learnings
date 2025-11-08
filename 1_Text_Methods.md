### Session 1 Excel functions for combining text values
  # Spreading the formula
   <!-- 1-  Use the fill handle drag it down till whichever column you want to apply the formula but the problem is with huge data set it could be inconvinient and time consuming -->
   <!-- 2- The quicker way is double clicking on fill handle -->

  # concatenate function(older)
   <!-- The older verson still in use but prefer not using instead use CONCAT function -->
   <!-- You can use upto 255 arguments in concatenate function  -->
   <!-- The problem with this function is even if you have n contigous columns still you have to select them one by one  -->
    =CONCATENATE(A2, "_", B2)   

  # concatenate operator(&)
   <!-- The problem with & operator is also the same even if you have n contigous columns still you have to select them one by one  -->
    =A2 &"_"&B2   

  # concat function(latest)
   <!-- The preffered version-->
   <!-- You can use upto 255 arguments in concat function but as a signle range only if(columns are next to each other) else specify one by one by separating with comas  -->
   <!-- You can select all the columns in one go or could also specify the range  -->
    =CONCAT(A2 : F2)  

  # TEXTJOIN function(latest)
   <!-- Provide two great advantages over the other's-->
   <!-- First advantage is it provides a delimeter -->
   <!-- Parameters of TEXTJOIN -->
   =TEXTJOIN(delimeter, Do_ignore_empty_cells(TRUE OR FALSE), cell addresses(individualy or range))
   =TEXTJOIN("-", TRUE, H2: J2)

### Session2 split functions to split text data
  
  # LEFT
   <!-- =LEFT(cell to access, number of characters to access from left)  -->
   =LEFT(D2, 3)
  # RIGHT
   <!-- =RIGHT(cell to access, number of characters to access from right)  -->
   =LEFT(D2, 3)
  # MID
   <!-- =MID(cell to access, starting char, number of characters to access )  -->
   =MID(D2, 3, 4)

### Session3 Combining text functions to formulate more powerfull tools 
  # FIND function 
   <!-- It is used to find starting index of particular part of the string  -->
   <!-- =FIND(the part to be found, in which cell to search, from what character to start search [start_num]) -->
   <!-- It returns the position where the search text started --> 
   <!-- Always remember that unlike programing langs indexing in excel starts from 1 not 0 -->
   =FIND("-", G2, 4)
   <!-- Find could be used with other functions to get text uptil a particular special identifiable character to extract a variable length piece of info  -->
   <!-- for ex. in this string PO-Sydney-223809 we are finding the pos of second - with help of FIND then subtracting 4(3 starting char and one 2nd -) to get length of address which we could pass to MID that get the 6 chars of city -->
   =MID(G2, 4, FIND("-", G2, 4)-4)
   <!-- But we always don't get such perfect data with hyphens or a particular special character but even in those cases we could use our next function -->

  # LEN()
   <!-- Returns the number of characters in a text string -->
   =LEN(G2)
   <!-- Now you could this LEN function for the same previous problem even if there is no special char -->
   <!-- How it will would since in "POSydney223809" we know that PO(2 chars) at beggining and 223809(6 chars at end) the length of them is fixed in every CUSTOMER PO as it's a fixed length code so can we say rest of the characters are lenght of the city name  -->
   =MID(G2, 4, LEN(G2)-8)


   # NOTE: THE MOST IMPORTANT THING IS TO COMBINE THE EXCEL FUNCTIONS PROPERLY TO EXTRACT MORE AND MORE COMPLEX INFORMATION. FOCUS ON THIS IT WILL HELP YOU MASTER EXCEL REALLY FAST

### Session 4 Cleaning data 
   <!-- A lot of time your data is too messed up where these tools will be really helpful -->
  # CLEAN
   <!-- Strips non-printable characters from text  -->
   <!-- CLEAN function helps us clean first 32 non printable characters in ASCII table but be cautious it doesn't work for other characters, so for those we will be using trim -->
   <!-- Since ASCII value of white space(32) is not one of the first 32(0 to 31) characters so it can't be removed by CLEAN we need TRIM -->

  # TRIM 
   <!-- Removes Leading spaces  -->
   <!-- Removes Trailing spaces  -->
   <!-- Removes extra spaces(need more than one space and reduces multipe spaces to one)  -->
   <!-- So if we'd use both together both first 32 non printable characters and after that all the extra white spaces would be removed -->
   =TRIM(CLEAN(E2))

### Changing case
  # UPPER
   <!-- Converts text to upper case -->
   UPPER(B2)
  # LOWER
   <!-- Converts text to lower case -->
   LOWER(B2)
  # PROPER
   <!-- Capitalises the first letter of each word -->
   PROPER(B2)

### Removing and replacing text characters using SUBSTITUE function
  # SUBSTITUTE
   <!-- =SUBSTITUTE(cell from which we want to take data, text to be replaced, replacement text, [instace(only one multiple selecting instances are not allowed either all or any ones) to replace if not given all instances will be replaced]) -->
   =SUBSTITUTE(F2, "S", "$")
   <!-- A lot of time it seems like your text is having a whitespace but it's some other character because of which thei's an unnecessary space to handle this you can't use TRIM, CLEAN or direct SUBSTITUTE instead we would be using mid to access that exact character from the original string and replace it with "" to get rid of the unnecessary char -->
   =SUBSTITUTE(SUBSTITUTE(F2, "S", ""), MID(F2, 2, 1), "")
  # For getting unicode of any char we can use =unicode(char) and similarly to get unichar we can use =unichar(code)