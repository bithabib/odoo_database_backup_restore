# Odoo Database Backup Restore
### Take backup of all the custom modules
1. Goto you custom module folder
```
cd /path/to/your/custom/modules
Example:
cd /odoo18/custom
```
2. Convert your desired folder to zip

```
sudo apt install zip unzip
zip -r filename.zip folder
```

### 1. Take Backup of Database 
1. Goto server using ssh 
```
ssh user@ip
```
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
Example:
cd /odoo18/.local/share/Odoo/filestore
```

2. Convert your desired folder to zip (Please zip the that match with your database name)

```
sudo apt install zip unzip
zip -r filename.zip folder
```
## You are done with taking Backup of your databse its time to upload


### 1. Upload filestore and dumped.sql file
1. Use FileZilla for uploading zipped filestore and dumped.sql file
2. Goto the server where you want to restore using ssh 
```
ssh user@ip
```
3. Goto the folder you have uploaded zip and sql file using cd 
```
cd /path/to/your/zip/and/sql/file
Example:
cd /odoo
```
### Unzip filestore and move to specific folder
1. Unzip the filestore 
```
unzip filename.zip
Example:
unzip production.zip
```
2. Move the file to filestore 
```
sudo mv unzipped_folder_name/ /path/to/your/filestore
Example
sudo mv filestore/ /odoo/.local/share/Odoo/filestore
```

### Now creating the database and uload psql file 
1. Goto server using ssh 
```
ssh user@ip
```
2. Goto your postgres user
```
sudo su - postgres
```
3. Goto the folder you have sql file 
```
cd /path/to/your/uploaded/sql/file
Example
cd /odoo
```
4. Create Database and Upload 
```
createdb -O db_user dbname
Example:
createdb -O odoo Sakan.live
psql db_name < sql_file_you_want_to_upload
Example:
psql Sakan.live < sakan.sql
```

## Its Time to Setup PDF Report

1. Go to settings > Technical > Parameters > System parameters
2. Make a new paramater
a. Name: web.base.url.freeze
b. Value: True
3. Edit the parameter web base.url and place the ip on http://0.0.0.0:8069
4. Refresh and everything is fixed.
### Still you may face some problem to show image if yes here is the solution 
```
sudo wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb
sudo dpkg -i wkhtmltox_0.12.5-1.bionic_amd64.deb
sudo apt install -f
```
# You are Done


Another is comming

