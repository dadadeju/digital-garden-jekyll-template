create database Wordpress;
create user 'wp'@'localhost' identified by 'Wordpress666';
grant all on Wordpress.* to wp@'localhost';