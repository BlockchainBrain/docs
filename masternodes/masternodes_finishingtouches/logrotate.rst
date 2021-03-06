.. _logrotate_mn:

===================
Configure Logrotate
===================

This section is intended for MasterNode users that want to configure automatic log rotation.  This is to prevent the log files from filling up the Linux VPS hard drive.  If you do not occassionally clean up the log files then your Linux VPS hard drive will eventually fill up and the server will crash.  Completing the steps in this section will configure your Linux VPS to automatically clean up the logs every 30 days, rather than having to do it manually.  This is a necessary step for anyone running a MasterNode. 

1. Connect to your Linux VPS and login as **rupxmn**.

2. Elevate to **root** level privelege::

	sudo -i

3. Run the following command to create and edit the file **/etc/logrotate.d/rupaya**::

	nano /etc/logrotate.d/rupaya

* If prompted, select Nano as your text editor
	
4. Copy the following text and paste it into the file.

* Use this template if you are running the wallet with the user **rupxmn**::
	
	/home/rupxmn/.rupayacore/*.log {
		su root adm
		size 3M
		daily
		missingok
		rotate 30
		copytruncate
		dateext
		compress
		notifempty
		create
	}

* Use this template if you are running the wallet with the user **root**::
	
	/root/.rupayacore/*.log {
		su root adm
		size 3M
		daily
		missingok
		rotate 30
		copytruncate
		dateext
		compress
		notifempty
		create
	}
	
* Save and close the file by hitting **Ctrl-X**, and then type **Y** to confirm that you want to save it, and then hit **ENTER** to confirm the file name.

5. Run the following command to initialize logrotate.

* Use this template if you are running the wallet with the user **rupxmn**::

	logrotate /etc/logrotate.d/rupaya --state /home/rupxmn/logrotate-state --verbose

* Use this template if you are running the wallet with the user **root**::

	logrotate /etc/logrotate.d/rupaya --state /root/logrotate-state --verbose
	
6. Run the following command to open and edit the **crontab** file::

	crontab -e

* If prompted, select Nano as your text editor
	
7. Copy the following text and paste it on a new line at the bottom of the **crontab** file.

* Use this template if you are running the wallet with the user **rupxmn**::

	0 1 * * * /usr/sbin/logrotate /etc/logrotate.d/rupaya --state /home/rupxmn/logrotate-state

* Use this template if you are running the wallet with the user **root**::

	0 1 * * * /usr/sbin/logrotate /etc/logrotate.d/rupaya --state /root/logrotate-state
	
* Save and close the file by hitting **Ctrl-X**, and then type **Y** to confirm that you want to save it, and then hit **ENTER** to confirm the file name.
* This above line added to the **crontab** file will configure the Linux VPS to initialize logrotate when the Linux VPS is rebooted.

**Now that logrotate is configured, you can proceed to the next section to** :ref:`automatically start the MasterNode Hot wallet when the Linux VPS reboots<hotwalletautostart>`

