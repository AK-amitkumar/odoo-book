.. _install-ubuntu:

.. index::
   single: Install on Ubuntu Desktop
   single: Install on Ubuntu Server
   single: Install on Debian

======================================
Install Odoo on Ubuntu or Debian Linux
======================================

Once you install Ubuntu server or desktop based client, you need to install few libraries that is required to run Odoo.

Install PostgreSQL
------------------

You need to install PostgreSQL database as Odoo is using as a backend storage, you need to install and configure before you setup additional libraries and Odoo server.

.. code-block:: shell

	openerp@openerp-desktop:/$ sudo apt-get install postgresql

Configure postgresql for Odoo user. You need to add your current user as a postgres user which you have created under Ubuntu and you are using the same user to run Odoo server. Inorder to add  role to postgresql switch to postgres user.

.. code-block:: shell

	openerp@openerp-desktop:/$ sudo su postgres
	password: XXXXXXXXXX

Create a new user using following command, in my case I have created openerp as a linux user.

.. code-block:: shell

	postgres@openerp-desktop:/$ createuser openerp
	Shall the new role be a superuser? (y/n) y

:ref:`Install and configure PgAdmin3 <pgadmin3>` if you want to use graphical user interface for PostgreSQL.


Install Odoo
------------

If you plan to use Odoo 6.1 or above you need Python 2.6 or later version, simple like Odoo's Versions policy its better to use the Ubuntu's last stable or LTS version for the Production Server. On a Ubuntu or and Debian based Linux distribution you can install all required dependencies with this single command:

.. code-block:: shell

	sudo apt-get install python-dateutil python-feedparser \
		python-gdata python-ldap python-libxslt1 python-lxml python-mako \ 
		python-openid python-psycopg2 python-pybabel python-pychart \
		python-pydot python-pyparsing python-reportlab python-simplejson \ 
		python-tz python-vatnumber python-vobject python-webdav \
		python-werkzeug python-xlwt python-yaml python-zsi \
		python-docutils python-mock

Odoo server can be download form the Odoo's website, :ref:`check which version you should download <version>`. If you only want to test the server, you do not need to install it. Just unpack the archive and start the openerp-server executable:

.. code-block:: shell

	tar -xzf openerp-8.0-latest.tar.gz
	cd openerp-8.0-*
	./openerp-server
	./openerp-server -h

The Odoo Server can be installed very easily using the setup.py file:

.. code-block:: shell

	sudo python setup.py install

Once you install Odoo successfully you are ready to Create your first database in Odoo.

Setup Production Environment
----------------------------
After successfully setup the Odoo Latest server, you can deploy Odoo for production environment on Apache or gUnicorn based on your needs.