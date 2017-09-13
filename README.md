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
sysctl -w fs.file-max=65536
