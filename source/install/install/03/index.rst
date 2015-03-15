.. _install-fedora:

.. index::
   single: Install on Fedora
   single: Install on Redhat
   single: Install on CentOS

==============================
Install Odoo on Fedora, CentOS
==============================

Once you install Fedora or CentOS desktop based client, you need to install PostgreSQL and few libraries that is required to run Odoo.

Install PostgreSQL
------------------
You need to install PostgreSQL database as Odoo is using as a backend storage, you need to install and configure before you setup additional libraries and Odoo server.

.. code-block:: shell

	$ sudo yum install postgresql-server postgresql

After installing the packages, a database needs to be initialized and configured. To do this use Terminal (in fact, do not close current Terminal window during the installation process). First of all, log in as posgresql user using command

If you're not logged in as a root user, do it now, oherwise you won't be able to login as postgres user and type below commands to to initialize the database.

.. code-block:: shell

	$ su -
	$ su postgres
	$ initdb /var/lib/pgsql/data

Following commands will start PostgreSQL server and check for running PostgreSQL processes:

.. code-block:: shell

	$ sudo service postgresql start

Check whether postgres is running or now and add postgresql service to startup list:

.. code-block:: shell

	$ ps -eZ | grep postgres
	$ sudo chkconfig -level 235 postgresql on

:ref:`Install and configure PgAdmin3 <pgadmin3>` if you want to use graphical user interface for PostgreSQL.

Install Odoo Server
----------------------
If you plan to use Odoo 6.1 or above you need Python 2.6 or later version, simple like Odoo's Versions policy its better to use the Fedora's last stable version for the Production Server.

On a Fedora or CentOS or rpm based Linux distribution you can install all required dependencies with this single command:

.. code-block:: shell

	$ sudo yum install python-devel pychart python-dateutil \
		python-reportlab python-lxml  python-psycopg2 python-mako \
		python-setuptools pytz PyYAML graphviz pydot python-imaging \
		pywebdav python-vobject vim system-config-firewall-tui \
		python-babel python-gdata python-ldap python-openid \
		python-werkzeug python-vatnumber

Odoo server can be download form the Odoo's website, check which version you should download. If you only want to test the server, you do not need to install it. Just unpack the archive and start the openerp-server executable:

.. code-block:: shell

	tar -xzf openerp-7.0-latest.tar.gz
	cd openerp-7.0-*
	./openerp-server
	./openerp-server -h
	
The Odoo Server can be installed very easily using the setup.py file:

.. code-block:: shell

	tar -xzf openerp-7.0-latest.tar.gz
	cd openerp-7.0-*
	sudo python setup.py install

Once you install Odoo successfully you are ready to Create your first database in Odoo.

Setup Production Environment
----------------------------
After successfully setup the Odoo Latest server, you can deploy Odoo for production environment on Apache or gUnicorn based on your needs.

