# Denied-Schema-Public
# Summary
The error "permission denied for schema public" occurs when a user or role does not have the necessary permissions to perform an action on the "public" schema.
# Causes
* The user or role does not have the USAGE privilege on the "public" schema. This means they cannot access any objects in the schema.
* The user or role does not have the SELECT privilege on a specific table in the "public" schema. This means they cannot query that table.
* The user or role does not have the EXECUTE privilege on a specific function or procedure in the "public" schema. This means they cannot execute that function or  procedure.
* The user or role does not have the CONNECT privilege on the database. This means they cannot connect to the database at all.
# Solutions
* To resolve this error, you need to identify the specific cause and grant the appropriate permissions to the user or role.

## Cấp Quyền CHo Role
* Grant USAGE privilege on the "public" schema: 
- sql 
    GRANT USAGE ON SCHEMA public TO your_role;

* Grant SELECT privilege on the "mytable" table:
- sql 
    GRANT SELECT ON TABLE public.mytable TO your_role;

* Grant EXECUTE privilege on the "myfunction" function:
- sql 
    GRANT EXECUTE ON FUNCTION public.myfunction TO your_role;

* Grant CONNECT privilege on the database:
- sql 
    GRANT CONNECT ON DATABASE mydatabase TO your_role;

# ** How to create 1 role(user) in postgres ** 
## Create role
* sqlCREATE ROLE your_role_name WITH LOGIN; 
- in case you want add password you can change cmd to 
* sql 
CREATE ROLE your_role_name WITH LOGIN PASSWORD 'your_password';
