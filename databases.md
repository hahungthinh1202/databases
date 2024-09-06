### Exercises 2: Single Table Queries

Question 1:
select * from goal;
![image](https://github.com/user-attachments/assets/d9e9e350-d0c6-4bee-9c0d-d6f175443c63)

Question 2:
select name from airport where iso_country ='FI';
![image](https://github.com/user-attachments/assets/b9e5e22b-de15-4abd-acab-5331e6f9d88f)

Question 3:
select name from airport where iso_country ='FI' group by name;
![image](https://github.com/user-attachments/assets/7174d5db-01d0-4af2-80a7-01cfb6e3edde)

Question 4:
select name, type from airport where iso_country ='FI' group by type, name;
![image](https://github.com/user-attachments/assets/4e256d21-7d2c-4d69-b588-ad16bf0d2357)

Question 5:
select name from country where name like 'f%';
![image](https://github.com/user-attachments/assets/ed32e57e-a3c8-47ce-a276-76ef42dcd741)

Question 6:
Select name as name from country where name like '%f%';
![image](https://github.com/user-attachments/assets/f4b94ee4-aa7e-4f66-88f8-90ae45e7e637)

Question 7:
select location from game where screen_name = "Vesa";
![image](https://github.com/user-attachments/assets/ade081df-9ef7-457a-9053-e5cb1f297f7e)

Question 8:
select co2_consumed from game where screen_name = "Ilkka";
![image](https://github.com/user-attachments/assets/2bd23e4c-ebc4-4233-891d-1fb2cffaa188)

Question 9:
select distinct game.co2_budget from game;
![image](https://github.com/user-attachments/assets/3d1017eb-c3df-4941-8c13-77ede6d8b845)

Question 10:
select screen_name, co2_budget, co2_consumed, @co2_left:=co2_budget-co2_consumed as co2_left
from game  
where screen_name = 'Ilkka';
![image](https://github.com/user-attachments/assets/f5916a07-438e-4d89-bd0f-4c69d4a85e52)

  
