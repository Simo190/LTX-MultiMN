# LTX-MultiMN
LTX MultiMasternode 1 VPS

Shell script to install a [LITEX Masternode](https://ltxcoin.info) on a Linux server running Ubuntu 16.04. Use it on your own risk.


Type this command in your VPS

wget https://raw.githubusercontent.com/Simo190/LTX-MultiMN/master/install.sh && chmod 777 bash install.sh 

./install.sh

I recommend installing the node verification monitor


At the time of installation in the VPS it is necessary to have generated as many private keys as the daemon you want to install. See point 2 Windows Wallet below

Once the nodes have been installed, if the blocks still remain at 0 to verify Alias_getinfo you can add nodes to all the ltx.conf files present in all the folders .ltx_Alias

These are the commands to enter the relevant folders

From root
Alias_stop [off the daemnon]
cd .ltx_Alias [enter the relative folder]
nano ltx.conf [edit the ltx.conf file]

This is the line to past in you ltx.conf

addnode=80.211.7.32:17991

addnode=206.189.72.106:17991

addnode=144.202.8.79:17991

addnode=178.238.237.136:17991

addnode=185.174.173.192:17991

addnode=207.148.77.127:17991

addnode=138.68.16.124:17991

addnode=45.76.106.102:17991

addnode=174.138.7.128:17991

addnode=159.89.158.129:17991


Pasted the nodes press control + O and then send control + X [save and exit]

Added all the nodes to all the daemons installed to restart all daemons

Alias_start [start the daemon]

## Windows wallet

1. Launch your local wallet
2. Go to debug console (Tools - Debug Console) and enter the following command (one for each installed daemon):

> `masternode genkey` *save the result (masternode_privkey)*

3. Enter the following command (one for each installed daemon): 

> `getaccountaddress MN1` *you will get new Masternode wallet address. Use like MN1 or other to better remeber and check your Masternode*

4. Send 10,000 LTX to Masternode wallet address.
5. Enter the following command (one for each transaction): 

> `masternode outputs` output_txid

6. Open your masternode.conf file (Tools - Open Masternode Configuration file) and add the following line (port=17991):

> `MN_ALIAS VPS_IP:port masternode_privkey output_txid output_index`

## Local wallet when the VPS ended the syncro

1. Reopen you local wallet
2. Go to Debug Console and run your masternode:

> `walletpassphrase YourPassword 360` *If you have encrypted your wallet - 360 the time in seconds in which the wallet will be unlocked*

> `masternode start-alias MN1 <MN_ALIAS>` *You should see something like this: { "alias" : "MN1", "result" : "successful" }*

> `masternode start-alias false MN1 <MN_ALIAS>` (If you have encrypted you wallet) *You should see something like this: { "alias" : "MN1", "result" : "successful" }*






