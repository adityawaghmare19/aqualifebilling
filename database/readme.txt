user-root
pass=root

here in this project we have 5 tables .
 that are --

login - fields are- uname and password(int)

 
product- fields are-id(int),product,cat_id(varchar),price,qty(int),barcode(int),status(varchar)

rec_login -fields are- id , name ,date


sales -fields are- id,date,subtota,pay,balance,prd_id 
--note all field are in int formate except date and prd_id and prd_id *doesnot contain any data* its just a failed experiment yet important

sales_product fields are- id,sales_id,product_id,sell_price,qty,total
--note all field are in int formate