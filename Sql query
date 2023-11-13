SELECT * FROM heart_attack_dataset;
SELECT COUNT(Patient_ID) FROM heart_attack_dataset;
#1 In this query we find patient whose family hiostory of heartattack are blank but they have risk of heartattack.
select Patient_ID,Age,Gender
	from heart_attack_dataset 
    where Age<50 and Heart_Attack_Risk=1 and Family_History=0;
    
#2 In this query we find age vs number of smokers in the world.
select count(Smoking),Age 
	from heart_attack_dataset 
    where Smoking=1 
    group by Age;
    
#3 In this query we find/assume that patient who given  time for exercise more 15 hours per week so they are fall under the safe category and others are unknown.
select Patient_ID,country, 
	case 
		when Exercise_Hours_Per_Week > 15 then 'safety' 
        end as safe 
from heart_attack_dataset;

#4 In this query we divide the treatement category according to the age and heart attack risk. 
select Patient_ID,Country,
	case
		when Age <50 and Heart_Attack_Risk=1 then 'priority' 
		when Age>50 and Heart_Attack_Risk=1 then 'hige priority' 
        else 'normal' 
	end as treatment  
from heart_attack_dataset;

#5 In this query we find the patient whose heart rate is greater than normal heart rate and group by the patient Id , country, gender and heart rate.
select Patient_ID,Gender,Heart_Rate,Country 
from heart_attack_dataset 
where exists ( 
				select * 
                from heart_attack_dataset 
                where Heart_Rate>75
);

#6 In this query we know that who are smoking about his cholesterol, blood pressure with the age and patient Id
select Patient_ID,Age,Blood_Pressure,Cholesterol
from heart_attack_dataset 
where exists ( 
				select * 
                from heart_attack_dataset 
                where smoking=1
);

#7 In this query we find number of patient from each country whose having heart risk.
select count(patient_ID),Country 
from heart_attack_dataset 
	where heart_attack_risk =1
	group by country;

#8 In this query we find number of patient from each continent whose having heart risk.
select count(patient_ID),Continent
from heart_attack_dataset 
	where heart_attack_risk =1
	group by continent;
    
#9 In this query we find the patient Id with the minimum heart rate in ascending order with the country.
select Patient_ID,Country,Heart_Rate 
from heart_attack_dataset 
where ( 
		select min(heart_rate) 
        from heart_attack_dataset) 
order by heart_rate ;

#10 In this query we the number of patient with the particular heart rate.
select count(heart_rate),heart_rate
from heart_attack_dataset 
	where heart_rate >1 
    group by heart_rate 
    order by heart_rate;
    
    
