<h1> JDBC Interpreter </h1>

ZEPL supports JDBC interpreter with drivers for popular databases. To connect your database, it's important to check

  - Database is currently up and running
  - Database is accessible from public internet
  - You have proper credentials to access database

## Create new JDBC Interpreter

First, you'll need to create an intepreter to provide database connection information.

1. Click **Create interpreter** button from [Interpreter](https://www.zepl.com/settings/interpreters) page.
2. Select **jdbc** in Interprer group
3. Type **Interpreter name**. This name will be used in the notebook to call this JDBC interpreter.
4. Type **JDBC connection URL**, **username** and **password**.
5. Select **JDBC driver**

You can use **Test connection** button to test connection.

### Use your JDBC Interpreter

Once you have created JDBC interpreter, you can call it in the notebook using `%[Interpreter name]` directive. For example if you have created your JDBC interpreter with name "psql", you can call it `%psql` in the notebook. i.e.

```
%psql
SELECT * from my_table
```

## Secure database connection

### Whitelist IP addresses
ZEPL connects your database using two IP addresses **52.38.31.66** and **52.32.218.160**. It's always good idea setup firewall and whitelist the IP.


