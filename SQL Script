create user Ehab WITH password 'IntMain#555'
create database Sales
WITH 
OWNER Ehab
ENCODING= UTF8

CREATE table categories(
category_id serial primary key,
category_name text
)

CREATE TABLE brand(
brand_id serial primary key,
brand_name text
)

create table products(
product_id serial primary key,
product_name text NOT NULL,
brand_id int NOT NULL,
category_id INT NOT NULL,
model_year int,
list_price DECIMAL(8,2),
FOREIGN KEY (brand_id) references brand (brand_id),
FOREIGN KEY (category_id) references  categories (category_id) on delete cascade on update cascade
)

create table customers(
customer_id SERIAL PRIMARY KEY,
first_name NAME NOT NULL,
last_name NAME NOT NULL,
phone text,
email text,
street text,
city VARCHAR(20),
state text,
zip_code text not null
)

CREATE TABLE stores (
	store_id  SERIAL PRIMARY KEY,
	store_name VARCHAR (255) NOT NULL,
	phone VARCHAR (25),
	email VARCHAR (255),
	street VARCHAR (255),
	city VARCHAR (255),
	state VARCHAR (10),
	zip_code VARCHAR (5)
);

CREATE TABLE staffs (
	staff_id SERIAL PRIMARY KEY,
	first_name VARCHAR (50) NOT NULL,
	last_name VARCHAR (50) NOT NULL,
	email VARCHAR (255) NOT NULL UNIQUE,
	phone VARCHAR (25),
	active BOOLEAN NOT NULL,
	store_id INT NOT NULL,
	manager_id INT,
	FOREIGN KEY (store_id) REFERENCES stores (store_id) ON DELETE CASCADE,
	FOREIGN KEY (manager_id) REFERENCES staffs (staff_id) ON DELETE cascadE ON UPDATE CASCADE
);

CREATE TABLE orders (
	order_id SERIAL PRIMARY KEY,
	customer_id INT,
	order_status smallint NOT NULL,
	order_date DATE NOT NULL,
	required_date DATE NOT NULL,
	shipped_date DATE,
	store_id INT NOT NULL,
	staff_id INT NOT NULL,
	FOREIGN KEY (customer_id) REFERENCES customers (customer_id) ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (store_id) REFERENCES stores (store_id) ON DELETE CASCADE ON UPDATE CASCADE,
	FOREIGN KEY (staff_id) REFERENCES staffs (staff_id) ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE TABLE order_items (
	order_id INT,
	item_id INT,
	product_id INT NOT NULL,
	quantity INT NOT NULL,
	list_price DECIMAL (10, 2) NOT NULL,
	discount DECIMAL (4, 2) NOT NULL DEFAULT 0,
	PRIMARY KEY (order_id, item_id),
	FOREIGN KEY  (order_id) REFERENCES orders(order_id),
	FOREIGN KEY (product_id) REFERENCES products (product_id)
);

CREATE TABLE stocks (
	store_id INT,
	product_id INT,
	quantity INT,
	PRIMARY KEY (store_id, product_id),
	FOREIGN KEY (store_id) REFERENCES stores (store_id),
	FOREIGN KEY (product_id) REFERENCES products (product_id) 
);



