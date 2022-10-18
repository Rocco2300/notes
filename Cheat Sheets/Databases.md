## MySQL / MariaDB

### How to host the server
---

This is the easy part, if you have the luck of not encountering an error.

You can just start the server using the following command in cmd/pwsh: 

``` cmd
mysqld
```

After that check that the process is running in task manager.

If it is running, yay, you are done, if not, then you have to launch it manually from Services. You have to open a command prompt, and enter the command:

``` cmd
services.msc
```

In this app, you will have to find the service MySQL80 and launch it, and then check in the task manager that it works.

### Hosting server on Win with client on Linux (WSL)
---

To connect to the server, the host provided to MySQL/MariaDB client should be the hostname, which can be found with the following command, ran in wsl:

``` bash
hostname -i
```

This command will return the ip: `127.0.1.1`

Take care, localhost won't work as a host for the client, so the command to launch the client becomes:

``` bash
mysql -h 127.0.1.1 -u <user> -p
```

