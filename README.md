# script_sql_poc
```
CREATE TABLE IF NOT EXISTS public.transaction
(
    trx_id bigint PRIMARY KEY,
    "trx_date" character varying COLLATE pg_catalog."default",
    account_from character varying COLLATE pg_catalog."default",
	amount character varying COLLATE pg_catalog."default",
	"account_to" character varying COLLATE pg_catalog."default",
	"trx_channel" character varying COLLATE pg_catalog."default"
	);
```
```
CREATE TABLE IF NOT EXISTS public.account
(
    account_no bigint PRIMARY KEY,
    "cif" character varying COLLATE pg_catalog."default",
    open_date character varying COLLATE pg_catalog."default"
	);
```
```
CREATE TABLE IF NOT EXISTS public.customers
(
    cif bigint PRIMARY KEY,
    "name" character varying COLLATE pg_catalog."default",
    address character varying COLLATE pg_catalog."default",
	city character varying COLLATE pg_catalog."default",
	type character varying COLLATE pg_catalog."default"
	);
```

### COPY SCRIPT
```
COPY account(cif,account_no,open_date)
FROM '/var/lib/postgresql/12/account.csv'
DELIMITER ';'
CSV HEADER;
```
```
COPY customers(cif,name,address,city,type)
FROM '/var/lib/postgresql/12/cif.csv'
DELIMITER ';'
CSV HEADER;
```
COPY transaction(trx_id,trx_date,account_from,amount,account_to,trx_channel)
FROM '/var/lib/postgresql/12/transaction.csv'
DELIMITER ';'
CSV HEADER;
```

