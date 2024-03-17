# Customer_Data_Pre-processing
The processing of customer records for business purposes and further analyses including representation changes, filtering, and deriving some new attributes / metrics.

Using standard python (No pandas / seaborn) with default libraries (os, sys, time, json, csv, …) the following tasks were completed:
1) Read in the ACW Data using the CSV library.
2) As a CSV file is an entirely flat file structure, converted the data back into its rich structure. Converted all flat structures into nested structures. These are notably:
  a. Vehicle - consisting of make, model, year, and type
  b. Credit Card - consisting of start date, end date, number, security code, and IBAN.
  c. Address - consisting of the main address, city, and postcode.
  The CSV headers were inspected to see which data columns may correspond to the above. Also, ensured that the values read in are appropriately cast to their     respective types.
3) Resolved difficulty with errors in the dependants column as some entries are empty (i.e. “ “ or “”), these hindered conversion from Task 2. These were         changed into something meaningful by generating random numbers between 0 & 5 and replaced the empty values. Additionally, converted string data type values    in the dependents column to Integer. Finally, a list where all such error corrections took place were printed.
4) Wrote all records to a processed.json file in the JSON data format. This is a list of dictionaries, where each index of the list is a dictionary               representing a singular person.
5) Created two additional file outputs, retired.json and employed.json, these contained all retired customers (as indicated by the retired field in the CSV),     and all employed customers respectively (as indicated by the employer field in the CSV) in the JSON data format.
6) Wrote a function that accepts a single row from the CSV data to create a seperate file that contains any customers that have more than 10 years between        their start and end date need writing to a separate file, the file is called remove_ccard.json, in the JSON data format.
7) Calculated some additional metrics which was used for ranking customers. Created a new data attribute for the customers called “Salary-Commute”. Reading in from processed.json (file created in task 4):
  a. Added and calculated appropriately, this new attribute that represented the Salary that a customer earns, per mile of their commute.
    i. Note: If a person travels 1 or fewer commute miles, then their salary-commute would be just their salary.
  b. Sorted these records by the new metric, in ascending order.
  c. Stored the output file out as a JSON format, for a commute.json file.

Data Visualisation
To understand the data on the customers a bit more by use of visualisations, Pandas and Seaborn were utilized. With use of Pandas and Seaborn, the original CSV file initially provided were read in and the tasks below were completed:
1) Obtained the Data Series for Salary, and Age, and calculated the following:
  a. Mean Salary
  b. Median Age
2) Performed univariate plots of the following data attributes:
  a. Age, calculating how many bins would be required for a bin_width of 5.
  b. Dependents, fixing data errors with seaborn itself.
  c. Age (of default bins), conditioned on Marital Status
3. Performed multivariate plots with the following data attributes:
  a. Commuted distance against salary.
  b. Age against Salary
  c. Age against Salary conditioned by Dependants
4. Created a function to save all the plots produced.
