# Air-BNB-Project
Air BNB Project using Mysql.


show databases;
create database Air_BNB;
use air_BNB;
select * from listing;
select * from booking_detail bd ;

#1. Import Data from both the .CSV files to create tables, Listings and Booking Details.

#2. Q2 Write a query to show names from Listings table

select name from booking_detail bd ;

#3. Write a query to fetch total listings from the listings table

select count(listing_id) Total_Listing from listing l ;

select count(distinct(listing_id)) Total_Listing from listing l ; 

#4. Write a query to fetch total listing_id from the booking_details table

select count(distinct (id)) from booking_detail bd ;

select distinct(count(listing_id))
from booking_detail bd
inner join listing l
on bd.listing_id = l.id;

#5. Write a query to fetch host ids from listings table

select host_id Host_ID from Listing l ;
select count(host_id) Host_ID_Count from Listing l ; 
select count(distinct(Host_id)) from Listing l ; 

#6. Write a query to fetch all unique host name from listings table

select distinct(host_name) from Listing l ; 

#7. Write a query to show all unique neighbourhood_group from listings table

select distinct (neighbourhood_group) Unique_Neighbourhood_Group  from Listing l ; 

#8. Write a query to show all unique neighbourhood from listings table

select distinct (neighbourhood) Unique_Neighbourhood  from Listing l ;

#9. Write a query to fetch unique room_type from listings tables

select distinct (room_type) Unique_Room_type  from Listing l ;
     
#10. Write a query to show all values of Brooklyn & Manhattan from listings tables

select * from Listing l ;

with booking_1 as
(select * from booking_detail bd 
join listing l 
on bd.listing_id = l.id
where neighbourhood_group = "Manhattan" or "Brooklyn")
select count(*) from booking_1;

with bvbv1 as
(select * from listing l where neighbourhood_group = 'Manhattan' or 'brooklyn')
select count(*) from bvbv1 ;


select count(*) from booking_detail bd 
join listing l 
on bd.listing_id = l.id
where neighbourhood_group in ("Manhattan", "Brooklyn");

select count(*) from booking_detail bd 
join listing l 
on bd.listing_id = l.id
where neighbourhood_group = "manhattan" or "Brooklyn";

#11. Write a query to show maximum price from booking_details table

select max(price) Maximum_Price from booking_detail bd ; 

#12. Write a query to show minimum price fron booking_details table

select min(price) Minimum_Price from booking_detail bd ;

#13. Write a query to show average price from booking_details table

select avg(price) Average_Price from booking_detail bd ;

#14. Write a query to show minimum value of minimum_nights from booking_details table

select min(minimum_nights) Minimum_Value from booking_detail bd ;

#15. Write a query to show maximum value of minimum_nights from booking_details table

select max(minimum_nights) Maximum_Value from booking_detail bd ;

#16. Write a query to show average availability_365

select avg(availability_365) Avg_Availability_365 from booking_detail bd ;

#17. Write a query to show id , availability_365 and all availability_365 values greater than 300

select listing_id, availability_365 from booking_detail bd where availability_365 >300;

#18. Write a query to show count of id where price is in between 300 to 400

select count(listing_id) from booking_detail bd where price between 300 and 400;

#19. Write a query to show count of id where minimum_nights spend is less than 5

select count(listing_id) from booking_detail bd where minimum_nights <5;

#20. Write a query to show count where minimum_nights spend is greater than 100

select count(listing_id) from booking_detail bd where minimum_nights >100;

#21. Write a query to show all data of listings & booking_details

select * from booking_detail bd2 , listing l2 ;

select * from booking_detail bd 
union
select * from listing l ;

select * from booking_detail bd 
left join listing l 
on BD.listing_id = L.id ;

#22. Write a query to show host name and price

select host_name, PRICE
from booking_detail bd join listing l 
on BD.listing_id = L.id ;

#23. Write a query to show room_type and price

select ROOM_TYPE, PRICE
from booking_detail bd join listing l 
on BD.listing_id = L.id ;

#24. Write a query to show neighbourhood_group & minimum_nights spend

select neighbourhood_group, minimum_nights 
from booking_detail bd join listing l 
on BD.listing_id = L.id ;

#25. Write a query to show neighbourhood & availability_365

