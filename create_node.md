# This is how to create and configure mqsinode in IBM Integration Bus:

### Create New Node
```sh
mqsicreatebroker NODENAME
```
### List All Nodes
```sh
mqsilist
```
### Check New Node for some errors in configuration
```sh
mqsicvp NODENAME
```
### Set webadministration port for new node
```sh
mqsichangeproperties NODENAME -b webadmin -o HTTPConnector -n port -v 4472
```
### Start node
```sh
mqsistart NODENAME
```
### Create Servers
```sh
mqsicreateexecutiongroup NODENAME -e main -w 90
mqsicreateexecutiongroup NODENAME -e auth -w 90
```
### Set port for Servers
```sh
mqsichangeproperties NODENAME -e main -o HTTPConnector -n explicitlySetPortNumber -v 7806
mqsichangeproperties NODENAME -e auth -o HTTPConnector -n explicitlySetPortNumber -v 7807
```
### Create JDBC Connector for Oracle
```sh
mqsicreateconfigurableservice NODENAME -c JDBCProviders -o NODENAME_BACK_UI -n connectionUrlFormat,connectionUrlFormatAttr1,description,jarsURL,portNumber,serverName,type4DatasourceClassName,type4DriverClassName -v "jdbc:oracle:thin:[user]/[password]@[serverName]:[portNumber]:[connectionUrlFormatAttr1],ldb,Simplified Database Routing Sample Database,/home/oracle/app/oracle/product/12.1.0/client_1/jdbc/lib/,oracle_port,oracle_ip,oracle.jdbc.xa.client.OracleXADataSource,oracle.jdbc.OracleDriver"
```
### Create SecurityIdentity or Change username/password:
```sh
mqsisetdbparms NODENAME -n jdbc::authNODENAMEtest -u oracleuser -p oraclepass
```
### Set SI to JDBC Provider:
```sh
mqsichangeproperties NODENAME -c JDBCProviders -o NODENAME_BACK_UI -n securityIdentity -v uiNODENAMEtest
mqsichangeproperties NODENAME -c JDBCProviders -o NODENAME_BACK_AUTH -n securityIdentity -v authNODENAMEtest
```
### List All parameter of Node
```sh
mqsireportproperties NODENAME-c AllTypes -o AllReportableEntityNames -r
```
### Check username/password of SI
```sh
mqsireportdbparms NODENAME -n jdbc::uizeus4jtest -u back_ui -p oracle
```
### View username of SI
```sh
mqsireportdbparms NODENAME -n jdbc::uizeus4jtest
```
### Details of BIP message
```sh
mqsiservice -m 4367
```
