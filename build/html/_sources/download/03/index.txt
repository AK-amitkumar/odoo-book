.. _select-version:

.. index::
   single: Windows
   single: MacOSX
   single: Linux

Which version of OpenERP should I download ?
============================================
OpenERP is an platform independent business application. You can run it on any platform Windows, Linux or Mac.

.. image:: images/download.png
   :alt: alternate text

OpenERP Download Page

Linux is the preferred platform for the Production Deployment. You can choose Ubuntu, Fedora, CentOS  or Read Hat flavor of the Linux.

Versions of OpenERP
-------------------

OpenERP is releasing stable version almost every year i.e 5.0, 6.0, 7.0, 8.0 is upcoming version. Each major release is Long term supported versions, as on today 7.0 is the Last stable LTS version and OpenERP is supporting 5.0, 6.0 and 7.0 under the OpenERP Maintenance Contract.

So, If  you plan to Implement OpenERP in production, straight away you should select the OpenERP's last stable version along with the Maintenance contract.

Download Last Stable Version
----------------------------

To visit the download page Click Here !

You just need an user account on OpenERP site in order to download OpenERP and Install modules later from OpenERP's Apps store.

.. image:: images/signup_login.png
   :alt: alternate text

Signup on OpenERP.com

Download the Latest Version
---------------------------
Every night a new set of packages (exe, tgz, deb, rpm) is generated automatically for the following branches:

* `7.0 LTS (stable) <http://nightly.openerp.com/7.0/>`_
* `6.1 (unsupported) <http://nightly.openerp.com/6.1/>`_
* `6.0 LTS (old stable) <http://nightly.openerp.com/6.0/>`_
* `trunk (development) <http://nightly.openerp.com/trunk/>`_

You can download them from OpenERP `Nightly Build Platform. <http://nightly.openerp.com/>`_

For Debian/Ubuntu Users
-----------------------

To install the Debian/Ubuntu package, add the following line to your /etc/apt/sources.list:

::

	deb http://nightly.openerp.com/7.0/nightly/deb/ ./

And type:

::

	sudo apt-get update
	sudo apt-get install openerp
