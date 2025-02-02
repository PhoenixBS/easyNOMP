## Pool Installation Instructions

-------

### Installer Script
You know we like things easy, so we've created this handy installer script for you!
Please be aware, this script is not yet tested, and may not even work!
Simply create a user for the pool to run as, and log in to that user.
Run this command

```
# Please be careful, this script may or may not work :P
# Manual install preferable.
#
git clone https://github.com/EasyX-Community/EasyNOMP.git ; cd EasyNOMP ; ./install.sh ;
```
**Done!**

-------
### Install Requirements
```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
sudo apt-get install -y sudo git nano wget curl build-essential libtool autotools-dev autoconf pkg-config libssl-dev libboost-all-dev git npm nodejs libminiupnpc-dev redis-server software-properties-common 
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install libdb4.8-dev libdb4.8++-dev

wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
source ~/.bashrc
nvm install 8
nvm use 8
npm update -g
npm install -g pm2@4.2.0
npm install -g npm@6.13.4
```

-------
### Flush Redis Data
**If you are switching from z-nomp, your old statistics and payouts data is incompatable - to wipe it please run:**
```
redis-cli FLUSHALL
```
**WARNING: You will loose statistics and payout data.**

-------
### Install Pool
```
git clone https://github.com/PhoenixBS/EasyNOMP.git
cd EasyNOMP
npm install
npm update
npm audit fix
./pool-start.sh
```

-------
### Watching Pool Logs
```
./pool-logs-watch.sh # Watch regular logs

./pool-logs-watch.sh " BTCADDRESSTOSCANFOR " # Scan for a coin address

./pool-logs-watch.sh "block>accepted>" # Scan for accepted blocks

./pool-logs-watch.sh "block>rejected>" # Scan for a rejected blocks

./pool-logs-watch.sh "share>accepted>" # Scan for accepted shares

./pool-logs-watch.sh "share>rejected>" # Scan for rejected shares

./pool-logs-watch.sh "DIFFICULTY>" # Scan for difficulty updates
```

-------
### Restarting Pool
```
./pool-restart
```

-------
### Startup on Boot
```
pm2 startup
```
Copy & paste the command (if it asks you to)<br />
Save the process list
```
pm2 save
```

-------
### Update Pool Source (should be done monthly at minimum)
```
cd EasyNOMP
git pull
rm -rf node_modules
npm update -g
npm update -g npm
npm install
npm audit fix
./pool-restart.sh
```

***EOF***
