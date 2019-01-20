.. _walletinstall:
.. _Video: https://www.youtube.com/watch?v=0TU044CYfl4/

.. _installnewwallet:

=======================================
Install the Newest Rupaya Core 5 Wallet
=======================================

These instructions are intended for those that are installing the newest Rupaya Core 5 wallet on your personal Windows or Mac computer.

Requirements:
--------------
	+--------------------------------------------------------------------------------------+
	| * Windows 7 or higher, Mac OS, or Linux Ubuntu 16.04/18.04                           |
	| * Outgoing internet access to sync the blockchain and enable the MasterNode remotely | 
	+--------------------------------------------------------------------------------------+

Install the Rupaya Core Wallet
------------------------------

1. Open the following URL in a web browser to download the appropriate wallet version for your system:

	* https://github.com/rupaya-project/rupx/releases

2. Be sure that your existing wallet.dat and private keys are backed up from the old wallet.  We strongly recommend backing up your wallet.dat and private keys prior to starting this process.

	For more instructions, watch this Video_ from a fellow Rupayan, David Coen, on how to export your private keys:

3.Double click the Rupaya file to open and install the new wallet.

	* Accept any pop ups asking to confirm if you want to continue with the installation
	* When prompted, select **Use the default data directory** and click **OK**, unless you previously installed the wallet in a different location, such as the ~/appdata/rupayacore folder.
	+------------------------------------------------+
	|* Mac: ~/Library/Application Support/RupayaCore |
	|*     or ~/Library/Application Support/Rupaya   |
	|* Windows: ~/AppData/Roaming/RupayaCore         |
	|*       or ~/AppData/Roaming/Rupaya             |
	+------------------------------------------------+
	* If prompted by security or antivirus software, click **Allow Always**
	* The new wallet should now open and begin to synchronize with the network


Updating the Wallet Default Settings
------------------------------------

Now that the new wallet is installed, let's take care of updating some very important default wallet settings.  These steps are especially critical if you plan to setup a MasterNode.

Enable Coin Control
-------------------

This feature will allow you to control your wallet inputs, to verify that all coins are consolidated into a single input, to choose which inputs you send coins from, and to optimize staking.

1. Open the Rupaya Wallet and click on **Settings**
2. Select **Options**
3. Click on the **Wallet** tab
4. Click the check-box that says **Enable coin control features**

Disable zRUPX Automint
----------------------

This feature will disable the auto minting of RUPX into zRUPX.

1. Open the Rupaya Wallet and click on **Settings**
2. Select **Options**
3. Click on the **Main** tab
4. Uncheck the check-box that says **Enable zRUPX Automint**
5. Click **OK** to close the wallet options.

	**NOTE: THIS IS A CRITICAL STEP FOR THOSE THAT PLAN TO RUN A MASTERNODE**
	
**Once completed, you can proceed to the next step to install the bootstrap, which will reduce the amount of time it takes to synchronize the wallet with the network.**