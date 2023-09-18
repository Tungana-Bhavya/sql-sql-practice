### sql-sql-practice
The goal of this repository is to help professionals and students who want to improve and grow their SQL knowledge for their professions. the following questions were 
collected from the website  https://www.sql-practice.com/ . Based on the complexity there are three sections as given below:  

1. Easy level
2. Medium level
3. Difficult level

#### Easy level(1-17)
----------------------------
1. Show first name, last name, and gender of patients whose gender is 'M'

---SELECT FIRST_NAME,LAST_NAME,GENDER FROM PATIENTS WHERE GENDER='M';

-----

2. Show first name of patients that start with the letter 'C'

---SELECT FIRST_NAME FROM PATIENTS WHERE FIRST_NAME LIKE 'C%';

-----

4. Show first name and last name of patients who does not have allergies. (null)

---SELECT FIRST_NAME,LAST_NAME FROM PATIENTS WHERE ALLERGIES IS NULL; 

-----

4. Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)

---SELECT FIRST_NAME,LAST_NAME FROM PATIENTS WHERE WEIGHT BETWEEN 100 AND 120;

-----

5. Show first name and last name concatinated into one column to show their full name.

---SELECT CONCAT(FIRST_NAME,' ',LAST_NAME) AS FULL_NAME FROM PATIENTS;

-----
   
6. Show first name, last name, and the full province name of each patient.

---SELECT P.FIRST_NAME,P.LAST_NAME,P1.PROVINCE_NAME FROM PATIENTS P 
   LEFT JOIN PROVINCE_NAMES P1 ON P.PROVINCE_ID=P1.PROVINCE_ID;

-----
   
7. Show how many patients have a birth_date with 2010 as the birth year.

---SELECT COUNT(*) FROM PATIENTS WHERE YEAR(BIRTH_DATE)=2010; 

-----

8. Show the first_name, last_name, and height of the patient with the greatest height.

---SELECT FIRST_NAME,LAST_NAME,MAX(HEIGHT) FROM PATIENTS; 

-----

9. Show the patient id and the total number of admissions for patient_id 579.

---SELECT PATIENT_ID,COUNT(*)AS TOTAL_ADMISSIONS FROM ADMISSIONS WHERE PATIENT_ID LIKE 579;

-----

10. Show all columns for patients who have one of the following patient_ids:
    1,45,534,879,1000

---SELECT * FROM PATIENTS WHERE PATIENT_ID IN(1,45,534,879,1000);

-----

11. Based on the cities that our patients live in, show unique cities that are in province_id 'NS'?

--SELECT DISTINCT(CITY)AS UNIQUE_CITIES FROM PATIENTS WHERE PROVINCE_ID IS 'NS';

-----

12. Update the patients table for the allergies column. If the patient's allergies is null then replace it with 'NKA'

---UPDATE PATIENTS SET ALLERGIES='NKA' WHERE ALLERGIES IS NULL;

-----

13. Show the total number of admissions

---SELECT COUNT(PATIENT_ID) AS TOTAL_ADMISSIONS FROM ADMISSIONS;

-----

14. Write a query to find list of patients first_name, last_name, and allergies from Hamilton where allergies are not null

---SELECT FIRST_NAME,LAST_NAME,ALLERGIES FROM PATIENTS WHERE CITY='Hamilton' AND ALLERGIES IS NOT NULL;

-----

15. Show all the columns from admissions where the patient was admitted and discharged on the same day.

---SELECT * FROM ADMISSIONS WHERE ADMISSION_DATE=DISCHARGE_DATE;

-----

16. Write a query to find the first_name, last name and birth date of patients who has height greater than 160 and weight greater than 70

---SELECT FIRST_NAME,LAST_NAME,BIRTH_DATE FROM PATIENTS WHERE HEIGHT>160 AND WEIGHT>70;

-----

17. Based on cities where our patient lives in, write a query to display the list of unique city starting with a vowel (a, e, i, o, u). Show the result order in ascending by city.

---SELECT DISTINCT(CITY) FROM PATIENTS WHERE CITY LIKE 'A%' OR  CITY LIKE 'E%' OR  CITY LIKE 'I%' OR  CITY LIKE 'O%' OR  CITY LIKE 'U%' ORDER BY CITY ASC; 
---SELECT DISTINCT CITY FROM STATION WHERE CITY REGEXP '^[aeiou]';

-----
#### Medium level(18-)
------------------------------
18. Show unique birth years from patients and order them by ascending.

---SELECT DISTINCT(YEAR(BIRTH_DATE))AS BIRTH_YEAR from PATIENTS ORDER BY BIRTH_YEAR ASC;

-----

19. Show unique first names from the patients table which only occurs once in the list.

---SELECT DISTINCT(FIRST_NAME) FROM PATIENTS GROUP BY FIRST_NAME HAVING COUNT(FIRST_NAME)=1;

-----

20. Show patient_id and first_name from patients where their first_name start and ends with 's' and is at least 6 characters long.

