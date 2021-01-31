You just installed MySQL or MariaDB and you receive this error: `Access Denied for User 'root'@'localhost' (using password: YES) - No Privileges`. How to solve it? In many websites there are a lot of different approaches and solutions, often with 5 or more steps to do.

A working solution for old systems is to execute `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';`
if you get: `ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'BY 'password'' at line 1` ... then your version of MariaDB is not compatible with this solution.

In this case is better to use 
```bash
sudo mysql

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password USING PASSWORD('password');` this should correctly reset your password.
```

