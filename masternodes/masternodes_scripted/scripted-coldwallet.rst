.. _scripted-coldwallet:
.. _Video: https://www.youtube.com/watch?v=0TU044CYfl4/

=================
Cold Wallet Setup
=================

These instructions are intended for advanced users that are setting up a Cold wallet and don't want to waste time with all those pesky details and explanations.

Requirements:
--------------
	+--------------------------------------------------------------------------------------+
	| * Windows 7 or higher, Mac OS, or Linux Ubuntu 16.04/18.04                           |
	| * Outgoing internet access to sync the blockchain and enable the MasterNode remotely | 
	+--------------------------------------------------------------------------------------+

Install the Rupaya Cold Wallet
------------------------------

1. Open the following URL in a web browser to download the appropriate wallet version for your system:

	* https://github.com/rupaya-project/rupx/releases

2. Be sure that your existing wallet.dat and private keys are backed up from the old wallet.  We strongly recommend backing up your wallet.dat and private keys prior to starting this process.

	For more instructions, watch this Video_ from a fellow Rupayan, David Coen, on how to export your private keys:

3. Close the Rupaya wallet, if you already have one installed and running.

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


Create a MN1 Wallet Address and Send it the 20000 Collateral Coins
------------------------------------------------------------------

1. Create a receiving address named MN1.  This wallet address will be used for the MasterNode collateral funds.

2. Send **EXACTLY 20000 RUPX** coins to the MN1 address. Double check you've got the correct address before transferring the funds.

	* After sending, you can verify the balance in the Transactions tab. This can take **a few minutes** to be confirmed by the network.

.. warning::	If you are sending from an exchange, make sure you account for the withdrawal fee so that you get EXACTLY EXACTLY EXACTLY 20000 RUPX in the new wallet address. This is a common error that will cause the next step to not give you the transaction id that is needed. For example, to withdraw from `Stocks.Exchange` the correct ammount for a MasterNode, you need to specify the ammount of **20000.001** to account for the fee.

Output your MN TXhash and Outputidx and update the MasterNode configuration file
--------------------------------------------------------------------------------

1. Open the Debug console.

2. Run the **masternode outputs** command to retrieve the transaction ID (aka txhash) of the new MN1 wallet that contains the 20000 RUPX collateral::

	masternode outputs

3. Copy and save the **txhash** and **outputidx**.

4. Go to **Tools** -> **Open Masternode Configuration File** to open the **masternode.conf** file.  

5. Copy the following template and paste it into the **masternode.conf** file, on a new line::

	MN1 <public_mn_ip_address_here>:9050 <your_masternode_genkey_output> <collateral_output_txid> <collateral_output_index>
	
6. Update the **masternode.conf** file variables as instructed below.

* Leave **MN1** as is.  
* Replace the variable **<public_mn_ip_address_here>** with your Linux VPS IP address.
* Leave **:9050** as is and ensure that there are no spaces between the IP address and the port. 
* Replace the variable **<your_masternode_genkey_output>** with your masternode private key (aka GenKey). 
* Replace the variable **<collateral_output_txid>** with the **txhash**.
* Replace the variable **<collateral_output_index>** with the **outputidx**.
* **NOTE:** Below is an example of what the newly added line will look like once you have updated it will all of the required information::

	MN1 199.247.10.25:9050 87LBTcfgkepEddWNFrJcut76rFp9wQG6rgbqPhqHWGvy13A9hJK c19972e47d2a77d3ff23c2dbd8b2b204f9a64a46fed0608ce57cf76ba9216487 1

7. Restart the Cold wallet to pick up the changes to the **masternode.conf** file.

Verify the Masternode.conf File is Configured Correctly
------------------------------------------------------

1. Open the Debug console and run the command **masternode list-conf**::

	masternode list-conf

* Verify that the output matches what you entered in the **masternode.conf** file.
	
2. Go to the Masternodes tab and verify that the newly added MasterNode is listed.

	* You should now see the newly added MasterNode with a status of **MISSING**.
	
Start the MN from the Cold Wallet
------------------------------------

.. warning:: It is very important that you let the MasterNode Hot wallet synchronize for a couple of hours prior to starting it from the Cold wallet.  If you attempt to start it before it is fully synchronized then it will expire after 60 minutes.  Both the Cold and Hot wallets need to be on same version/protocol to activate the MasterNode.

1. There are three ways that you can start the MasterNode from the Cold Wallet.  Below are the three options to re-activate the MasterNode.

* Option 1. Open the Masternodes tab, select the MasterNode that you want to start, and click the button **Start alias**
* Option 2. Open the Masternodes tab and click the button **Start all**
* Option 3. Open the Cold wallet Debug console and run the following command::

	startmasternode alias false MN1

* In the example above, the alias of my MasterNode was MN1. In your case, it might be different and is based on what you entered as the first word in the masternode.conf file.
* You should get multiple lines of output.  If one of the lines of output says **"result" : successful"** then you can proceed to the next step to verify the MasterNode started correctly on the VPS Hot wallet.  If you did not get the **successful** output then there is likely an issue with the masternode.conf file that needs to be resolved first.

.. warning:: Every time you start the MN, from the Cold Wallet, it starts the queue cycle over again.  The queue cycle currently takes up to 36 hours for you to get a payout.  DO NOT USE THIS COMMAND IF YOUR SYSTEM IS ALREADY STARTED OR IT WILL CAUSE YOU TO LOSE YOUR PLACE IN THE QUEUE CYCLE AND THE 36 HOUR WAIT WILL START OVER AGAIN.

**If you received the output that shows the MasterNode started successfully then you can proceed to the next step to verify that your MasterNode started correctly from the VPS Hot wallet.**