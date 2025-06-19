***Naming Conventions***

```
General naming convention: snake_case
Language: English
```



**Table Naming Conventions**



**Raw Layer Rules**

```
<sourcesystem>_<entity>
```

```
<sourcesystem>: The name of the system (e.g. crm, erp)

<entity>: The exact table name from the source
```
```
For example: crm_cust_info - Customer information from the crm source.
```
Stage Layer Rules

```
<sourcesystem>_<entity>
```
```
<sourcesystem>: The name of the system (e.g. crm, erp)

<entity>: The exact table name from the source
```
```
For example: crm_cust_info - Customer information from the crm source
```

**Business Layer Rules**

```
<category>_<entity>
```
```
<category>: Description of the table role e.g. dim_, fact_, agg_)

<entity>: Description of the table aligned with the business domain (products, sales, customers)
```
```
For example: dim_customers - Dimension table for customer information.
```
| Pattern |   Explanation |  Examples |
|---------|---------------|-----------|
| dim_ |  Dimension table |   dim_customers |
| fact_ |  Fact table   |   fact_sales |
| agg_  |  Aggregated table | agg_sales_quarterly |



**Column Naming Conventions**



**Surrogate Keys**

```
<table_name>_key
```
```
<table_name>: The name of the table

_key: A suffix indicating the column is a primary key
```
```
For example: customer_key
```


**Technical Columns**

```
dwh1_<column_name>
```
```
dwh1_: A prefix used for all system generated metadata

<column_name>: The name of the column
```
```
For example: dwh1_load_date
```


**Stored Procedures**

```
load_<layer>
```
```
load_: The name of the procedure

<layer>: indicates which layer is being used in the procedure
```
```
For example: load_raw - The stored procedure for loading data into the raw layer.
```
