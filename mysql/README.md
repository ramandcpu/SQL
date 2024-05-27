
# Setting Up MySQL on Windows


In this tutorial, we'll walk through the installation process for MySQL and MySQL Workbench. Additionally, we'll cover the steps to create a sample database, which will serve as a practical exercise. MySQL is a popular open-source relational database management system, renowned for its reliability and performance. On the other hand, MySQL Workbench is a comprehensive visual tool designed for database architecture, administration, and development tasks.

The reason for installing MySQL Workbench is that I will be working on Windows, and this tool will be particularly useful for my upcoming tutorials on Power BI and Tableau. These business intelligence tools often require seamless integration with databases, and MySQL Workbench provides a user-friendly interface for managing and interacting with MySQL databases.

However, it's important to note that while MySQL Workbench offers a convenient graphical interface, I will also delve into the command-line interface (CLI) and learn how to execute MySQL commands directly. This approach will not only enhance your understanding of the underlying database operations but also equip you with the necessary skills to work with MySQL in various environments, including server deployments where a graphical interface may not be available.

Additionally, when working with sample databases from GitHub or other sources, the command prompt will come in handy for tasks such as creating and populating databases. By mastering the command-line interface, you will gain flexibility and control over your MySQL environment, enabling you to efficiently manage and manipulate data.

By combining the visual capabilities of MySQL Workbench and the command-line interface, you will gain a comprehensive understanding of MySQL, enabling you to work efficiently with databases in your Power BI and Tableau projects.



## Installing MySQL Server

While the specific steps may vary as software updates are released, the overall installation procedure should remain largely consistent. These are high-level overview steps, but it's essential to carefully follow the prompts during the installation process. Ensure that you select both MySQL and MySQL Workbench components when prompted, as we'll be utilizing both tools in our upcoming tutorials.

Go to https://dev.mysql.com/downloads/installer/ and download the MySQL Installer for Windows.

You will be given two options one will require the use of internet while installing the other will not.

.
![workbench](/mysql/pics/mysql-1.png)
.

Run the downloaded installer file.

In the installer, choose the "Custom" setup type.

Select "MySQL Server" and optionally "MySQL Workbench" if you want to install it together. Click "Next".


Accept the license agreements and click "Next".
Select "Execute" to install the selected products.
On the "Type and Networking" screen, select the desired MySQL Server configuration type (Development Machine is recommended for testing).
Set the root password for your MySQL instance and click "Next".
On the "Accounts and Roles" screen, click "Next" to proceed.
Click "Execute" to apply the configuration.
Once completed, click "Finish" to exit the installer.


To set up the Windows environment for MySQL commands to work, follow these steps:

1. Open the Start menu and search for "Environment Variables". Select "Edit the system environment variables".

2. In the System Properties window, click the "Environment Variables" button.

3. Under the "System Variables" section, scroll down and find the "Path" variable, then click "Edit".

4. Click "New" and enter the full path to the MySQL bin directory, e.g., "C:\Program Files\MySQL\MySQL Server 8.0\bin". This adds the MySQL bin directory to the system PATH.

5. Click "OK" on all open windows to save the changes.

6. Open a new Command Prompt window. You should now be able to run MySQL commands like `mysql`, `mysqladmin`, `mysqldump`, etc. from any directory.

To verify, try running:

```
mysql --version
```

This should display the installed MySQL server version.

Alternatively, you can also add the MySQL bin directory to your user PATH instead of the system PATH:

1. In the "Environment Variables" window, under "User variables", find and edit the "Path" variable.

2. Click "New" and enter the MySQL bin directory path.

3. Save the changes and open a new Command Prompt.

This way, only your user account will have access to run MySQL commands from any directory.

By adding the MySQL bin directory to the PATH, you can run MySQL utilities and connect to the server from any location without having to specify the full path each time.

Here are the step-by-step instructions to install Git on Windows:

1. Go to https://git-scm.com/downloads and click on the "Windows" download link.

2. Once the download completes, run the installer executable file.

3. On the license window, review the license agreement and click "Next" if you agree with the terms.

4. On the Select Destination Location window, either keep the suggested default directory or click "Browse" to choose a different location. Click "Next" to proceed.

5. On the Select Components window, you can select additional options or keep the defaults selected. Click "Next".

6. On the Choosing the default editor used by Git window, select your preferred text editor or keep the recommended default. Click "Next".

7. On the Adjusting your PATH environment window, select "Use Git from the Windows Command Prompt" to add Git to your system's PATH. This allows you to run Git from any directory in the command prompt.

8. On the Choosing HTTPS transport backend window, select the "Use the OpenSSL library" option. Click "Next".

9. On the Configuring the line ending conversions window, select the recommended option for your development platform (e.g. "Checkout Windows-style, commit Unix-style line endings"). Click "Next".

10. On the Configuring the terminal emulator to use with Git Bash window, select the recommended default option. Click "Next".

11. Review your selections on the Installing window. Click "Install" to begin the installation process.

12. Once the installation completes, click "Finish" to exit the installer.

After installation, you can launch Git Bash (a bash emulator) from the Start menu or run git commands in the regular Windows Command Prompt.

```
C:\Users\Administrator\test_db>git --version
```
```
git version 2.45.1.windows.1
```

Now that we have installed MySQL, Workbench, Git, and set all the necessary variables, it's time to create our sample database.
We will use the following sample;

https://github.com/datacharmer/test_db

