az sql server create \
	--name server-p20rps \
	--resource-group p20rps \
	--location eastus  \
	--admin-user AdminUser \
	--admin-password ChangeYoPassword2

# Create Fire wall Rule
    az sql server firewall-rule create \
	--resource-group p20rps \
	--server server-p20rps \
	-n AllowYourIp \
	--start-ip-address 23.96.126.64 \
	--end-ip-address 23.96.126.64
  
# Create a database in the server with zone redundancy as true
az sql db create \
	--resource-group myResourceGroup \
	--server $servername \
	--name mySampleDatabase \
	--sample-name AdventureWorksLT \
	--service-objective S0 \
	--zone-redundant

# Update database and set zone redundancy as false
az sql db update \
	--resource-group myResourceGroup \
	--server $servername \
	--name mySampleDatabase \
	--zone-redundant false
    Server=tcp:server-p20rps.database.windows.net,1433;Initial Catalog=p20rpsdb;Persist Security Info=False;User ID={your_username};Password={your_password};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;
