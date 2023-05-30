architecture link - https://drive.google.com/file/d/1Fwz-YCtylrlNX9mFgW50U_DNBrFnt04Z/view?usp=sharing

In this what i did was

1) Imported youtube dataset from kaggle
2) uploaded those 2 data files ( category and youtube video data) folders into s3 bucket ( raw)
3) transform the category json to parquet with only items in it - in lambda function
4) now add the trigger functionality to that lamabda function 
5) in trigger you have to make for s3 with full operation - (means whenever any files will land on the raw bucket this lambda function will start)
6) this lambda function will save the parquet files to cleansed bucket
7) you can check the the table in the athena
note before running that code the database you mention in the lambda function environment variable should be their in the funtion

8) afterwords check the schema of the table in the database if any datatyype mismatch change that from there

9) now delete the data from raw bucket and reuploaded it will trigger the function and run the code the output will be save in cleansed s3

10) afterwoards we can use the clean category data and raw youtube files but that youtube files will contain differnt langues for that we need to change it to utf-8

Note but for this we will not change this to utf-8 we just remove the countries and process that data

11) now we have to write the code for the transforming of the data in etl glue and then the result will save in cleansed s3

12)afterwords we have to create the crawler for that cleansed youtube data for crawl the catalouge 

13) now we can queary the data from the athena 

14) but for processing we will create a new table ( because when we use same join statement multiple time this will waste time )
insted of that we will create intermidiate table from it and save it to new bucket called analytics bucket
15) afterwards we create crawler on that bucket and can queary the data in it

now our queary tech part is done just need to connect this servies with the quicksight (standerd) and see the insight of the data