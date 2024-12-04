---
Owner: Sharafat Karim
Last edited time: 2022-12-12T11:36
---
1. Install the necessary packages:

`sudo pacman -S mysql mariadb-clients`

1. Configure MySQL:

`sudo mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql`

1. Start the MySQL service:

`sudo systemctl start mysqld`

1. Run the MySQL security script:

`sudo mysql_secure_installation`

1. Install the MySQL extension for Visual Studio Code:

Open VS Code, then type `Ctrl + P` and type “`ext install mysql`”.

1. Connect to MySQL from VS Code:

Open the Command Palette (`Ctrl + Shift + P`) and type “`MySQL: Connect to MySQL`”. Enter your MySQL credentials and click “`Connect`”.

1. Access files from MySQL in VS Code:

Open the Command Palette (`Ctrl + Shift + P`) and type “`MySQL: Show Tables`”. This will open up a list of all the tables in your database. You can right click on a table to open it in a new tab and view the data.

> [!important]  
> Taken from openAI playground