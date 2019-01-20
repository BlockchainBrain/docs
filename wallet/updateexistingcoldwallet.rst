.. _updateexistingcoldwallet:

=========================================
Update an Existing MasterNode Cold Wallet
=========================================

These instructions are intended for those that were already running a MasterNode Cold wallet and want to update the wallet to the newest version.  

Install the Rupaya Core Wallet
------------------------------

1. Open the following URL in a web browser to download the appropriate wallet version for your system:

	* https://github.com/rupaya-project/rupx/releases

2. Be sure that your existing wallet.dat and private keys are backed up from the old wallet.  We strongly recommend backing up your wallet.dat and private keys prior to starting this process.

	For more instructions, watch this Video_ from a fellow Rupayan, David Coen, on how to export your private keys:

3. Close the Rupaya wallet.

4. Double click the Rupaya file to open and install the new wallet.

	* Accept any pop ups asking to confirm if you want to continue with the installation
	* When prompted, select **Use the default data directory** and click **OK**, unless you previously installed the wallet in a different location, such as the **rupayacore** folder.
	+------------------------------------------------+
	|* Mac: ~/Library/Application Support/RupayaCore |
	|*     or ~/Library/Application Support/Rupaya   |
	|* Windows: ~/AppData/Roaming/RupayaCore         |
	|*       or ~/AppData/Roaming/Rupaya             |
	+------------------------------------------------+
	* If prompted by security or antivirus software, click **Allow Always**
	* The new wallet should now open and begin to synchronize with the network


Start the MN from the Cold Wallet
------------------------------------

.. warning:: It is very important that you let the MasterNode Hot wallet synchronize for a couple of hours prior to starting it from the Cold wallet.  If you attempt to start it before it isfully synchronized then it will fail.  Both the Cold and Hot wallets need to be on same version/protocol to activate the MasterNode.

**NOTE:** If you can update and restart your MasterNode within 1 hour, then it won't require a restart and shoudl stay enabled. However, if you are updating to a wallet with a different protocol then you must re-activate your node from the Cold Wallet regardless of whether you did the migration in less than one hour.

.. _startmasternode_updateexisting:

1. There are three ways that you can start the MasterNode from the Cold Wallet.  Below are the three options to register the MasterNode.
	
* Option 1. Open the Masternodes tab, select the MasterNode that you want to start, and click the button **Start alias**
* Option 2. Open the Masternodes tab and click the button **Start all**
* Option 3. Open the Cold wallet Debug console and run the following command::
	
	startmasternode alias false MN1

* In the example above, the alias of my MasterNode was MN1. In your case, it might be different and is based on what you entered as the first word in the masternode.conf file.
* You should get multiple lines of output.  If one of the lines of output says **"result" : successful"** then you can proceed to the next step to verify the MasterNode started correctly on the VPS Hot wallet.  If you did not get the **successful** output then there is likely an issue with the masternode.conf file that needs to be resolved first.

.. warning:: Every time you start the MN, from the Cold Wallet, it starts the queue cycle over again.  The queue cycle currently takes up to 36 hours for you to get a payout.  DO NOT USE THIS COMMAND IF YOUR SYSTEM IS ALREADY STARTED OR IT WILL CAUSE YOU TO LOSE YOUR PLACE IN THE QUEUE CYCLE AND THE 36 HOUR WAIT WILL START OVER AGAIN.
	
**If you received the output that shows the MasterNode started successfully then you can proceed to the next step to verify that your MasterNode started correctly from the VPS Hot wallet.**