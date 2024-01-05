#1. Create the database schema named health_care_management.
CREATE SCHEMA health_care_management;

#2. Now we need to create the required table
create table hospital_staffing
(
    `Sr.No`                                   int          not null
        primary key,
    Year                                      int          not null,
    Facility_number                           int          not null,
    Facility_name                             varchar(200) null,
    Begin_date                                text         null,
    End_date                                  text         null,
    Country_name                              varchar(45)  null,
    Type_of_control                           varchar(45)  null,
    Hours_type                                varchar(100) null,
    Productive_hours                          int          null,
    Productive_hours_per_adjusted_patient_day int          null
);

#3. Now we need to find the some details about the table we have uploaded.
DESCRIBE TABLE hospital_staffing;

#4. Counting Of the number of rows
SELECT COUNT(*) FROM hospital_staffing;

#5. Counting Of the number of Columns
SELECT COUNT(*) AS Column_numbers FROM
    information_schema.columns
WHERE TABLE_NAME = "hospital_staffing";

#6. Finding the distinct year from the table.
SELECT DISTINCT Year FROM hospital_staffing;

#7. Finding the number of hours types.
SELECT DISTINCT hours_type FROM hospital_staffing;

#8. FInding the distinct country type of control.
SELECT DISTINCT Type_of_control FROM hospital_staffing;

#9. Finding the distinct country name from the table.
SELECT DISTINCT Country_name FROM hospital_staffing;

#10. Finding the number of distinct country name.
SELECT COUNT(DISTINCT Country_name) AS Country_Count FROM hospital_staffing;

#11. Finding the distinct facility name.
SELECT DISTINCT Facility_name FROM hospital_staffing;

#12. Now we are going to find the number of distinct facility name.
SELECT COUNT(DISTINCT Facility_name) AS Facility_Count FROM hospital_staffing;

#13. Now we are finding the average of the Total productive hours per adjusted patient date
SELECT AVG(Productive_hours_per_adjusted_patient_day) FROM hospital_staffing;

#14. Finding Minimum value in the table
SELECT MIN(Productive_hours_per_adjusted_patient_day) FROM hospital_staffing;

#15. Finding the maximum value in the table
SELECT MAX(Productive_hours_per_adjusted_patient_day) FROM hospital_staffing;

#16. Finding all the columns of the maximum value of Productive hours per adjusted patient day using sub-query
SELECT *
    FROM hospital_staffing
    WHERE Productive_hours_per_adjusted_patient_day IN
        (
    SELECT MAX(Productive_hours_per_adjusted_patient_day
        ) FROM hospital_staffing);

#17. Finding all the columns for maximum value of the productive hours
SELECT *
    FROM hospital_staffing
    WHERE Productive_hours IN
          (
          SELECT MAX(Productive_hours
          ) FROM hospital_staffing);
#18. Making the table whose rows contains the minimum value of Productive hours per sdjusted patient day.
SELECT *
    FROM hospital_staffing
    WHERE Productive_hours_per_adjusted_patient_day IN
          (
          SELECT MIN(Productive_hours_per_adjusted_patient_day
          ) FROM hospital_staffing);


#19. We are going to find the total productive hours and total productive hours per adjusted day by grouping the table according to Type of control
SELECT Type_of_control, SUM(Productive_hours) AS Total_productive_hours, SUM(Productive_hours_per_adjusted_patient_day) AS Total_productive_hours_per_adjusted_patient_day
	FROM hospital_staffing
    GROUP BY Type_of_control;


#20. Here we have found the maximum productive hours after grouping by facility name 
SELECT MAX(x.total_Productive_hours)
    FROM
        (SELECT Facility_name, Year, SUM(Productive_hours) AS total_Productive_hours,
                SUM(Productive_hours_per_adjusted_patient_day) AS Total_Productive_hours_per_adjusted_patient_day
        FROM hospital_staffing
    WHERE Year = 2009
    GROUP BY Facility_name) x;


#20. Here we are finding the maximum productive hours from the table in the year 2009.
SELECT * FROM (SELECT Facility_name, Year, SUM(Productive_hours) AS total_Productive_hours,
                SUM(Productive_hours_per_adjusted_patient_day) AS Total_Productive_hours_per_adjusted_patient_day
        FROM hospital_staffing
    WHERE Year = 2009
    GROUP BY Facility_name) x