---SELECT PATIENT_ID,FIRST_NAME FROM PATIENTS WHERE FIRST_NAME LIKE 'S%S'AND LENGTH(FIRST_NAME)>=6; 

-----

21. Show patient_id, first_name, last_name from patients whos diagnosis is 'Dementia'.

---SELECT P.PATIENT_ID,P.FIRST_NAME,P.LAST_NAME FROM PATIENTS P 
   JOIN ADMISSIONS A ON P.PATIENT_ID=A.PATIENT_ID WHERE A.DIAGNOSIS='Dementia';

-----

22. Display every patient's first_name. Order the list by the length of each name and then by alphbetically

---SELECT FIRST_NAME FROM PATIENTS ORDER BY LENGTH(FIRST_NAME),FIRST_NAME;

-----

23. Show the total amount of male patients and the total amount of female patients in the patients table.
    Display the two results in the same row

---SELECT SUM(GENDER ='M') AS MALE_COUNT,SUM(GENDER='F') AS FEMALE_COUNT FROM PATIENTS;

-----

24. Show first and last name, allergies from patients which have allergies to either 'Penicillin' or 'Morphine'. Show results ordered ascending by allergies then by first_name then by 
    last_name.

---SELECT FIRST_NAME,LAST_NAME,ALLERGIES FROM PATIENTS WHERE ALLERGIES IN('Penicillin','Morphine')ORDER BY ALLERGIES,FIRST_NAME,LAST_NAME;

------

25. Show the city and the total number of patients in the city.Order from most to least patients and then by city name ascending.

---select CITY,COUNT(*)AS NUM_PATIENTS FROM PATIENTS GROUP BY CITY ORDER BY NUM_PATIENTS DESC, CITY ASC;

-----

26. display the number of duplicate patients based on their first_name and last_name.

---SELECT FIRST_NAME,LAST_NAME,COUNT(*) AS NUM_OF_DUPLICATES FROM PATIENTS GROUP BY FIRST_NAME,LAST_NAME HAVING COUNT(*)>1;

-----

27. Show first name, last name and role of every person that is either patient or doctor.
    The roles are either "Patient" or "Doctor"

---SELECT FIRST_NAME,LAST_NAME,'PATIENT' AS ROLE FROM PATIENTS UNION ALL
   SELECT FIRST_NAME,LAST_NAME,'DOCTOR' AS ROLE FROM DOCTORS;

 -----

28. Show all allergies ordered by popularity. Remove NULL values from query.

---SELECT ALLERGIES,COUNT(*) AS TOTAL_DIAGNOSIS FROM PATIENT WHERE ALLERGIES IS NOT NULL
   GROUP BY ALLERGIES ORDER BY TOTAL_DIAGNOSIS DESC;

-----

29. Show all patient's first_name, last_name, and birth_date who were born in the 1970s decade. Sort the list starting from the earliest birth_date.

---SELECT FIRST_NAME,LAST_NAME,BIRTH_DATE FROM PATIENTS WHERE BIRTH_DATE  LIKE '197%' ORDER BY BIRTH_DATE ASC;

-----

30. Show the difference between the largest weight and smallest weight for patients with the last name 'Maroni'

---SELECT MAX(WEIGHT)-MIN(WEIGHT) FROM PATIENTS WHERE LAST_NAME='Maroni';

-----

31. Show patient_id, diagnosis from admissions. Find patients admitted multiple times for the same diagnosis.

---SELECT PATIENT_ID, DIAGNOSIS FROM ADMISSIONS GROUP BY PATIENT_ID,DIAGNOSIS HAVING COUNT(PATIENT_ID)>1;

-----

32. We want to display each patient's full name in a single column. Their last_name in all upper letters must appear first, then first_name in 
    all lower case letters. Separate the last_name and first_name with a comma. Order the list by the first_name in decending order

---SELECT CONCAT(UPPER(LAST_NAME),',',LOWER(FIRST_NAME))AS NEW_NAME_FORMAT FROM PATIENTS ORDER BY FIRST_NAME DESC;

-----

33. Show the province_id(s), sum of height; where the total sum of its patient's height is greater than or equal to 7,000.

---SELECT PROVINCE_ID, SUM(HEIGHT)AS SUM_HEIGHT FROM PATIENTS GROUP BY PROVINCE_ID HAVING SUM_HEIGHT>=7000;

-----

34. Show all columns for patient_id 542's most recent admission_date.

---SELECT * FROM ADMISSIONS WHERE PATIENT_ID=542 GROUP BY PATIENT_ID HAVING MAX(ADMISSION_DATE);

-----

35. Show patient_id, first_name, last_name from patients whose does not have any records in the admissions table. (Their patient_id does not 
    exist in any admissions.patient_id rows.)