```
>git clone https://github.com/datacharmer/test_db.git
```
```
>cd test_db
```
```
C:\Users\Administrator\test_db>mysql -u root -p < employees.sql
```
```
C:\Users\Administrator\test_db>mysql -u root -p < employees.sql
Enter password: **********
```

```
INFO
CREATING DATABASE STRUCTURE
INFO
storage engine: InnoDB
INFO
LOADING departments
INFO
LOADING employees
INFO
LOADING dept_emp
INFO
LOADING dept_manager
INFO
LOADING titles
INFO
LOADING salaries
data_load_time_diff
00:01:46
```

```
C:\Users\Administrator\test_db>mysql -u root -p
Enter password: **********
```
```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 8.0.37 MySQL Community Server - GPL

Copyright (c) 2000, 2024, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

```
mysql> use employees;
```
```
Database changed
```

```
mysql> select * from employees;
```
The result below is truncated.

```
+--------+------------+----------------+------------------+--------+------------+
| emp_no | birth_date | first_name     | last_name        | gender | hire_date  |
+--------+------------+----------------+------------------+--------+------------+
|  10001 | 1953-09-02 | Georgi         | Facello          | M      | 1986-06-26 |
|  10002 | 1964-06-02 | Bezalel        | Simmel           | F      | 1985-11-21 |
|  10003 | 1959-12-03 | Parto          | Bamford          | M      | 1986-08-28 |
|  10004 | 1954-05-01 | Chirstian      | Koblick          | M      | 1986-12-01 |
|  10005 | 1955-01-21 | Kyoichi        | Maliniak         | M      | 1989-09-12 |
|  10006 | 1953-04-20 | Anneke         | Preusig          | F      | 1989-06-02 |

```
If the database is very large then the better command will;
```
mysql> select * from employees limit 20;
```
```
+--------+------------+------------+-------------+--------+------------+
| emp_no | birth_date | first_name | last_name   | gender | hire_date  |
+--------+------------+------------+-------------+--------+------------+
|  10001 | 1953-09-02 | Georgi     | Facello     | M      | 1986-06-26 |
|  10002 | 1964-06-02 | Bezalel    | Simmel      | F      | 1985-11-21 |
|  10003 | 1959-12-03 | Parto      | Bamford     | M      | 1986-08-28 |
|  10004 | 1954-05-01 | Chirstian  | Koblick     | M      | 1986-12-01 |
|  10005 | 1955-01-21 | Kyoichi    | Maliniak    | M      | 1989-09-12 |
|  10006 | 1953-04-20 | Anneke     | Preusig     | F      | 1989-06-02 |
|  10007 | 1957-05-23 | Tzvetan    | Zielinski   | F      | 1989-02-10 |
|  10008 | 1958-02-19 | Saniya     | Kalloufi    | M      | 1994-09-15 |
|  10009 | 1952-04-19 | Sumant     | Peac        | F      | 1985-02-18 |
|  10010 | 1963-06-01 | Duangkaew  | Piveteau    | F      | 1989-08-24 |
|  10011 | 1953-11-07 | Mary       | Sluis       | F      | 1990-01-22 |
|  10012 | 1960-10-04 | Patricio   | Bridgland   | M      | 1992-12-18 |
|  10013 | 1963-06-07 | Eberhardt  | Terkki      | M      | 1985-10-20 |
|  10014 | 1956-02-12 | Berni      | Genin       | M      | 1987-03-11 |
|  10015 | 1959-08-19 | Guoxiang   | Nooteboom   | M      | 1987-07-02 |
|  10016 | 1961-05-02 | Kazuhito   | Cappelletti | M      | 1995-01-27 |
|  10017 | 1958-07-06 | Cristinel  | Bouloucos   | F      | 1993-08-03 |
|  10018 | 1954-06-19 | Kazuhide   | Peha        | F      | 1987-04-03 |
|  10019 | 1953-01-23 | Lillian    | Haddadi     | M      | 1999-04-30 |
|  10020 | 1952-12-24 | Mayuko     | Warwick     | M      | 1991-01-26 |
+--------+------------+------------+-------------+--------+------------+
20 rows in set (0.00 sec)

```

Here are the full steps to open MySQL Workbench, connect to a database, and view your databases:

## Opening MySQL Workbench

### Launch the MySQL Workbench application on your computer.

Upon launching MySQL Workbench, you'll be greeted with the "Welcome to MySQL Workbench" screen. This window displays the connections you created during the installation process. Locate the connection you want to use and double-click on it. You will then be prompted to enter the password associated with that connection. Type in the correct password and hit enter or click "OK." This action will authenticate your credentials and launch the MySQL Workbench interface. Once the Workbench is open, you'll have access to a comprehensive visual environment for managing your MySQL databases. From here, you can explore existing databases, create new ones, design schemas, execute queries, and perform various administrative tasks.

.
![workbench](/mysql/pics/mysql-2.png)
.
### Viewing Your Databases

 In the MySQL Workbench window, expand the "Schemas" section in the Navigator panel on the left.

You will see a list of all databases associated with the connection you just created.

.
![workbench](/mysql/pics/mysql-3.png)
.
To view the tables and data within a specific database, double-click on the database name in the "Schemas" list. This will open the database schema in the main window.

You can now browse the tables, views, and other objects within the database by expanding the relevant sections in the schema viewer.

By following these steps, you can easily connect MySQL Workbench to your desired database and explore its contents visually. The Workbench provides a user-friendly interface for managing and interacting with your MySQL databases.





