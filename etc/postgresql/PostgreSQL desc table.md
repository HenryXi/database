# PostgreSQL desc table
In MySQL you can use `desc <table_name>` to show the details of table. There is no `desc` command in PostgreSQL, but you 
can use `\d` or `\d+` to show the table detail.

**example**

```bash
database=$ \d lable
                                       Table "public.lable"
    Column     |            Type             |                    Modifiers                     
---------------+-----------------------------+--------------------------------------------------
 id            | integer                     | not null default nextval('lable_id_seq'::regclass)
 lable_name      | character varying(500)      | not null
 update_time   | timestamp without time zone | 
 page_num      | integer                     | 
 combined_name | character varying(500)      | 
Indexes:
    "lable_pkey" PRIMARY KEY, btree (id)
    "lable_lable_name_index" btree (lable_name)
    "lable_update_time_index" btree (update_time)

database=$ \d+ lable
                                                           Table "public.lable"
    Column     |            Type             |                    Modifiers                     | Storage  | Stats target | Description 
---------------+-----------------------------+--------------------------------------------------+----------+--------------+-------------
 id            | integer                     | not null default nextval('lable_id_seq'::regclass) | plain    |              | 
 lable_name      | character varying(500)      | not null                                         | extended |              | 
 update_time   | timestamp without time zone |                                                  | plain    |              | 
 page_num      | integer                     |                                                  | plain    |              | 
 combined_name | character varying(500)      |                                                  | extended |              | 
Indexes:
    "lable_pkey" PRIMARY KEY, btree (id)
    "lable_lable_name_index" btree (lable_name)
    "lable_update_time_index" btree (update_time)
```

EOF