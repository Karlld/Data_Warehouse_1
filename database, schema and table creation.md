**Creating the Database and schemas**

```sql
DROP DATABASE IF EXISTS DataWarehouse_1;

CREATE DATABASE DataWarehouse_1;

CREATE SCHEMA raw; 

CREATE SCHEMA stage;

CREATE SCHEMA business;
```

```SQL
DO $$
BEGIN
    IF NOT EXISTS (SELECT 1 FROM raw.crm_cust_info) THEN
        EXECUTE 'DROP TABLE raw.crm_cust_info';
    END IF;
END $$;

CREATE TABLE raw.crm_cust_info(
    cst_id INT,
    cst_key VARCHAR(50),
    cst_firstname VARCHAR(50),
    cst_lastname VARCHAR(50),
    cst_material_status VARCHAR(50),
    cst_gndr VARCHAR(50),
    cst_create_date DATE
);

DO $$
BEGIN
    IF NOT EXISTS (SELECT 1 FROM raw.crm_prd_info) THEN
        EXECUTE 'DROP TABLE raw.crm_prd_info';
    END IF;
END $$;

CREATE TABLE raw.crm_prd_info(
    prd_id INT,
    prd_key VARCHAR(50),
    prd_nm VARCHAR(50),
    prd_cost INT,
    prd_line VARCHAR(50),
    prd_start_dt DATE,
    prd_end_dt DATE
);

DO $$
BEGIN
    IF NOT EXISTS (SELECT 1 FROM raw.crm_sales_details) THEN
        EXECUTE 'DROP TABLE raw.crm_sales_details';
    END IF;
END $$;

CREATE TABLE raw.crm_sales_details(
   sls_ord_num VARCHAR(50),
   sls_prd_key VARCHAR(50),
   sls_cust_id INT,
   sls_order_dt INT,
   sls_ship_dt INT,
   sls_due_dt INT,
   sls_sales INT,
   sls_quantity INT,
   sls_price INT
);

DO $$
BEGIN
    IF NOT EXISTS (SELECT 1 FROM raw.erp_cust_az12) THEN
        EXECUTE 'DROP TABLE raw.erp_cust_az12';
    END IF;
END $$;

CREATE TABLE raw.erp_cust_az12(
    cid VARCHAR(50),
    bdate DATE,
    gen VARCHAR(50)
);

DO $$
BEGIN
    IF NOT EXISTS (SELECT 1 FROM raw.erp_loc_a101) THEN
        EXECUTE 'DROP TABLE raw.erp_loc_a101';
    END IF;
END $$;

CREATE TABLE raw.erp_loc_a101(
    cid VARCHAR(50),
    cntry VARCHAR(50)
);


DO $$
BEGIN
    IF NOT EXISTS (SELECT 1 FROM raw.erp_px_cat_g1v2) THEN
        EXECUTE 'DROP TABLE raw.erp_px_cat_g1v2';
    END IF;
END $$;


CREATE TABLE raw.erp_px_cat_g1v2(
    id VARCHAR(50),
    cat VARCHAR(50),
    subcat VARCHAR(50),
    maintenance VARCHAR(50)
);
```  
