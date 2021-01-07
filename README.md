# automateMySQL
Automate MySQL with a script and Crontab

The aim of this script is to automate the download of a specific field from a mysql database in a very simple way and with the help of crontab in linux
Crontab is a text file that saves a list of commands to be executed in a time specified by the user.

The first part of the script is save the db credentials:
script.sh
``
#!/usr/bin/
  user=""
  password=""
  host=""
  db_name=""
  table_name=""
``
Next to define the current date:
``
  *date=$(date +"%d-%b-%Y")
``
With de db credential you can access to the data of MySql:
``
  *mysql --user=$user --password=$password --host=$host $db_name -e "SELECT fieldTable INTO OUTFILE '/path/to/your/home/_backup/date-file.txt' FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' FROM table;"
``
Finally if you want to copy the the file to othe path you must to give the permissions with:
``
  chmod -R o+rwx '/path/to/your/home/_backup/date-file.txt'
  cp '/path/to/your/home/_backup/date-file.txt' '/newpath/to/your/home/_backup/date-file.txt'
``
When we have the script,only the task has to be programmed with crontab

Command Terminal:
``
 sudo crontab -e
``
Shell Crontab:
``
  30 3 * * * sh path/file/script.sh
``
https://crontab.guru/


  

  
 
  
  


