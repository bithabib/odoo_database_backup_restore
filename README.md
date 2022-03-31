# Odoo Database Backup Restore

### 1. Take Backup of Database 
1. Open terminal 
2. Goto your postgres user
```
sudo su - postgres
```
3. Goto psql server
```
psql
```
4. Check list of database you have
```
\l
```
5. Came back to the psql server and Dump the desired database
```
pg_dump database_name > database_name_20160527.sql
```

### 2. Now take backup of filestore 

1. Goto the filestore folder using cd 

```
cd /path/to/your/filestore
cd /odoo18/.local/share/Odoo/filestore
```

2. Convert your desired folder to zip (Please zip the that match with your database name)

```
sudo apt install zip unzip
zip -r filename.zip folder
```
