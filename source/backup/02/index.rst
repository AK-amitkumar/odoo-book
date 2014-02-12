.. _backup-restore-auto:

Automatic Backup of OpenERP Database
====================================

OpenERP provides backup and restore functionality of its database on various platforms. You can take back and restore on locally installed server while you are allowed to take only backup from OpenERP online, If  you want to restore your database on OpenERP online you can contact to sales@openerp.com.

Here is a very simple steps for creating the OpenERP's database backup automatically using the linux cron job when you have install OpenERP on your own server.

Create a folder under your home folder, here I have created backups.

.. code-block:: bash

	$ cd ~
	$ mkdir backups

Create a new file under backups directory called pg_backup.sh

.. code-block:: bash

	$ vim pg_backup.sh

Create a Script
---------------

Copy and paste the below content to your pg_backup.sh file.

.. code-block:: bash

	#enable this option, if you are creating hourly backup
	if [ ! -d "$2/`date +%F-%H`" ]; then
	    mkdir $2/`date +%F-%H`
	    pg_dump $1 > $2/`date +%F-%H`/$1.sql
	else
	    echo "Do not run this script manually !"
	fi
	
	#enable this option, if you are creating daily backup
	if [ ! -d "$2/`date +%F`" ]; then
	    mkdir $2/`date +%F`
	    pg_dump $1 > $2/`date +%F`/$1.sql
	else
	    echo "Do not run this script manually !"
	fi
	
If you enable both part in pg_backup.sh, it will create a folders for hourly backup and daily backups too.

As this file should be an executable file and called by the root user of your linux system. So, you need to change the permission of file so that root can execute this file.

.. code-block:: bash

	$ chmod 755 pg_backup.sh
	
Now, we are going to execute this backup script through Linux Cronjob so we need to edit crontab list and add few lines to execute our backup script periodically. You can read full details what to write in crontab.

Create Hourly Backup
--------------------

You can create a hourly backups using below commands

.. code-block:: bash
	
	$ sudo crontab -e
	
Add below lines to that edited file and save it.

.. code-block:: bash
	
	@hourly /home/openerp/backups/pg_backup.sh database_name /home/openerp/backups/

Create Daily Backup
-------------------

You can create a daily backups using below commands

.. code-block:: bash

	$ sudo crontab -e

Add below lines to that edited file and save it.

.. code-block:: bash

	@daily /home/openerp/backups/pg_backup.sh database_name /home/openerp/backups/
	
You have setup Linux cronjob  successfully, the last setting you have to apply is to create a role in PostgreSQL database with the name root. Backup script is run by the crontab and it is executed by the root user so usually all execution is done by the root and if root user does not have access to PostgreSQL database our script will not be able to take the backup.

So, just execute the following commands on your linux shell, enter password when prompt and enter "y" when asked for Shall the new role be a superuser? (y/n)

.. code-block:: bash
	
	$ sudo su postgres
	$ createuser root
	
Its Done !

However you can change the pg_backup.sh file to take the backup of large database, as text backup is not capable to handle large database where you have many blob objects in database. Read more about Backup and Restore of OpenERP Database to work with Large database.

Based on your configuration you will see the folders in your backups directory.

.. image:: images/backup_auto.png

Backup Directory

