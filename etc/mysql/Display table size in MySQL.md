# Display table size in MySQL
Use the following sql to query the space occupied by each table in the database.
```sql
use information_schema;
SELECT
  table_schema as 'database',
  table_name as 'table_name',
  table_rows as 'records',
  truncate(data_length/1024/1024, 2) as 'data_size(MB)',
  truncate(index_length/1024/1024, 2) as 'index_size(MB)',
  truncate(DATA_FREE/1024/1024, 2) as 'data_free_size(MB)'
from 
  information_schema.tables
where 
  table_schema='<database_name>'
order by 
  data_length desc, index_length desc;
```

Enjoy!