select neighbourhood, availability_365 
from booking_detail bd join listing l 
on BD.listing_id = L.id ;

#26. Write a query to show total price by neighbourhood_group
 
select sum(price), neighbourhood_group
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by neighbourhood_group;

#27. Write a query to show maximum price by neighbourhood_group

select max(price), neighbourhood_group
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by neighbourhood_group;

#28. Write a query to show maximum night spend by neighbourhood_group

select * from booking_detail bd  ;

select max(minimum_nights) , neighbourhood_group
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by neighbourhood_group;

#29. Write a query to show maximum reviews_per_month spend by neighbourhood

select max(reviews_per_month) , neighbourhood
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by neighbourhood;

#30. Write a query to show maximum price by room type

select max(price) Maximum_Price, room_type
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by room_type;

#31. Write a query to show average number_of_reviews by room_type

select avg(number_of_reviews) Avg_no_of_review, room_type
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by room_type;

#32. Write a query to show average price by room type

select avg(price) Avg_Price, room_type
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by room_type;

#33. Write a query to show average night spend by room type

select avg(minimum_nights) minimum_nights, room_type
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by room_type;


#34. Write a query to show average price by room type but average price is less than 100

select avg(price) Avg_price, room_type
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by room_type having avg(price) <100;

#35. Write a query to show average night by neighbourhood and average_nights is greater than 5

select avg(minimum_nights) Avg_MInimum_nights, neighbourhood
from booking_detail bd join listing l 
on bd.listing_id = l.id
group by neighbourhood having avg(minimum_nights) > 5 ;


#36. Write a query to show all data from listings where price is greater than 200 using sub-query.

select * from booking_detail bd ;
select * from booking_detail bd where price > 200;

select l.*, bd.price  from booking_detail bd 
inner join listing l 
on BD.listing_id = L.id 
where price>(select max(price) from booking_detail bd where price =200);

#37. Write a query to show all values from booking_details table where host id is 314941 using sub-query.

select bd.*,l.host_id from listing l 
inner join booking_detail bd 
on l.id = bd.listing_id 
where host_id = (select max(host_id) from listing l where host_id=314941);

#38. Find all pairs of id having the same host id, each pair coming once only.

show databases ;
use air_bnb;

select distinct t1.id, t1.host_id, t2.host_id
from listing t1 join listing t2
on t1.id<>t2.id and t1.host_id=t2.host_id;


SELECT bd.listing_id AS Booking_id1, l.id AS Listing_id2
FROM booking_detail bd 
INNER JOIN listing l ON bd.listing_id  < l.id  group by calculated_host_listings_count  having hos <1;

SELECT bd.listing_id AS Booking_id1, host_id, listing_id AS Listing_id2
FROM booking_detail bd  
INNER JOIN listing l  ON bd.listing_id  < l.id 
group by host_id having host_id<1;


select *
from listing l2  
inner join booking_detail bd 
on bd.listing_id < l2.id 
group  by  l2.host_id having l2.host_id <1;


with VAYEDA
as (
select a.id, b.id, 
case when a.id > b.id 
then concat(b.id,'-',a.id) 
when b.id > a.id 
then concat(a.id,'-',b.id) 
else concat(a.id,'-',b.id) 
end as Pairs from listing a  
left join listing b 
on a.host_id = b.host_id 
where a.id != b.id)
(
select max(a.id), 
min(b,id) 
from vayeda 
group by pairs);



with VAYEDA
as (
select a.id as id1, b.id as id2, 
case when a.id > b.id 
then concat(b.id,'-',a.id) 
when b.id > a.id 
then concat(a.id,'-',b.id) 
else concat(a.id,'-',b.id) 
end as Pairs from listing a  
left join listing b 
on a.host_id = b.host_id 
where a.id != b.id);, 

vayeda2
as (
select max(id1) as id1, 
min(id2) as id2 
from vayeda 
group by pairs)
,
vayeda3 as( 

select distinct
case when id1 > id2
then concat(id2,'-',id1) 
when id2 > id1 
then concat(id1,'-',id2) 
else concat(id1,'-',id2) 
end as Pairs
from vayeda2)
 select count(*) from vayeda3; 




