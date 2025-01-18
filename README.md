# AWK-Command

- AWK is a powerful scripting language and command-line tool used for text processing and data extraction in Unix/Linux environments. Columns contents are fields for awk. awk will scan each line in file and give us required output.
- Inside curly braces we state actions to be performed and provide pattern/condition outside.

_**Terms used in awk**_

- NR :- no or rows/record
- NF :- no of fields
- $0 :- print everything
- $1, $2 :- field no

- The file on which the awk command operations are performed looks like below:-

![image](https://github.com/user-attachments/assets/f5110e68-a8c7-41f7-9af4-3febf96cb247)

*1. Print only a given column*
- Command :- awk '{print $4}' data.sh

![image](https://github.com/user-attachments/assets/76e862c5-c2e3-4ff2-b43e-21b289662981)

*2. Print multiple columns at a time*
- Command :- awk '{print $4, $2}' data.sh
- Data gets loaded in the sequence of columns no's given

![image](https://github.com/user-attachments/assets/0fa4da0e-22a1-4e53-bcab-19f0d612a995)

*3. Print last column*
- Command :- awk '{print $NF}' data.sh
- Use "NF" for last column (No of fields)

![image](https://github.com/user-attachments/assets/77708eb3-30ce-4a51-b479-772b593f0d47)

*4. Print all the content*
- Command :- awk '{print $0}' data.sh

![image](https://github.com/user-attachments/assets/bb6eaada-3828-4eb6-957f-274836ad5d6c)

*5. Print Specific Line (line containing specific word)*
- Command :- awk '/Nyssa/{print $0}' data.sh
- We can also use "grep" command for the same

![image](https://github.com/user-attachments/assets/696c48b1-25c4-47de-81f1-d135b6e88a4c)

*6. Print line no at start of each line*
- Command :- awk '{print NR, $0}' data.sh
- Use NR (No of rows) attribute, also known as record no

![image](https://github.com/user-attachments/assets/cebcd175-d367-454d-9b2b-5338562a29ee)

*7. Print line no containing required user*
- Command :- awk '/Nyssa/{print NR, $0}' data.sh

![image](https://github.com/user-attachments/assets/a9532801-6b74-46f5-8860-61e613c2533e)

*8. Print only given line no*
- Command :- awk 'NR==6 {print $0}' data.sh

![image](https://github.com/user-attachments/assets/bf634043-fec5-40e4-a24a-63c769847acd)

*9. Print range of lines*
- Command :- awk 'NR==3,NR==6 {print NR, $0}' data.sh

![image](https://github.com/user-attachments/assets/44cbc26f-90d4-4b14-ae79-8fafa1694336)

*10. Print line no of empty lines*
- Command :- awk 'NF==0 {print NR}' data.sh
- NF==0 means give lines which have zero no of fields present

![image](https://github.com/user-attachments/assets/0f0d7e94-b78d-4608-bfcc-be2842666970)

*11. Search multiple words*
- Command :- awk '/Alisha|Renae/ {print $0}' data.sh
- print $0 to print all fields in that line containing given words

![image](https://github.com/user-attachments/assets/b46aae69-443c-4097-910f-1022d5654d29)

*12. Check if given character is present in column*
- Command :- awk '$2 ~ /a/ {print $0}' data.txt
- Lets say we've to take data from 2nd column which have "a" in it

![image](https://github.com/user-attachments/assets/132ace2f-2baa-4bde-8850-b498a82714e1)

----------------------------------------------------------------------------------------------------------------------------------------------

_**Working with CSV or different delimeter**_

Below is the example of CSV file

![image](https://github.com/user-attachments/assets/fd33e788-0ed6-4f7d-ba29-af3b197a32c4)


*1. How to work with CSV File*
- Command :-  awk -F, '{print $2}' emp.csv
- Here we have to pass -F for all fields and , so that awk understands all fields are separated by commas

![image](https://github.com/user-attachments/assets/52642876-c41b-4c52-abe3-cfe9f8e04b8b)

*2. Print data of employees whose salary is more than 50000*
- Command :- awk -F, '$NF>50000 {print $0}' emp.csv
- $NF is for the no of fields

![image](https://github.com/user-attachments/assets/b8bfd7b2-0554-4223-8794-9d2cfa2d460c)

*3. File with multiple delimeter*
- Below is the example of file with multi-delimeters like space, comma, colon,etc

![image](https://github.com/user-attachments/assets/ec56589e-e081-4781-ac7f-0324461e39ed)

- For field separator, always provide -F and then delimeters. Here how many delimeters we provide inside [] the file will get divided in those many parts and we can print the output accordingly column wise giving column numbers. Even if we miss any delimeter in file, the command will take the input accordingly.
- Command :- awk -F[,:.:-] '{print $4, $2, $3, $1}' multiple_delimeter.txt

 ![image](https://github.com/user-attachments/assets/1a68dedf-67e9-4ab3-a91f-0eba8a37ec4b)'

 ----------------------------------------------------------------------------------------------------------------------------------------------

_**Use cases of awk in Linux System**_

1. To get list of files
- Command :- ls -lrt | awk '{print $9}'

![image](https://github.com/user-attachments/assets/c3c78bc0-1184-4d59-80bf-7ecc6e048ef3)

- If we don't want the blank line at start or any other line, we can state that in command i.e. exclude the line
- Command :- ls -lrt | awk 'NR>1 {print $NF}'   #Instead of NF we can also give columnn no.

![image](https://github.com/user-attachments/assets/aaaaf49b-010a-44db-b30c-d2e771386a21)

2. To read logs in given range of time frame
- Command :- less /var/logs/messages | awk '$3>="1:00:00" && $3>="1:00:00"'    #3 is column no where the time is
- If we have to take logs from 1.00.00 to 1.00.01, use above command specifying the file name.

3. List the files modified in specific month
- Command :- ls -lrt | awk '$6==Oct'

4. To replace a word
- Command :- awk '{gsub("Kore","Shubham); print $0}' data.txt
- "gsub" means "Global Substitute" to replace some word by new word and then we can print the whole file using $0 or customize the columns as required

![image](https://github.com/user-attachments/assets/28ddc41b-240a-4c8b-a645-9df77fce86de)

5. Find length of line/field
- Lets print no of characters in specific column (name). Here "length" function is used.
- Command :- awk '{print length($2)}' data.txt

![image](https://github.com/user-attachments/assets/b326959f-1e5f-4d62-a7e4-db14866c9ea9)
![image](https://github.com/user-attachments/assets/56aa984e-3b74-4bb9-9675-f5881a72da3a)


6. Check index/position of word in line
- Here we can use "index" function

7. Print values in upper or lower case
- Command :- awk '{print toupper($2)}' data.txt

![image](https://github.com/user-attachments/assets/0267d58e-8027-4ca5-be79-318d074466e9)

----------------------------------------------------------------------------------------------------------------------------------------------

_**Awk Scripting Concepts**_

1. Use of Begin and End
- We can give condition on how to begin and end the awk using this
- Command :- awk 'BEGIN{print "----Employee Data----"} {print $0} END{print "----Ending the Table----"}' data.txt

![image](https://github.com/user-attachments/assets/f8e2c8f5-948d-4adf-9f00-9555cb0c60c4)

2.  To find total of salary of all employees in table
- Command :- awk 'BEGIN{sum=0} {sum=sum+$NF} END{print "Sum of salary" : sum}' emp.csv

![image](https://github.com/user-attachments/assets/6cf2506e-952e-4295-872a-8ac1d447f159)

3. To ignore headers/first row to count no. of users
- Command :- awk 'NR>1 {count++} END{print "Total employees are : ", count}' emp.csv

![image](https://github.com/user-attachments/assets/fa5dc04b-bc54-4f80-825e-8f3f5bdfc7c3)

4. To find average salary
- Command :- awk -F, '{count++; sum=sum+$NF} END{print "Average Salary: " sum/count}' emp.csv

![image](https://github.com/user-attachments/assets/1cc9e6e1-b207-4c48-982b-2ba2353fc0b3)

5. To get length of longest line
- length variable is used to find length as we know
- The command will check length of each line and then using "max" variable it will check if the subsequent line's length is more than first, if yes it will print the longest line length.
- Command :- awk '{if(length($0)>max)max=length($0)} END{print "Length of longest line is " max}' emp.csv

![image](https://github.com/user-attachments/assets/82df578a-7b72-4624-abd2-61290f07e3a9)

6. If -else condition for salary
- Lets print high for salary more than 50k else print low
- Command :- awk -F, '{if($NF>50000)$7="High"; else $7="Low"; print $0}' emp.csv

![Uploading image.png…]()




