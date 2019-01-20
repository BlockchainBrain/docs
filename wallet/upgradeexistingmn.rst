.. _upgradeexistingmn:

.. _upgradehotwallet:

=============================================
Upgrade an Existing MasterNode VPS Hot Wallet
=============================================

These instructions are intended for those that are already running a MasterNode and want to upgrade an existing VPS with the newest Rupaya Core 5 wallet.

1. Use Putty (PC) or Terminal (MAC) to login to the Linux VPS that is running the Rupaya Hot wallet.  

2. Login as the user that you used to install the wallet.  Below are some of the possible usernames you may have used, depending on which installation guide you followed:

	+-------------------------------------+
	|* root (github)                      |
	|* rupxmn (http://rupx.center/mnode)  |
	|* rupx01 (GoodTimes setup guide)     |
	|-------------------------------------+

	* Note: These instructions will assume that you did not use root as the default user and therefore provides the commands starting with sudo to allow the commands to run with root privileges.

3. Stop the current wallet daemon with the following command::

	rupaya-cli stop

4. Download and extract the new wallet::

	wget https://github.com/rupaya-project/rupx/releases/download/v5.0.33/rupaya-5.0.33-x86_64-linux-gnu.tar.gz
	tar -xvf rupaya-5.0.33-x86_64-linux-gnu.tar.gz --strip-components 2

5. Delete the unneccessary file::

	rm rupaya-5.0.33-x86_64-linux-gnu.tar.gz

6. Move the neccessary files to the /usr/local/bin/ directory::

	sudo mv rupayad rupaya-cli /usr/local/bin/

7. Restart the Hot wallet with the **rupayad -deamon** command::

	rupayad -daemon
	
* NOTE: If you get the error "**error: couldn't connect to server**" then you may need to kill the process manually or reboot the VPS and then restart the wallet with the **rupayad -daemon** command.

8. Run the **ps -ef |grep rupaya** command to verify that the daemon is indeed running::

	ps -ef |grep rupaya
	
NOTE: You should get output showing that the **rupayad -daemon** is running.  If you only see one single line that contains this output "**grep --color=auto rupaya**" then the daemon is not actually running.  In this case, you may need to reboot the VPS and then run the **rupayad -daemon** command to be able to start the daemon successfully.

**Once the rupayad -daemon service is confirmed as running, the upgrade of your existing Hot wallet is complete.  Please proceed to the next step to set up the Cold Wallet on your computer.**