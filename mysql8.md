
===================mysql8==================

Q1: Navicat 连接mysql 2059-Authentication plugin 'caching_sha2_password' cannot be loaded


mysql8 之前加密规则为 mysql_native_password

mysql8 创建user: bruce; password: Password123

mysql8 > CREATE USER bruce IDENTIFIED BY 'Password123';   ||  CREATE USER 'root'@'%' IDENTIFIED BY 'Password123';

mysql8 > SHOW GRANTS FOR bruce;

mysql8 > GRANT EXECUTE,INSERT,SELECT,UPDATE ON db_name.* TO 'bruce'@'%';

mysql8 > FLUSH PRIVILEGES; 

===========================================================

mysql8 修改加密规则及密码

mysql8 > ALTER USER 'root'@'localhost' IDENTIFIED BY 'your_password' PASSWORD EXPIRE NEVER;

mysql8 > ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password';

mysql8 > FLUSH PRIVILEGES;




