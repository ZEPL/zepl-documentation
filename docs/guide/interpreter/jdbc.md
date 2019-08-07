title: JDBC Database Interpreter | Zepl Documentation
description: Zepl supports a JDBC interpreter with drivers for popular databases, including Mysql, Oracle, and Redshift. Learn more about our JDBC database interpreter. 

# JDBC Interpreter

Zepl supports a JDBC interpreter with drivers for popular databases. Drivers for the following databases are currently supported by Zepl:

  - Mysql
  - Oracle
  - Postgresql
  - Redshift

For additional database connections, please contact [support@zepl.com](mailto:support@zepl.com).

Before connecting to your database, it's important to check the following:

  - the database is currently up and running
  - the database is accessible from the public internet
  - you have the proper credentials to access the database

## Creating a New JDBC Interpreter

First you'll need to create an interpreter to provide the database connection information as follows:

1. Click the *Create interpreter* button from the Interpreter settings page
2. Select *jdbc* from the *Interpreter type* group
3. Provide a name for your interpreter (note that this name will be used in the notebook to call this JDBC interpreter)
4. Provide the JDBC connection URL, username and password
5. Select a JDBC driver from the dropdown menu

Use the *Test connection* button to test the connection.

### Using Your JDBC Database Interpreter

Once you have created the JDBC interpreter, you can use it in your notebook by providing the `%[Interpreter name]` directive. For example, if you have created your JDBC interpreter with name "psql", you can use `%psql` in the notebook as follows:

```
%psql
SELECT * from my_table
```

## Secure Database Connections

### Whitelist IP Addresses

Zepl connects to your database using the IP addresses below so you'll need to whitelist them in your firewall:

- 35.164.138.115
- 52.24.205.101
- 34.214.146.198

### SSH Tunneling for Private Networks

To connect to a database in a private network, create an SSH tunnel using the following steps:

#### - Create a New JDBC Interpreter

* Go to the *Interpreters* page and click *Create interpreter*
* Select *JDBC* from the *Interpreter type*
* Enable SSH tunneling in the *JDBC driver* area

<img src="../../../img/jdbc_tunnel.png" class="image-box img-70" />

#### - Setup the Public Key

1. Download our public key using the *Download* button and whitelist the IP addresses listed above through your firewall.

2. Create a user account for Zepl

  ```sh
  ubuntu@user:~$ sudo useradd zepl
  ```

3. Since Zepl authenticates via public key, there's no need to set a password. Authorize the key by opening up `default.ssh.public_key` (the downloaded file)
and pasting its contents into a new line in `/home/zepl/.ssh/authorized_keys`.
Make sure the `authorized_keys` file has `600` permission.

4. In most cases the SSH Port will be 22 by default. Check the *Port* variable in
`/etc/ssh/sshd_config` to see which port is used for SSH.

  ```sh
  ubuntu@user:~$ cat /etc/ssh/sshd_config | grep Port
  Port 22
  ```

Now you can use your newly created JDBC interpreter with your notebooks
to query and process data.