with VAYEDA
as (
select a.id as id1, b.id as id2, 
case when a.id > b.id 
then concat(b.id,'-',a.id) 
when b.id > a.id 
then concat(a.id,'-',b.id) 
else concat(a.id,'-',b.id) 
end as Pairs from listing a  
left join listing b 
on a.host_id = b.host_id 
where a.id != b.id), 

vayeda2
as (
select max(id1) as id1, 
min(id2) as id2 
from vayeda 
group by pairs)

,

vayeda3 as( 

select distinct
case when id1 > id2
then concat(id2,'-',id1) 
when id2 > id1 
then concat(id1,'-',id2) 
else concat(id1,'-',id2) 
end as Pairs
from vayeda2)
 select count(*) from vayeda3; 
  

select distinct(bd.listing_id) , l.host_id 
from listing l 
join booking_detail bd 
on l.host_id = bd.listing_id
where l.host_id >bd.listing_id  ;


#39. Write an sql query to show fetch all records that have the term cozy in name

select * from listing l where name = ()


select * from listing l where name like '%cozy%';


#40. Write an sql query to show price, host id, neighbourhood_group of manhattan neighbourhood_group

select price, host_id , neighbourhood_group  from listing l 
inner join booking_detail bd 
on l.id = bd.listing_id 
where neighbourhood_group = 'manhattan';

with vayed as
(select price, host_id , neighbourhood_group  from listing l 
inner join booking_detail bd 
on l.id = bd.listing_id 
where neighbourhood_group = 'manhattan')
select count(*) Count_of_Manhattan_Group from vayed ;

#41. Write a query to show id , host name, neighbourhood and price but only for Upper West Side & Williamsburg neighbourhood, also make sure price is greater than 100


select id, host_name, neighbourhood, price
from listing l inner join booking_detail bd 
on l.id = bd.listing_id 
where neighbourhood = 'UPPER east side' and price>100;

#42. Write a query to show id , host name, neighbourhood and price for host name Elise and neighbourhood is Bedford-Stuyvesant

select id, host_name, neighbourhood, price
from listing l inner join booking_detail bd 
on l.id = bd.listing_id 
where neighbourhood = 'bedford-stuyvesant' and host_name = 'elise';


#43. Write a query to show host_name, availability_365,minimum_nights only for 100+ availability_365 and minimum_nights

select * from booking_detail bd  ;

select host_name, availability_365, minimum_nights
from listing l inner join booking_detail bd 
on l.id = bd.listing_id 
where availability_365>100 and minimum_nights>100;


#44. Write a query to show to fetch id , host_name , number_of_reviews, and reviews_per_month but show only that 
#records where number of reviews are 500+ and review per month is 5+

select * from booking_detail bd2 ;

select id, host_name, number_of_reviews, reviews_per_month
from listing l inner join booking_detail bd 
on l.id = bd.listing_id 
where number_of_reviews>500 and reviews_per_month>5;

#45. Write a query to show neighbourhood_group which have most total number of review

select * from booking_detail bd2 ;
select * from listing l ;

select neighbourhood_group, max(number_of_reviews)  
from booking_detail bd inner join listing l 
on l.id = bd.listing_id
group by neighbourhood_group ; 

select neighbourhood_group, sum(number_of_reviews)  
from booking_detail bd inner join listing l 
on l.id = bd.listing_id
group by neighbourhood_group ; 

#46. Write a query to show host name which have most cheaper total price

select host_name, min(price) Minimum_Price 
from booking_detail bd inner join listing l 
on l.id = bd.listing_id
group by host_name order by Minimum_price;

#47. Write a query to show host name which have most costly total price

select host_name, max(price) Maximum_Price 
from booking_detail bd inner join listing l 
on l.id = bd.listing_id
group by host_name order by MAXIMUM_PRICE DESC;

#48. Write a query to show host name which have max price using sub-query

select HOST_NAME, price 
from booking_detail bd2 
inner join listing l
where price = (select max(price) from booking_detail bd ); 

#49. Write a query to show neighbourhood_group where price is less than 100

select neighbourhood_group, price
from booking_detail bd 
inner join listing l 
where price <100;

#50. Write a query to find max price, average availability_365 for each room type and order in ascending by maximum price.

select * from booking_detail bd2 ;
select max(price) Maximum_Price, avg(availability_365) Average_Availability_365, room_type
from booking_detail bd 
inner join listing l 
on l.id = bd.listing_id 
group by room_type order by max(price) asc;