---SELECT PATIENTS.PATIENT_ID,FIRST_NAME,LAST_NAME from PATIENTS LEFT JOIN ADMISSIONS ON PATIENTS.PATIENT_ID=ADMISSIONS.PATIENT_ID WHERE 
   ADMISSIONS.PATIENT_ID IS NULL;

-----

36. For each doctor, display their id, full name, and the first and last admission date they attended.

---SELECT DOCTOR_ID,CONCAT(FIRST_NAME,' ',LAST_NAME),MIN(ADMISSION_DATE)AS LAST_DATE,MAX(ADMISSION_DATE)AS FIRST_DATE FROM ADMISSIONS JOIN 
   DOCTORS ON ADMISSIONS.ATTENDING_DOCTOR_ID=DOCTORS.DOCTOR_ID GROUP BY DOCTOR_ID;

-----

37. For every admission, display the patient's full name, their admission diagnosis, and their doctor's full name who diagnosed their problem.

---SELECT CONCAT(P.FIRST_NAME,' ',P.LAST_NAME)AS PATIENT_NAME,A.DIAGNOSIS,CONCAT(D.FIRST_NAME,' ',D.LAST_NAME)AS DOCTOR_NAME FROM PATIENTS P 
   JOIN ADMISSIONS A JOIN DOCTORS D ON P.PATIENT_ID=A.PATIENT_ID ANDA.ATTENDING_DOCTOR_ID=D.DOCTOR_ID;

-----

38. Display the total amount of patients for each province. Order by descending.

---SELECT PROVINCE_NAME,COUNT(*)AS PATIENT_COUNT FROM PROVINCE_NAMES JOIN PATIENTS ON PROVINCE_NAMES.PROVINCE_ID=PATIENTS.PROVINCE_ID 
   GROUP BY PROVINCE_NAMES.PROVINCE_ID ORDER BY PATIENT_COUNT DESC;

-----

39. Show first_name, last_name, and the total number of admissions attended for each doctor.Every admission has been attended by a doctor

---SELECT D.FIRST_NAME,D.LAST_NAME,COUNT(*) AS ADMISSIONS_TOTAL FROM DOCTORS D JOIN ADMISSIONS A ON D.DOCTOR_ID=A.ATTENDING_DOCTOR_ID GROUP BY 
   ATTENDING_DOCTOR_ID;

-----

40. Show patient_id, attending_doctor_id, and diagnosis for admissions that match one of the two criteria:
    1. patient_id is an odd number and attending_doctor_id is either 1, 5, or 19.
    2. attending_doctor_id contains a 2 and the length of patient_id is 3 characters.

---SELECT PATIENT_ID,ATTENDING_DOCTOR_ID,DIAGNOSIS FROM ADMISSIONS WHERE PATIENT_ID % 2=1 AND 
ATTENDING_DOCTOR_ID IN (1,5,19) OR ATTENDING_DOCTOR_ID LIKE '%2%' AND LENGTH(PATIENT_ID)=3;

-----

41. Show all of the days of the month (1-31) and how many admission_dates occurred on that day. Sort by the day with most admissions to least 
    admissions.

---SELECT DAY(ADMISSION_DATE)AS DAY_NUMBER,COUNT(*) AS NUMBER_OF_ADMISSIONS FROM ADMISSIONS GROUP BY DAY_NUMBER ORDER BY 
   NUMBER_OF_ADMISSIONS DESC;

-----

42. Display patient's full name, height in the units feet rounded to 1 decimal, weight in the unit pounds rounded to 0 decimals, birth_date,
    gender non abbreviated.
    Convert CM to feet by dividing by 30.48.
    Convert KG to pounds by multiplying by 2.205.

---SELECT CONCAT(FIRST_NAME,' ',LAST_NAME) AS 'PATIENT_NAME',ROUND(HEIGHT/30.48,1)AS 'HEIGHT "FEET"',ROUND(WEIGHT/2.205,0)AS 'WEIGHT 
   "POUNDS"',BIRTH_DATE, CASE WHEN GENDER ='M' THEN 'MALE' ELSE 'FEMALE' END AS "GENDER" FROM PATIENTS;

   -----

   #### Difficult level(43-54)
43. Show patient_id, first_name, last_name, and attending doctor's specialty.
    Show only the patients who has a diagnosis as 'Epilepsy' and the doctor's first name is 'Lisa'
    Check patients, admissions, and doctors tables for required information.

---SELECT
  P.PATIENT_ID,
  P.FIRST_NAME AS PATIENT_FIRST_NAME,
  P.LAST_NAME AS PATIENT_LAST_NAME,
  D.SPECIALTY AS ATTENDING_DOCTOR_SPECIALTY
  FROM PATIENTS P
  JOIN ADMISSIONS A ON A.PATIENT_ID = P.PATIENT_ID
  JOIN DOCTORS D ON D.DOCTOR_ID = A.ATTENDING_DOCTOR_ID
  WHERE
  D.FIRST_NAME = 'Lisa' and
  A.DIAGNOSIS = 'Epilepsy';
  
  -----




    


















