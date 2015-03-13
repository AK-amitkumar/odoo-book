.. _setup-production-openerp-service:

Configure OpenERP as Linux Service
==================================

.. note::
	Some of the part of this page is taken from http://powerphil.wordpress.com/
	
As we advice that for production setup Linux is the preferred Operating System, It is an essential to configure OpenERP as an linux server after the installation. 

OpenERP can be install on any linux system based on ``.deb`` or ``.rpm``, please go through below installation steps for Linux and Mac.

* :ref:`Install OpenERP on Ubuntu Desktop or Server <install-ubuntu>`
* :ref:`Install OpenERP on Fedora, CentOS <install-fedora>`
* :ref:`Install OpenERP on Mac OSX 10.X.X <install-macosx>`

After successfully installation, you can configure the server to be started automatically at boot time, so install it as a service.

.. warning::
	OpenERP should be installed and have access on the postgresql for the linux user ``openerp``. If you not have a openerp as user create a user with ``adduser openerp``
	
Create a Script
---------------
Create a new fie, /etc/init.d/openerp-server with these contents. This script should work on Ubuntu and Centos. If you are on Ubuntu or Debian and have start-stop-daemon available.

.. code-block:: bash

	#!/bin/sh
	
	#
	# OpenERP init script v0.1 for centos by Open-Future
	# Bert Deferme - www.open-future.be - bert@open-future.be
	#
	
	# This program is free software; you can redistribute it and/or modify
	# it under the terms of the GNU General Public License version 3 as
	# published by the Free Software Foundation.
	#
	# For a copy of the GNU General Public License, see <http://www.gnu.org/licenses/>.
	
	# chkconfig: 345 60 61
	# description: starts the openerp-server service
	
	NAME=openerp-server
	USER=openerp
	
	PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin
	PIDDIR=/var/run/openerp
	PIDFILE=$PIDDIR/$NAME.pid
	DAEMON=/usr/local/bin/openerp-server
	DAEMONOPTS="--pidfile=${PIDFILE}"
	
	checkpid() {
	  [ -f $PIDFILE ] || return 1
	  pid=`cat $PIDFILE`
	  [ -d /proc/$pid ] && return 0
	  return 1
	}
	
	do_start() {
	
	  if [ -f $PIDFILE ]; then
	    echo "pidfile already exists: $PIDFILE"
	    exit 1
	  fi
	
	  echo -n "Starting $NAME: "
	
	  if [ ! -d $PIDDIR ]
	  then
	      mkdir $PIDDIR
	      chown $USER $PIDDIR
	  fi
	
	  su - $USER -c "nohup $DAEMON $DAEMONOPTS >/dev/null 2>&1 &"
	
	  sleep 3
	
	  checkpid
	
	  if [ $? -eq 1 ]; then
	    rm -f $PIDFILE
	    echo "failed."
	    exit 1
	  fi
	
	  echo "done."
	}
	
	do_stop() {
	
	  checkpid
	
	  if [ $? -eq 1 ]; then
	    echo -n "$NAME not running... (no pidfile found)"
	    exit 0
	  fi
	
	  echo -n "Stopping $NAME: "
	
	  pid=`cat $PIDFILE`
	  kill -15 $pid
	
	  sleep 2
	
	  if [ $? -eq 1 ]; then
	    echo "Failed. (pidfile found but process didn't exist)"
	    exit 1
	  fi
	
	  echo "done."
	
	}
	
	do_status() {
	
	  echo -n "Checking $NAME: "
	
	  checkpid
	
	  if [ $? -eq 1 ]; then
	    echo "stopped."
	  else
	    echo "running."
	  fi
	
	}
	
	do_restart() {
	
	  do_stop
	
	  if [ $? -eq 1 ]; then
	    exit 1
	  fi
	
	  do_start
	
	}
	
	case "$1" in
	    start) do_start ;;
	    stop) do_stop ;;
	    restart|force-reload) do_restart ;;
	    status) do_status ;;
	    *)
	        N=/etc/init.d/$NAME
	        echo "Usage: $N {start|stop|restart|status}" >&2
	        exit 1
	        ;;
	esac
	
	exit 0
	
Make the file executable
------------------------
Once the file created make it executable using below command

.. code-block:: bash
	
	chmod a+x /etc/init.d/openerp-server
	

Configure to start on boot
--------------------------
In order to configure openerp-server to start on boot we have to link from /etc/init.d/openerp-server to /etc/rc*.d using below list of commands:

.. code-block:: bash
	
	ln -s /etc/init.d/openerp-server /etc/rc0.d/K83openerp-server
	ln -s /etc/init.d/openerp-server /etc/rc1.d/S83openerp-server
	ln -s /etc/init.d/openerp-server /etc/rc2.d/S83openerp-server
	ln -s /etc/init.d/openerp-server /etc/rc3.d/S83openerp-server
	ln -s /etc/init.d/openerp-server /etc/rc4.d/S83openerp-server
	ln -s /etc/init.d/openerp-server /etc/rc5.d/S83openerp-server
	ln -s /etc/init.d/openerp-server /etc/rc6.d/K83openerp-server
	

Make sure the log file is writable by openerp linux user.

.. code-block:: bash
	
	touch /var/log/openerp-server.log
	chown openerp /var/log/openerp-server.log

Create a config file 
--------------------
If the user you created as part of the installation was openerp, then create ``~openerp/.openerp_serverrc``, to get the content run OpenERP with -s option:

.. code-block:: bash
	
	sudo -u openerp openerp-server -s

Add below options to the configuration of the .openerp-serverrc file to define the log file and level of loginfo

.. code-block:: bash
	
	[options]
	debug_mode =  True
	logfile =  /var/log/openerp-server.log
	log_level =  debug_rpc_answer

Change Permission
-----------------
If you were running these commands as root and not as openerp user, change the ownership to openerp:

.. code-block:: bash
	
	chown openerp:openerp ~openerp/.openerp_serverrc
	
Start, Stop OpenERP Server
--------------------------
If everything goes well you will be able to satrt and stop server using below comands.

.. code-block:: bash
		
	service openerp-server start
	service openerp-server stop
