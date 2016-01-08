**Step # 1: Stop the MySQL server process.**

** Step # 2: Start the MySQL (mysqld) server/daemon process with the --skip-grant-tables option so that it will not prompt for password.**

**Step # 3: Connect to mysql server as the root user.**

**Step # 4: Setup new mysql root account password i.e. reset mysql password.**

** Step # 5: Exit and restart the MySQL server.**

Here are commands you need to type for each step (login as the root user):

##### Step # 1 : Stop mysql service

`# /etc/init.d/mysql stop`

Output:

`Stopping MySQL database server: mysqld.`

##### Step # 2: Start to MySQL server w/o password:

`# mysqld_safe --skip-grant-tables &`

Output:

```
[1] 5988
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[6025]: started
```
##### Step # 3: Connect to mysql server using mysql client:

`# mysql -u root`

Output:

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1 to server version: 4.1.15-Debian_1-log
Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
mysql>
```
##### Step # 4: Setup new MySQL root user password
```
mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit
```
##### Step # 5: Stop MySQL Server:
```
/etc/init.d/mysql stop
```

Output:
```
Stopping MySQL database server: mysqld
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[6186]: ended
[1]+  Done                    mysqld_safe --skip-grant-tables
```
##### Step # 6: Start MySQL server and test it

```
/etc/init.d/mysql start
mysql -u root -p
```
