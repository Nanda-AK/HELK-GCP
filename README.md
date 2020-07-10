# HELK-GCP
Installing HELK on GCP platform (Below steps works good on AWS Also) 

Below is the Details steps to install for HELK on Google Could Platfrom. 

Step1:- Creat VM Instance on GCP with below specifications 
a) Machine Configuration
    Series N1 (Minimum) 
    Machine Type: n1-standard-4
    
b) Boot Disk
   Ubuntu 18.04 LTS  
   Boot Disk Size 30GB or more 

c) Firewall, Http/Https


Step 2:-  After VM come up
SSH to the VM 
a) sudo mkdir /opt/mdt
    
b) sudo chown -R $(whoami):root /opt/mdt
    
c) cd /opt/mdt/

d)  wget http://archive.ubuntu.com/ubuntu/pool/main/o/openssl1.0/libssl1.0.0_1.0.2n-1ubuntu5.3_amd64.deb
    
e)  sudo dpkg -i libssl1.0.0_1.0.2n-1ubuntu5.3_amd64.deb
      
f)  sudo apt-get update
   
g)  sudo apt-get -y install git kafkacat dnsutils netcat
   
h)  git clone https://github.com/Cyb3rWard0g/HELK.git
   
j)  cd HELK/docker/
      
k)  HELK_IP=$(hostname -i)                #this will work on ubuntu only 

l)  sudo ./helk_install.sh -p hunting -i $HELK_IP -b helk-kibana-notebook-analysis -l basic
	
m) tail -f /var/log/helk-install.log 
   (it will start the installing using script, so to check open new terminal and perform below commands:) 

Output of the l) is 

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
***********************************************************************************
** [HELK-INSTALLATION-INFO] HELK WAS INSTALLED SUCCESSFULLY                      **
** [HELK-INSTALLATION-INFO] USE THE FOLLOWING SETTINGS TO INTERACT WITH THE HELK **
***********************************************************************************
 
HELK KIBANA URL: https://10.128.0.11
HELK KIBANA USER: helk
HELK KIBANA PASSWORD: hunting
HELK SPARK MASTER UI: https://10.128.0.11:8080
HELK JUPYTER SERVER URL: https://10.128.0.11/jupyter
HELK JUPYTER CURRENT TOKEN: 65b293dc55600812acba5b6fd9446401c57465df67d7b6fa
HELK ZOOKEEPER: 10.128.0.11:2181
HELK KSQL SERVER: 10.128.0.11:8088
 
IT IS HUNTING SEASON!!!!!
 
You can stop all the HELK docker containers by running the following command:
 [+] sudo docker-compose -f helk-kibana-notebook-analysis-basic.yml stop

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::


