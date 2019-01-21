.. _wallet_bootstrap:

========================================
Bootstrap - Steps to Install a Bootstrap
========================================

These instructions are intended for anyone that wants to speed up the synchronization process when installing the wallet for the first time or to resolve issues with a wallet that has forked onto the wrong chain. 


Downloading the Bootstrap from a PC or MAC
------------------------------------------

This section is intended for those that want to install the bootstrap on a PC or MAC.  
	
1. Close the Rupaya wallet.  Be sure that it is completely closed before proceeding.

2. Open the following URL in a web browser to download the zip file containing the bootstrap:

	* https://rupaya.ams3.cdn.digitaloceanspaces.com/bootstrap/rupx-bootstrap-160119.zip

3. Open the file named **rupx0bootstrap-16.xip** and extract the folders and files to the RupayaCore folder.
	+------------------------------------------------+
	|* Mac: ~/Library/Application Support/RupayaCore |
	|*     or ~/Library/Application Support/Rupaya   |
	|* Windows: ~/AppData/Roaming/RupayaCore         |
	|*       or ~/AppData/Roaming/Rupaya             |
	+------------------------------------------------+
	* If prompted, confirm that you want to replace the existing file(s).

3. Restart the Rupaya wallet.  

	* The installation of the bootstrap is now complete.

	
Download the Bootstrap from a Linux VPS Using a Bash Script
-----------------------------------------------------------

This section is intended for those that want to install the bootstrap on a Linux VPS using a bash script, which will automate the process.

.. warning:: Only do this on a Linux VPS Hot Wallet that does not contain RUPX or zRUPX, or you will lose your coins.  
	
1. Login to the Linux VPS as the user that will be running the wallet.

2A. For those running the wallet as the user **rupxmn**, run the following commands, **one at a time**, to download and run the bash script::

	wget https://raw.githubusercontent.com/BlockchainBrain/Rupaya_Bootstrap/master/rupxmn-bootstrap.sh
	sudo bash rupxmn-bootstrap.sh

2B. For those running the wallet as the user **root**, run the following commands, **one at a time**, to download the bash script::
	
	wget https://raw.githubusercontent.com/BlockchainBrain/Rupaya_Bootstrap/master/root-bootstrap.sh
	bash root-bootstrap.sh

3. Verify that the wallet is running and that the block count is above 177000::

	rupaya-cli getinfo

Download the Bootstrap manually from a Linux VPS
------------------------------------------------

This section is intended for those that want to manually install the bootstrap on a Linux VPS.  YOU DO NOT NEED TO REPEAT THIS STEP IF YOU ALREADY INSTALLED THE BOOTSTRAP USING THE BASH SCRIPT.  
	
.. warning:: Only do this on a Linux VPS Hot Wallet that does not contain RUPX or zRUPX, or you will lose your coins.

1. Login to the Linux VPS as the user that will be running the wallet.

2. Close the Rupaya wallet::

	rupaya-cli stop

3. Run the following commands to delete the old rupayacore files and folders::

	cp ~/.rupayacore/rupaya.conf .
	sudo rm -rf ~/.rupayacore
	mkdir ~/.rupayacore
	mv rupaya.conf ~/.rupayacore/.

4. Run the following command to download the bootstrap::

	wget https://www.dropbox.com/s/hqmmf5wo6gpbq1b/rupx-bootstrap-160119.zip

5. Install Unzip::

	apt-get install unzip -y

6. Unzip the bootstrap folders and files into the .rupayacore folder:: 

	unzip rupx-bootstrap-160119.zip -d ~/.rupayacore

7. Restart the wallet::

	rupayad -daemon

8. Delete the bootstrap.zip file::

	rm rupx-bootstrap-160119.zip
