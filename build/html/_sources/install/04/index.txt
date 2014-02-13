.. _install-macosx:

.. index::
   single: Install on Mac OSX
  
Install OpenERP on Mac OSX 10.X.X
==================================

There are many ways to install libraries in to Mac OS 10.X which is required by the OpenERP to run on your Mac OS. Some of the preferred methods are port or pip or easy_install in few case you may use brew is it install libraries in to users local directory not available for other users in same machine.

Install PostgreSQL
------------------
You need to install PostgreSQL database as OpenERP is using as a backend storage, you need to install and configure before you setup additional libraries and OpenERP server.

Download the Installable package form http://www.enterprisedb.com/products-services-training/pgdownload or you can read more ways to install PostgreSQL on Mac OS at http://www.postgresql.org/download/macosx/

Run the installer and follow the steps

.. image:: images/postgresql-mac.png

PostgreSQL installation step - 1

Configure postgresql for OpenERP user. You need to add your current user as a postgres user which you have created under your MAC OS and you are using the same user to run OpenERP server. In order to add role to postgresql switch to postgres user.

.. code-block:: bash

	openerp-desktop:/$ sudo su postgres
	password: XXXXXXXXXX

Create a new user using following command, in my case I have created openerp as my mac user.

.. code-block:: bash

	bash-3.2$: createuser openerp
	Shall the new role be a superuser? (y/n) y

:ref:`Install and configure PgAdmin3 <pgadmin3>` if you want to use graphical user interface for PostgreSQL.

Install Xcode, Command line tool and MacPorts
---------------------------------------------
In order to install libraries using the port method on Mac OS, You need to install development platform and essential libraries, for that  you need to download and install Xcode from the Apple Store. You just need correct login and password for Apple store to install software from store.

.. image:: images/xcode-install.png

Install Xcode

Once you install Xcode correctly, you need to install command line tools that allow us to run port command from command line, run below command to install command line tool.

.. code-block:: bash

	openerp-desktop:/$xcode-select --install

Last tool you need to install is MacPorts, It is an easy to use system for compiling, installing, and managing open source packages, libraries and softwares on MacOS.

Before you Download and install the macport you need to agree to the license by dunning below command

.. code-block:: bash

	sudo xcodebuild -license

Download macport depending on your MacOS version an install the package like other software.

.. image:: images/install-macport.png

Install MacPorts

The MacPorts "selfupdate" command will also be run for you by the installer to ensure you have our latest available release and the latest revisions to the "Portfiles", run below command to update port profiles.

.. code-block:: bash

	sudo port -v selfupdate

Once you complete the installations of Xcode, Command Line Tool and MacPorts, you are ready install related libraries for the OpenERP

Install OpenERP Server
----------------------
If you plan to use OpenERP 6.1 or above you need Python 2.6 or later version,  you can check the version of your Python installed on your machine using below command.

.. code-block:: bash
	
	openerp-desktop:/$ python --version
	Python 2.7.5

You can install all required dependencies with below listed command:

.. code-block:: bash

	openerp-desktop:/$ sudo -i
	Password:
	root # port install py-psycopg2 py-reportlab \
	py-lxml py-tz py-mako py-dateutil graphviz py-parsing py-pil \
	py-docutils py-openid py-mock py-unittest2 py-Werkzeug \
	py-mxdatetime py-caldav py-pydot pt-babel py-chart

On success you are ready to download and run OpenERP server. OpenERP server can be download form the OpenERP's website, check which version you should download. If you only want to test the server, you do not need to install it. Just unpack the archive and start the openerp-server executable:

.. code-block:: bash

	tar -xzf openerp-7.0-latest.tar.gz
	cd openerp-7.0-*
	./openerp-server
	./openerp-server -h

The OpenERP Server can be installed very easily using the setup.py file:

.. code-block:: bash

	tar -xzf openerp-7.0-latest.tar.gz
	cd openerp-7.0-*
	sudo python setup.py install

Once you install OpenERP successfully you are ready to Create your first database in OpenERP.

.. note: Sometime you need to change the language settings by changing some variable related the language settings as below.

.. code-block:: bash
	
	export LC_ALL=en_US.UTF-8
	export LANG=en_US.UTF-8
	export LC_CTYPE="C"
	export LC_ALL="C"