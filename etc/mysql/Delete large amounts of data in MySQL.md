# Delete large amounts of data in MySQL
Recently I want to delete a large amount of data from mysql. There are about 400 million records. Fortunately, the data 
to be deleted can be queried according to the index. If I delete one by one, it will be very slow. If the entire 
deletion will cause the database to freeze. So I Write a script to delete these data in batches. The script probably 
looks like this.
```shell
#!/bin/bash
echo 'begin delete...' > /tmp/delete_target_record.log
input="/home/work/target_record.txt"
total=0;
while IFS= read -r line
do
       stop_flag=0;
       while(( $stop_flag<=0 ))
       do
               stop_flag=`mysql -h<host_address> -P<port> -u<user_name> -p<password> -e "delete from <table_name> where <column_name>='$line' limit 2000;" -vvv|grep 'Query OK, 0 rows affected'|wc -l`
               sleep 1s;
               total=$(($total+2));
               echo "deleting... '$line', total delete : $total k" >> /tmp/delete_target_record.log
       done
done < "$input"
```
This file '/home/work/target_record.txt' stores the conditions that need to be deleted.

It should be noted that the query conditions here must be able to hit the index. Deleting 2,000 items at one time will 
not cause data freezes.

Enjoy!