docker run -it ubuntu:14.04  
apt-get update  
apt-get install curl vim  
cd root  
curl -o bootstrap-salt.sh -L https://bootstrap.saltstack.com  
sh bootstrap-salt.sh stable  
/etc/init.d/salt-minion status  
/etc/init.d/salt-minion start  
/etc/init.d/salt-minion status  
mkdir -p /srv/salt  
cd !$  
vi top.sls // без tuning пока  
vi graphite.sls  
salt-call --local state.apply  
dpkg -l | grep graphite  
vi top.sls // добавим tuning  
sysctl -a | grep file-max  
vi tuning.sls  
salt-call --local state.apply  
sysctl -w fs.file-max=500000  


curl -o bootstrap-salt.sh -L https://bootstrap.saltstack.com  
sudo sh bootstrap-salt.sh -M stable  
sudo vim /etc/salt/minion  
sudo service salt-minion restart  
sudo mkdir -p /srv/salt  
cd !$  
sudo vim top.sls  
sudo vim graphite.sls  
sudo vim tuning.sls  
sudo salt-call state.highstate  
sudo salt-key -L  
sudo salt-key -A  
sudo salt-call state.highstate  
sudo salt '*' test.ping  
sudo vim graphite.sls // add carbon cache so this service will be running after reboot  
sudo salt '*' state.highstate  
  
  
curl -o bootstrap-salt.sh -L https://bootstrap.saltstack.com  
sudo sh bootstrap-salt.sh stable  

