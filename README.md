# Udacity-Azure-Developer-Learnings
Stores notes on learnings from Udacity Azure Developer program

**January 18, 2021**

**azure cli commands for resource group creation**
```
az account list-locations -o table
az group create --name resource-group-west --location westus2
```

**Azure cli documentation reference**
https://docs.microsoft.com/en-us/cli/azure/

**azure cli commands related to Creating a VM**

Use below command to get public IP of a specific VM

```

```

**January 19, 2021**

**cli commands related to Creating a VM exercise**
```
az vm create \
   --resource-group "resource-group-west" \
   --name "linux-vm-west" \
   --location "westus2" \
   --image "UbuntuLTS" \
   --size "Standard_B1ls" \
   --admin-username "udacityadmin" \
   --generate-ssh-keys \
   --verbose
   
az vm open-port \
    --port "80" \
    --resource-group "resource-group-west" \
    --name "linux-vm-west"   
    
az vm list-ip-addresses -g <RESOURCE-GROUP> -n <VIRTUAL-MACHINE-NAME>
scp -r ./web udacityadmin@IPADDRESS:/home/udacityadmin
ssh [username]@[IP Address]
ls
sudo apt-get -y update && sudo apt-get -y install nginx python3-venv
cd /etc/nginx/sites-available
sudo unlink /etc/nginx/sites-enabled/default
sudo vim reverse-proxy.conf
server {
    listen 80;
    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection keep-alive;
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
 }
 sudo ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/reverse-proxy.conf
 sudo service nginx restart
 
 cd web
 python3 -m venv venv
 source venv/bin/activate
 pip install --upgrade pip
 pip install -r requirements.txt
 python application.py
 
 az group delete -n resource-group-west
```

**cli commands related to Creating a App service exercise**
```
az login
cd web
az webapp up \
 --resource-group resource-group-west \
 --name hello-world1234 \
 --sku F1 \
 --verbose
 az webapp up \
 --name hello-world1234 \
 --verbose
 az group delete -n resource-group-west
 az webapp delete \
    --name hello-world1234 \
    --resource-group resource-group-west
az appservice plan delete \
    --name [App Service Plan Name] \
    --resource-group resource-group-west    
```

**January 209, 2021**
  Completed the project challenge 1
  
**January 21, 2021**

**Create SQL Server**

```
az sql server create \
--admin-user udacityadmin \
--admin-password p@ssword1234 \
--name hello-world-server \
--resource-group resource-group-west \
--location westus2 \
--enable-public-network true \
--verbose
```

**Create Firewall rule**

```
az sql server firewall-rule create \
-g resource-group-west \
-s hello-world-server \
-n azureaccess \
--start-ip-address 0.0.0.0 \
--end-ip-address 0.0.0.0 \
--verbose
```

**Create clientIp firewall rule**

```
az sql server firewall-rule create \
-g resource-group-west \
-s hello-world-server \
-n clientip \
--start-ip-address <PUBLIC-IP-ADDRESS> \
--end-ip-address <PUBLIC_IP_ADDRESS> \
--verbose
```

**Create SQL Database**

```
az sql db create \
--name hello-world-db \
--resource-group resource-group-west \
--server hello-world-server \
--tier Basic \
--verbose
```

**Adding Data** TODO

**Delete DB**

```
az sql db delete \
--name hello-world-db \
--resource-group resource-group-west \
--server hello-world-server \
--verbose
```

**Delete SQL Server**

```
az sql server delete \
--name hello-world-server \
--resource-group resource-group-west \
--verbose
```

