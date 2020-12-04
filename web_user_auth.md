# How to enable web-interface user authentication for IBM Integration Bus.
### As an iib admin, if you need to disable access for everyone into web-interface, you need to follow this article.

First of all, stop the instance and run the command:

```sh
mqsistop NODENAME
mqsichangeauthmode NODENAME -s active -m file
```

Start the node and run:
```sh
mqsistart NODENAME
mqsichangefileauth NODENAME -r iibAdmins -p all+
```

And create user:
```sh
mqsiwebuseradmin NODENAME -c -u username -a password -r root
```