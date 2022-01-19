# master-slave-architecture
 

#### On macOS, you can install MySQL easily using Homebrew.

https://flaviocopes.com/mysql-how-to-install/


#### Install MYSQL IN ec2

https://github.com/harsh6768/deploy-in-ec2

### Open mysql in terminal : 

use command : 

       mysql -u root -p
       
 
### After installing mysql in MASTER AND SLAVE instance we will start with Master configuration.


Master configuration changes : 

1. open mysqld.cnf using vi or nano editor to edit.
 
      vi /etc/mysql/mysql.conf.d/mysqld.cnf
      
   A. #bind-address  = 127.0.0.1
      
      Uncomment bind-address and Replace 127.0.0.1 with the master or source  server’s PRIVATE IP address. 
      
      after modification : 
      
       bind-address = master_private_ip
      
      
   B.  #server_id 
      Uncomment server_id and server_id can be any integer but it shoule be unique to all your database serverIds .
      
        server_id =1
        
   C.  # log_bin = /var/log/mysql/mysql-bin.log      Uncomment log bin in file
      
         log_bin = /var/log/mysql/mysql-bin.log
         
   D. # binlog_do_db = include_database_name        Uncomment binlog_do_db  in file
   
         binlog_do_db = db_name     // db_name should which one do you wanna replicate
         
         if there are more than one db then just copy and paste the above line 
         
         binlog_do_db = db_name1
         binlog_do_db = db_name2
         
   
      
