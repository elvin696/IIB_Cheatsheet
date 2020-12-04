# Password with special characters in IBM Integration Bus.
### If you configure JDBCProvider for oracle and password for your user has a special character follow this article, because documentation is little bit lie.

Quote from documentation:

>If you specify a password by using the -p Password parameter and the password includes characters that have special meaning to the command shell, you must use quotation marks around the password or escape the characters. Use single quotation marks on Linux and UNIX systems. Use double quotation marks on Windows systems. For a full list of reserved characters, and the rules that are associated with those characters when you use quotation marks and escape characters, see the documentation that is supplied with the shell.
>However, you can avoid the need to use quotation marks or to escape special characters if you omit to specify a password by using the -p Password parameter when you run the command. You are prompted to enter a password during the invocation of the command, and to enter the password a second time to verify that you have entered it correctly. The password that you specify after being prompted can include characters that have special meaning to the command shell with no need for you to use quotation marks or to escape these characters.

For connection from linux to oracle use this command:

```sh
mqsisetdbparms NODENAME -n jdbc::SINAME -u username -p '"P@$$Word!@#"'
```

For connection from linux to MSSQL use single quotation:

```sh
mqsisetdbparms NODENAME -n jdbc::SINAME -u username -p 'P@$$Word!@#'
```