<p align="center">
  <a href="https://imgbb.com/"><img src="https://i.ibb.co/4t9fTLQ/Screenshot-336.jpg" alt="Screenshot-336" border="0"></a>
</p>

# icwchain

## ICW : Migrate your node to new VPS


### Download ICW NODE and Update Script + Extract
```
wget http://8.219.130.70:8002/download/ICW_Wallet.tar
tar -xvf ICW_Wallet.tar
```
### Copy your account folder (make sure your `account` folder on /root directory) *skip this if u still don't have any node
```
\cp -rf /root/account/ /root/ICW_Wallet/data/
```
### Start ICW Node *wait for all status become GREEN
```
/root/ICW_Wallet/./start
/root/ICW_Wallet/./check-status
```
### Start ICW Cli
```
/root/ICW_Wallet/./cmd
```
### Import Account to ICW Node
```
import <youraddress>
```
input your password with your own password on Agent Address And "ICW123456" on Package Address
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
