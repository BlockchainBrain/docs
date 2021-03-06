.. _sendingcoins:

==============================
Sending Coins - RUPX and zRUPX
==============================

These instructions are intended for those that want instructions on how to send RUPX and zRUPX.  This process is useful for those that want to convert your zRUPX back into RUPX and for consolidating coins into a single wallet input for better staking results.

Sending RUPX
============

1. Locate and copy the Rupaya wallet address that you are sending coins to.

2. Open the Rupaya wallet(s) that currently contains RUPX.

3. From the side wallet bar, click **Send**.

4. In the **Pay To:** field, right click and select **Paste** to paste in the wallet address that you copied in Step 1.

5. Click **Open Coin Control**.

	If you haven't already enabled Coin Control then follow these steps:
	
	* From the Rupaya Wallet, click on **Settings**, select **Options**, click on the **Wallet** tab and then click the check-box that says **Enable coin control features**.  
	* This feature will allow you to control your wallet inputs, to verify that all coins are consolidated into a single input, to choose which inputs you send coins from, and to optimize staking.
	
6. Click **(un)Select all** and ensure that all of the checkboxes are checked and that none of them are locked.

7. Click **OK** to close the **Coin Selection** window.

8. Locate the numbers next to the field **After Fee** and right click them and then select **Copy after fee**.  This will copy the total amount of coins you have available to send after the fee is calculated.

9. Right click in the **Amount** field box and select **Paste**.  This will paste in the total amount of coins that you have available to send.

10. Verify that the following information is correct:

	* Pay to wallet address is the correct wallet address you are consolidating all of the coins into.
	* Amount field is the correct amount of all of the coins in the wallet, after the fee is removed.

11. Click **Send** to complete the transaction.  
	
	* Enter your wallet passphrase, if prompted.
	* Click **Yes** when prompted to confirm that you are sure you want to send.


Sending zRUPX
=============

1. Locate and copy the Rupaya wallet address that you are sending coins to.

2. Open your current Rupaya wallet(s) that currently contains zRUPX.

3. From the side wallet bar, click **Privacy**.

4. In the **Pay To:** field, right click and select **Paste** to paste in the wallet address that you will be sending zRUPX coins into.

5. Click **zRUPX Control**.

	If you haven't already enabled Coin Control then follow these steps:
	
	* From the Rupaya Wallet, click on **Settings**, select **Options**, click on the **Wallet** tab and then click the check-box that says **Enable coin control features**.  
	* This feature will allow you to control your wallet inputs, to verify that all coins are consolidated into a single input, to choose which inputs you send coins from, and to optimize staking.
	
6. Click **Select/Deselect all** until the checkboxes are **NOT** checked and then only check boxes next to 7 or less of the available inputs.

	* NOTE: If you select too many inputs then when you attempt to send the coins you will receive an error and the coins will not be sent.

7. Click **OK** to close the **Coin Selection** window.

8. Locate the numbers next to the field **zRUPX Selected:** and type that amount into the **Amount:** field at the bottom of the wallet.

9. Verify that the following information is correct:

	* Pay to wallet address is the correct wallet address you are consolidating all of the coins into.
	* Amount field is the correct amount of all of the coins in the **zRUPX Selected** field.

10. Click **Spend Zerocoin** to complete the transaction.  
	
	* Enter your wallet passphrase, if prompted.
	* Click **Yes** when prompted to confirm that you are sure you want to send.
	* NOTE: If you receive the error: **Failed to find coin set amonst held coins with less than maxNumber of Spends** then you will need to disable zRUPX Automint and wait for the existing zRUPX to complete 200 block confirmations before you will be able to complete this step.
	
