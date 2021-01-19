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
