.. _Putty: https://putty.org/
.. _scripted-vpsandhotwallet:
.. |br| raw:: html

   <br />
   
=================================
Scripted VPS and Hot wallet Setup
=================================

This section of the guide is for users that want to use the bash script to automatically install and setup the Linux VPS.  The setup and configuration of the Cold Wallet will still be a manual setup. 

Order and setup a Linux VPS
---------------------------
	
.. _identifyvps_vpsandhotwallet:

1. Identify a VPS provider and order a Linux Ubuntu 16.04 x64 server. **Ubuntu v18.04 is NOT SUPPORTED.**

	**Recommended VPS Providers:**
+---------------------------------------------------------+
|* `Digital Ocean <https://m.do.co/c/95a89fb0b62d>`_      | 
|* `Vultr <https://www.vultr.com/?ref=7318338>`_          |
|* `Linode <https://www.linode.com/>`_                    |
|* `Amazon Web Services (AWS) <https://aws.amazon.com/>`_ |
+---------------------------------------------------------+

	**VPS Minimum Requirements:**
+-----------------------------------------+
|* Linux - Ubuntu 16.04 - 64 Bit OS |
|* 1GB of RAM                             |
|* 20GB of disk space                     |
|* Dedicated Public IP Address            |
+-----------------------------------------+
	
2. Login to the VPS provider website and configure the external firewall to allow SSH port 22 and the Rupaya Wallet TCP port 9050.
	
3. Login to the VPS, via SSH, as the **root** user.

4. Run the following commands to download and run the bash script that will install and configure the Rupaya Wallet::

	wget -N https://raw.githubusercontent.com/rupaya-project/rupxscript/master/rupx_install.sh
	bash rupx_install.sh

5. Save the output from the script somewhere safe, as you will need this information again later in the setup.  The **MASTERNODE PRIVATEKEY** (aka. GenKey) will be used in the masternode.conf file in your Cold Wallet.  The output should look something like this::

	Rupaya Masternode is up and running listening on port 9050.
	Configuration file is: /root/.rupayacore/rupaya.conf
	Start: systemctl start Rupaya.service
	Stop: systemctl stop Rupaya.service
	VPS_IP:PORT 157.230.178.131:9050
	MASTERNODE PRIVATEKEY is: 2rE12DuD5zdtHfW8FK2eZiYbRYbCi9eysy6rQVeZsu8PTZgStN8
	Please check Rupaya daemon is running with the following command: systemctl status Rupaya.service
	Use rupaya-cli masternode status to check your MN.

6. Run the following command to verify the Rupaya daemon is running and that you have active connections::

	rupaya-cli getinfo

Download the Bootstrap from a Linux VPS Using a Bash Script
-----------------------------------------------------------

This section is intended for those that want to install the bootstrap on a Linux VPS using a bash script, which will automate the process.  
	
1. Login to the Linux VPS as the user that will be running the wallet.

2. Run the following commands, **one at a time**, to download and run the bash script::
	
	wget https://raw.githubusercontent.com/BlockchainBrain/Rupaya_Bootstrap/master/root-bootstrap.sh
	bash root-bootstrap.sh

	
Verify the Hot wallet is synchronizing with the blockchain
----------------------------------------------------------

1. Run the **rupaya-cli getinfo** command to make sure that you see active connections::
	
	rupaya-cli getinfo
	
2. Run the **rupaya-cli getblockcount** command every few mins until you see the blocks increasing::
	
	rupaya-cli getblockcount

* NOTE: If your block count is **NOT** increasing then you will need to stop the Hot wallet with the **rupaya-cli stop** command and then reindex with the **rupayad -reindex** command. 
* **NOTE: If you did the reindex and you continue to have issues with establishing connections then check that the VPS provider external firewall is setup correctly to allow TCP port 9050 from anywhere.  If that is not setup correctly then you will not be able to proceed beyond this step.**
	
**If your block count is indeed increasing, then you can proceed to the next step to setup the Cold wallet.**