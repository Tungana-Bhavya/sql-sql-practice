# sql-sql-practice
-----Queries-----
---------Easy level-------
--------------------------
1. Show first name, last name, and gender of patients whose gender is 'M'

---SELECT FIRST_NAME,LAST_NAME,GENDER FROM PATIENTS WHERE GENDER='M';

3. Show first name of patients that start with the letter 'C'

---SELECT FIRST_NAME FROM PATIENTS WHERE FIRST_NAME LIKE 'C%';

5. Show first name and last name of patients who does not have allergies. (null)

---SELECT FIRST_NAME,LAST_NAME FROM PATIENTS WHERE ALLERGIES IS NULL; 

6. Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)

---SELECT FIRST_NAME,LAST_NAME FROM PATIENTS WHERE WEIGHT BETWEEN 100 AND 120;

7. Show first name and last name concatinated into one column to show their full name.

---SELECT CONCAT(FIRST_NAME,' ',LAST_NAME) AS FULL_NAME FROM PATIENTS;
   
8. Show first name, last name, and the full province name of each patient.

---SELECT P.FIRST_NAME,P.LAST_NAME,P1.PROVINCE_NAME FROM PATIENTS P 
   LEFT JOIN PROVINCE_NAMES P1 ON P.PROVINCE_ID=P1.PROVINCE_ID;
   
9. Show how many patients have a birth_date with 2010 as the birth year.

---SELECT COUNT(*) FROM PATIENTS WHERE YEAR(BIRTH_DATE)=2010; 

10. Show the first_name, last_name, and height of the patient with the greatest height.

---SELECT FIRST_NAME,LAST_NAME,MAX(HEIGHT) FROM PATIENTS; 




