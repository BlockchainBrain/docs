.. _unlockmncoins:

===================================
Unlock all of your Masternode coins
===================================

These instructions are intended for those that are running a MasterNode on a Linux VPS and are managing it using a Cold wallet.  These instructions will walk you through the steps to unlock all of your MasterNode coins so they are no longer locked.

1. Open your current Rupaya wallet that is the MasterNode Cold Wallet

2. Select **Tools > Open Masternode Configuration File**

3. Insert a **#** symbol in front of each of the lines in your configuration file.  This will remark out those lines so that the wallet will no longer lock the funds for those Masternodes, once a wallet restart has been completed.

	* Alternatively, you can just rename the masternode.conf file to something like masternode.bak.

4. Close your Rupaya wallet and then open it back up again and the funds should now be unlocked.