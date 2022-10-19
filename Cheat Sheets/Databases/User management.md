## MySQL / MariaDB

### Creating a user
---
To be able to make any changes to tables, you have to have a user.

It is not recommended to use the root user for everything, due to the least priviliges principle. The user should only be able to do the operations necessary to complete his work.

For example, a user that is used on the server, should only have 'write' and 'read' permission to prevent any SQL injection table drop etc.

The command to create a user is:
``` sql
CREATE USER 'username'@'host' IDENTIFIED WITH authentication_plugin BY 'password';
```

The `authentication_plugin` can be left out or changed depending on the encryption of the password, if left blank the default is `caching_sha2_password` which doesn't permit remote access.

You can set it as `mysql-native-password` for remote access. Also, you can find more information [here](https://dev.mysql.com/doc/refman/8.0/en/authentication-plugins.html).

You can also alter users by using the command:
``` sql
ALTER USER 'username'@'host' IDENTIFIED WITH authentiction_plugin BY 'password';
```

### Granting priviliges
---
To make sure that a user can only have the necessary priviliges.

To grant priviliges you can use the following command:
``` sql
GRANT PRIVILEGE ON database.table TO 'username'@'host';
```

Here you will have to replace `PRIVILEGE` with a list of the privileges you want to add, for example:
``` sql
GRANT CREATE, ALTER, DROP, INSERT, UPDATE, DELETE, SELECT, REFERENCES, RELOAD on *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
```

Some useful priviliges might be:
- `ALTER`
- `CREATE`
- `DELETE`
- `INSERT`
- `SELECT`
You can find a list with all the privileges [here](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html).

You can create a super-user account using the command:
``` sql
GRANT ALL PRIVILEGES ON *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
```

To revoke a privilege the syntax is almost the same, you just have to replace the `GRANT` with `REVOKE`.

Make sure to flush the privileges after making a user, or granting, to make sure they take effect immediately:
``` sql
FLUSH PRIVILEGES;
```

### Other operations

Show grants:
``` sql
SHOW GRANTS FOR 'username'@'host';
```

Delete user:
``` sql
DROP USER 'username'@'localhost';
```