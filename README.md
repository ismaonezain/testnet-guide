<p align="center">
  <a href="https://imgbb.com/"><img src="https://i.ibb.co/4t9fTLQ/Screenshot-336.jpg" alt="Screenshot-336" border="0"></a>
</p>

# icwchain

## ICW : Migrate your node to new VPS


### Download ICW NODE and Update Script + Extract
```
wget http://8.219.130.70:8002/download/ICW_Wallet.tar
wget https://wallet.icwchain.com/update.sh
tar -xvf ICW_Wallet.tar
```
### Copy your account folder (make sure your `account` folder on /root directory)
```
\cp -rf /root/account/ /root/ICW_Wallet/data/
```
### Update Your Node and Wait for `./check-status` all green (it will stopped automatically)
```
sh update.sh
```
### Run ICW Cli
```
/root/ICW_Wallet/./cmd
```
### Check Your Node is Synchronized or Not (on ICW Cli)
```
network info
```
You can close ICW Cli with `CTRL + C`
## Other Command <br>
### See all Wallet that Imported (on ICW Cli)
```
getaccounts
```
