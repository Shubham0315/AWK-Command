# AWK-Command

- AWK is a powerful scripting language and command-line tool used for text processing and data extraction in Unix/Linux environments. Columns contents are fields for awk. awk will scan each line in file and give us required output.
- Inside curly braces we state actions to be performed and provide pattern/condition outside.

**Terms used in awk**

- NR :- no or rows/record
- NF :- no of fields
- $0 :- print everything
- $1, $2 :- field no

- The file on which the awk command operations are performed looks like below:-

- ![image](https://github.com/user-attachments/assets/f5110e68-a8c7-41f7-9af4-3febf96cb247)

_1. Print only a given column_
- Command :- awk '{print $4}' data.sh

- ![image](https://github.com/user-attachments/assets/76e862c5-c2e3-4ff2-b43e-21b289662981)

2. Print multiple columns at a time
- Command :- awk '{print $4, $2}' data.sh
- Data gets loaded in the sequence of columns no's given

- ![image](https://github.com/user-attachments/assets/0fa4da0e-22a1-4e53-bcab-19f0d612a995)

3. Print last column
- Command :- awk '{print $NF}' data.sh
- Use "NF" for last column (No of fields)

- ![image](https://github.com/user-attachments/assets/77708eb3-30ce-4a51-b479-772b593f0d47)

4. Print all the content
- Command :- awk '{print $0}' data.sh

- ![image](https://github.com/user-attachments/assets/bb6eaada-3828-4eb6-957f-274836ad5d6c)

5. Print Specific Line (line containing specific word)
- Command :- awk '/Nyssa/{print $0}' data.sh
- We can also use "grep" command for the same

- ![image](https://github.com/user-attachments/assets/696c48b1-25c4-47de-81f1-d135b6e88a4c)

6. Print line no at start of each line
- Command :- awk '{print NR, $0}' data.sh
- Use NR (No of rows) attribute, also known as record no

- ![image](https://github.com/user-attachments/assets/cebcd175-d367-454d-9b2b-5338562a29ee)

7. Print line no containing required user
- Command :- awk '/Nyssa/{print NR, $0}' data.sh

- ![image](https://github.com/user-attachments/assets/a9532801-6b74-46f5-8860-61e613c2533e)

8. Print only given line no
- Command :- awk 'NR==6 {print $0}' data.sh

- ![image](https://github.com/user-attachments/assets/bf634043-fec5-40e4-a24a-63c769847acd)

9. Print range of lines
- Command :- awk 'NR==3,NR==6 {print NR, $0}' data.sh

- ![image](https://github.com/user-attachments/assets/44cbc26f-90d4-4b14-ae79-8fafa1694336)

10. Print line no of empty lines
- Command :- awk 'NF==0 {print NR}' data.sh
- NF==0 means give lines which have zero no of fields present

- ![image](https://github.com/user-attachments/assets/0f0d7e94-b78d-4608-bfcc-be2842666970)

11. Search multiple words
- Command :- awk '/Alisha|Renae/ {print $0}' data.sh
- print $0 to print all fields in that line containing given words

- ![image](https://github.com/user-attachments/assets/b46aae69-443c-4097-910f-1022d5654d29)

12. 





