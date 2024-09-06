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

--------------------------------------------------------------------------------------------------------------------------

### Exercises 3: Multiple Table Queries

Question 1:
select country.name as "country name", airport.name as "airport name"
from airport, country
where airport.iso_country = country.iso_country and country.name = "Iceland";
![image](https://github.com/user-attachments/assets/7f2af940-8a48-4fd3-97e1-870e139f7cff)

Question 2:
select airport.name as "airport name"
from airport
where airport.type = 'large_airport' and iso_country = 'FR';
![image](https://github.com/user-attachments/assets/d641ec70-a3f6-48f7-b5cc-6f8449731e1d)

Question 3:
select country.name as 'country_name', airport.name as 'airport name'
from airport, country 
where airport.iso_country = country.iso_country and country.continent = 'AN';
![image](https://github.com/user-attachments/assets/892f9e2c-9923-4060-8b67-71924b763882)

Question 4:
select airport.elevation_ft
from airport, game
where game.location = airport.ident and game.screen_name = 'Heini';
![image](https://github.com/user-attachments/assets/6538a8a4-89ce-4b5c-a016-695960488d82)

Question 5:
select airport.elevation_ft * 0.3048 as 'elevation_m'
from airport, game
where game.location = airport.ident and game.screen_name = 'Heini';
![image](https://github.com/user-attachments/assets/08bf638e-d264-4bea-a4f9-a47eb32ec87d)

Question 6:
select name
from game, airport
where airport.ident = game.location and game.screen_name = 'Ilkka';
![image](https://github.com/user-attachments/assets/feafbad8-0e15-434c-9cb8-88604d88a95c)

Question 7:
select country.name
from airport, game, country
where game.screen_name = 'Ilkka' 
  and game.location = airport.ident 
  and airport.iso_country = country.iso_country;
![image](https://github.com/user-attachments/assets/bbc96790-c745-4c9b-bd7d-9ea80b4739a4)

Question 8:
select goal.name
from goal, goal_reached, game
where game.screen_name = 'Heini' 
  and game.id = goal_reached.game_id 
  and goal_reached.goal_id = goal.id;
![image](https://github.com/user-attachments/assets/494f879c-6ef3-480e-ad5b-cf0eeceabb93)

Question 9:
select airport.name
from goal, airport, game, goal_reached
where game.screen_name = 'Ilkka'
  and game.location = airport.ident
  and game.id = goal_reached.game_id
  and goal_reached.goal_id = goal.id
  and goal.name = 'CLOUDS';
![image](https://github.com/user-attachments/assets/74f78e50-0f83-4282-8985-783de92eba9f)

Question 10:
select country.name
from goal, airport, game, goal_reached, country
where country.iso_country = airport.iso_country
  and game.screen_name = 'Ilkka'
  and game.location = airport.ident
  and game.id = goal_reached.game_id
  and goal_reached.goal_id = goal.id
  and goal.name = 'CLOUDS';
![image](https://github.com/user-attachments/assets/71309987-26f5-4d01-bc02-8edd1b977a41)


--------------------------------------------------------------------------------------------------------------------------

### Exercises 4: Join

Question 1:
select country.name as 'country name', airport.name as 'airport.name'
from country join airport on country.iso_country = airport.iso_country
where country.iso_country = 'FI' and airport.scheduled_service = 'yes';
![image](https://github.com/user-attachments/assets/2d7e9f22-1cad-4a5c-84e0-09e05a47fbb0)

Question 2:
select game.screen_name, airport.name
from game join airport on game.location = airport.ident;
![image](https://github.com/user-attachments/assets/83894672-49d1-4edf-9c3f-adfc175373c0)

Question 3:
select game.screen_name, country.name
from game join airport on game.location = airport.ident
    join country on airport.iso_country = country.iso_country;
![image](https://github.com/user-attachments/assets/f8e3148b-d181-48ce-9f18-b47069f4795a)

Question 4:
select airport.name, game.screen_name
from airport left join game on airport.ident = game.location
where airport.name like '%Hels%';
![image](https://github.com/user-attachments/assets/0a2c9134-f60d-4cbf-892e-ee8dac36c8b5)

Question 5:
select goal.name, game.screen_name
from goal left join goal_reached on goal.id = goal_reached.goal_id
    left join game on goal_reached.game_id = game.id;
![image](https://github.com/user-attachments/assets/28910da9-3775-40aa-9baa-74e8065bbbe5)


### Exercises 5: Subqueries

Question 1:

Question 2:

Question 3:

Question 4:

Question 5:

Question 6:

Question 7:

Question 8:

Question 9:

Question 10:

### Exercises 6: Aggregate Queries

Question 1:

Question 2:

Question 3:

Question 4:

Question 5:

Question 6:

Question 7:

Question 8:

Question 9:

Question 10:

### Exercises 7: Update Queries

Question 1:

Question 2:

Question 3:

Question 4:

Question 5:

Question 6:

Question 7:

Question 8:

Question 9:

Question 10:

### Exercises 7: Database Design

Question 1:

Question 2:

Question 3:

Question 4:

Question 5:

Question 6:

Question 7:

Question 8:

Question 9:

Question 10:
  
