# QBCore Database
In order to have to QBCore server, you will need a database. There are multiple databases but amongst the most well known are HeidiSQL, MySQL, and MariaDB.

## HeidiSQL
If you plan to use HeidiSQL which is the most well known in the FiveM community, you will need [**XAMPP**](https://www.apachefriends.org/download.html).

1) Once downloaded XAMPP. Download [**HeidiSQL**](https://www.heidisql.com/download.php) and run it.

2) Open XAMPP and press on the MySQL box. Once checked, proceed to the following step.

3) Open HeidiSQL, click the green circle with plus sign and name it something (doesn't matter what). Click open, in an empty space in the left pane, right click and highlight "Create New" and select database, name it something (doesn't matter what) but you will need the name of this later!

4) Assuming you have [oxmysql](https://github.com/overextended/oxmysql/releases) already installed, you can just set the following with your own database details (only if txAdmin has not done it for you already).
```cfg
set mysql_connection_string "mysql://user:password@host/database?charset=utf8mb4&dateStrings=true"
```

## MariaDB
1) Make a copy of your database.

2) Completely uninstall XAMPP

3) Go to https://mariadb.org/download/?t=mariadb&p=mariadb&r=10.6.5&os=windows&cpu=x86_64&pkg=msi&m=netactuate and install the version that you use in my case 64 bits.

4) After that, the installation is very easy, you just have to follow everything, in the last step if you want you can put a password is (optional) you can deactivate the password by unchecking the first box.

5) After that installation you will be able to enter HeidiSQL without having to activate anything as you did before with XAMPP, now you will not have to do anything unless you have not setup your mysql_connection_string.

## MySQL
1) Uninstall XAMPP if you have it installed.

2) Go to https://dev.mysql.com/downloads/mysql/, download the latest version and install it.

3) Search for the following in your vscode extensions `cweijan.vscode-mysql-client2`. Download it and a new icon on your sidebar will appear.

4) Click on the new icon and add all your details necessary to connect your database. After that you will be able to do everything from vscode. Just remember to setup you mysql_connection_string.