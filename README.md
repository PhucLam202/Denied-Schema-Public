# Denied-Schema-Public
1. [overview](#overview)
2. [troubleshooting](#causes)
    1.  [causes](#causes)
    2.  [solutions](#solutions)  
3. [flowworking](#flowworking)

## Overview
The error "permission denied for schema public" occurs when a user or role does not have the necessary permissions to perform an action on the "public" schema.

## Causes
* Normally, after allowing a user to CREATE tables within a database, you didn't have to specifically define that they had the permission to do that within a SCHEMA, since public would be the default one.
* The user or role does not have the CONNECT privilege on the database. This means they cannot connect to the database at all.


### Solutions
* To resolve this error, you need to identify the specific cause and grant the appropriate permissions to the user or role.
* For example your need to add PRIVILEGES from Role to correct database
- Grant USAGE privilege on the "public" schema:
  
> [!NOTE]
> Make you following all this step

> [!TIP]
> If you do 4 first step just jumb to step 5

### FlowWorking 
1. **Create Role**
```bash
 CREATE ROLE your_role_name WITH LOGIN; 
```
- `in case you want add password you can change cmd to` 
```bash 
CREATE ROLE your_role_name WITH LOGIN PASSWORD 'your_password';
```
2. **Create DataBase**
```bash 
CREATE DATABASE your_database_name ;
```
3. **Grant All Full Access `All Privileges` From Role(User) to Database** 
```bash 
GRANT ALL PRIVILEGES ON DATABASE your_database_name TO your_role;
```
4. **Now you need to connet with your database with cmd `\c` or `\connect `**
```bash 
\c your_database_name
```
5. **Grant Schema Public From `Your Database` to `Your Role`** 
```bash 
GRANT ALL ON SCHEMA public TO your_role_name ;
```
`AFTER THIS YOUR CAN RUN YOUR CMD AGAIN TO SEE THE MAGIC` 

### ** Some Option ** 
1. 
```bash
    GRANT USAGE ON SCHEMA public TO your_role;
```
2. **Grant SELECT privilege on the "mytable" table:**
```bash   
 GRANT SELECT ON TABLE public.mytable TO your_role;
```
3. **Grant EXECUTE privilege on the "myfunction" function:**
```bash
    GRANT EXECUTE ON FUNCTION public.myfunction TO your_role;
```
4. **Grant CONNECT privilege on the database:**
```bash 
    GRANT CONNECT ON DATABASE mydatabase TO your_role;
```
