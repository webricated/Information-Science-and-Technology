create table customer(cust_id number(5) primary key, cust_name varchar2(15));

create table item(item_id number(4) primary key, item_name varchar2(15), price number(5));

create table sale(bill_no number(5) primary key, bill_date date, cust_id number(5) references customer(cust_id), item_id number(4) references item(item_id), qty_sold number(4));

desc customer;

desc item;

desc sale;

insert into customer values(100,'Aman');

insert into customer values(101,'Rajjo');

insert into customer values(102,'Abhi');

insert into customer values(103,'Sahil');

insert into customer values(104,'Teja');

select * from customer;

insert into item values(111,'Lays',10);

insert into item values(112,'Kurkure',20);

insert into item values(113,'Icecream',30);

insert into item values(114,'Milk',40);

insert into item values(115,'Egg',50);

select * from item;

insert into sale values(123,'04-jan-24',100,111,2);

insert into sale values(124,'05-jan-24',101,112,2);

insert into sale values(125,'06-jan-24',102,113,2);

insert into sale values(126,'07-jan-24',103,114,2);

insert into sale values(127,'08-jan-24',104,115,2);

select * from sale;

select c.cust_name, i.item_id, s.bill_no from customer c, item i, sale s where c.cust_id=s.cust_id and i.item_id=s.item_id and s.bill_date='06-jan-24';

select i.price, s.item_id, (i.price*s.qty_sold) as total from item i, sale s where i.item_id=s.item_id group by (i.price, s.item_id, s.qty_sold);

select c.cust_id, c.cust_name from customer c, sale s, item i where i.price>30 and c.cust_id=s.cust_id and i.item_id=s.item_id;

select cust_id, count(item_id) from sale group by cust_id;

select i.item_name from item i, sale s where s.cust_id=101 and i.item_id=s.item_id;

select i.item_id, i.item_name from item I, sale s where i.item_id=s.item_id and s.bill_date='07-jan-24';

create view cust as (select s.bill_no, s.bill_date, c.cust_id, i.item_id, i.price, s.qty_sold from customer c, sale s, item i where c.cust_id=s.cust_id and i.item_id=s.item_id);

select * from cust;