WHERE x.total_Productive_hours IN (SELECT MAX(Total_Productive_hours) FROM (SELECT Facility_name, Year, SUM(Productive_hours) AS total_Productive_hours,
                SUM(Productive_hours_per_adjusted_patient_day) AS Total_Productive_hours_per_adjusted_patient_day
        FROM hospital_staffing
    WHERE Year = 2009
    GROUP BY Facility_name) y);


#21. Here we have found which facility has the maximum productive hours
SELECT * FROM (SELECT Facility_name, SUM(Productive_hours) AS total_Productive_hours,
                SUM(Productive_hours_per_adjusted_patient_day) AS Total_Productive_hours_per_adjusted_patient_day
        FROM hospital_staffing
    GROUP BY Facility_name) x
WHERE x.total_Productive_hours IN (SELECT MAX(Total_Productive_hours) FROM (SELECT Facility_name, SUM(Productive_hours) AS total_Productive_hours,
                SUM(Productive_hours_per_adjusted_patient_day) AS Total_Productive_hours_per_adjusted_patient_day
        FROM hospital_staffing
    GROUP BY Facility_name) y);


#22. Here We have found that which year is the most productive year
SELECT * FROM (SELECT Year, SUM(Productive_hours) AS Total_Productive_hours
               FROM
             hospital_staffing
        GROUP BY Year) x
WHERE x.Total_Productive_hours IN (
SELECT MAX(Total_Productive_hours) FROM (SELECT Year, SUM(Productive_hours) AS Total_Productive_hours
               FROM
             hospital_staffing
        GROUP BY Year) x);



#23. Finding the productive hours per adjusted patient date greater than the average productive hours per adjusted patient date.
SELECT * FROM
             hospital_staffing
        WHERE Productive_hours_per_adjusted_patient_day > (
        SELECT AVG(Productive_hours_per_adjusted_patient_day) FROM hospital_staffing
        )
ORDER BY Productive_hours_per_adjusted_patient_day DESC
LIMIT 10;


#24. Total productive hours grouped by hours type.
SELECT Hours_type, SUM(Productive_hours) AS Total_productive_hours,
                    SUM(Productive_hours_per_adjusted_patient_day) AS Total_productive_hours_per_adjusted_patient_day
        FROM
             hospital_staffing
        WHERE Productive_hours_per_adjusted_patient_day
        GROUP BY Hours_type
ORDER BY SUM(Productive_hours_per_adjusted_patient_day) DESC;


#25. Here we are finding the total productive hours which are greater than average productive hours.
SELECT Hours_type, SUM(Productive_hours) AS Total_productive_hours,
                    SUM(Productive_hours_per_adjusted_patient_day) AS Total_productive_hours_per_adjusted_patient_day
        FROM
             hospital_staffing
        WHERE Productive_hours_per_adjusted_patient_day > (
        SELECT AVG(Productive_hours_per_adjusted_patient_day) FROM hospital_staffing
        )
        GROUP BY Hours_type
ORDER BY SUM(Productive_hours_per_adjusted_patient_day) DESC;


#26. Now we want to know about which facility and which Hours type is doing great in terma of productive hours
SELECT Facility_name, Hours_type, SUM(Productive_hours) AS Total_productive_hours,
                        SUM(Productive_hours_per_adjusted_patient_day) AS Total_productive_hours_per_adjusted_patient_day
FROM hospital_staffing
GROUP BY Facility_name, Hours_type
ORDER BY SUM(Productive_hours) DESC
LIMIT 20;


#27. Here we have found the total productive hours per adjusted day for the Registered nurse only and ordered them by descending order. 
SELECT Facility_name, Hours_type, SUM(Productive_hours) AS Total_productive_hours,
                        SUM(Productive_hours_per_adjusted_patient_day) AS Total_productive_hours_per_adjusted_patient_day
FROM hospital_staffing
WHERE Hours_type IN (SELECT Hours_type FROM hospital_staffing
						WHERE Hours_type = "Registered Nurse"
					 )
GROUP BY Facility_name
ORDER BY SUM(Productive_hours) DESC
LIMIT 20;




#28. We are grouping the table by using group by function and adding the sum of the total productive hours and total productive hours per adjusted patient day
SELECT Type_of_control, SUM(Productive_hours) AS Total_productive_hours, SUM(Productive_hours_per_adjusted_patient_day) AS Total_productive_hours_per_adjusted_patient_day
	FROM hospital_staffing
    GROUP BY Type_of_control 
    HAVING Type_of_control IN (
									SELECT Type_of_control FROM hospital_staffing
                                    WHERE Type_of_control IN ("Non-Profit", "District")
								);
