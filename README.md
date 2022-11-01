# icwchain
ICW Migrate your node to new VPS


Download ICW NODE and Update Script + Extract
```
wget http://8.219.130.70:8002/download/ICW_Wallet.tar
wget https://wallet.icwchain.com/update.sh
tar -xvf ICW_Wallet.tar
```
Copy your account folder (make sure your `account` folder on /root directory)
```
\cp -rf /root/account/ /root/ICW_Wallet/data/
```
Update Your Node and Wait for `./check-status` all green (it will stopped automatically)
```
sh update.sh
```
Create new Screen and run ICW Cli
```
screen -R icw
/root/ICW_Wallet/./cmd
```
Check Your Node is Synchronized or Not (on ICW Cli)
```
network info
```
Other Command <br>
See all Wallet that Imported (on ICW Cli)
```
getaccounts
```
