<h1> JDBC Interpreter </h1>

ZEPL supports JDBC interpreter with drivers for popular databases. Before connecting to your database, it's important to check the following:

  - Database is currently up and running
  - Database is accessible from public internet
  - You have proper credentials to access database

## Create new JDBC Interpreter

First, you'll need to create an intepreter to provide database connection information.

1. Click **Create interpreter** button from [Interpreter](https://www.zepl.com/settings/interpreters) page.
2. Select **jdbc** in Interpreter group
3. Provide an **Interpreter name**. This name will be used in the notebook to call this JDBC interpreter.
4. Provide a **JDBC connection URL**, **username** and **password**.
5. Select a **JDBC driver**

Use the **Test connection** button to test the connection.

### Use your JDBC Interpreter

Once you have created the JDBC interpreter, you can use it in your notebook by providing the `%[Interpreter name]` directive. For example, if you have created your JDBC interpreter with name "psql", you can use `%psql` in the notebook. i.e.

```
%psql
SELECT * from my_table
```

## Secure database connection

### Whitelist IP addresses
ZEPL connects your database using two IP addresses **52.38.31.66** and **52.32.218.160**. It's recommended to setup firewall and whitelist the IP.

## Connecting to a database in private network with an SSH tunnel

To connect to a database in a private network, create an SSH tunnel using the following steps:

### Create a new JDBC interpreter
* Go to ZEPL Interpreters page and click **Create interpreter**.
* Select **JDBC** from the **Interpreter group**.
* Check **SSH tunnel ON/OFF**.

<img src="../../../img/jdbc_tunnel.png" class="image-box big-img" />

### Setup the public key
* Download our public key from the popup and whitelist **52.38.31.66**
and **52.32.218.160** through your firewall.

* Create a user account for ZEPL:

```
ubuntu@user:~$ sudo useradd zepl
```
* Since ZEPL authenticates via public key, there's no need to set a password.
Authorize the key by opening up `zepl.rsa.pub`(the downloaded file)
and pasting its contents into a new line in `/home/user/.ssh/authorized_keys`.

* In most cases the SSH Port will be default 22. Check the Port variable in
`/etc/ssh/sshd_config` to see which port is used for SSH.

```
ubuntu@user:~$ cat /etc/ssh/sshd_config | grep Port
Port 22
```

Now you can use your newly created interpreter with your notebooks
to query and process data.
