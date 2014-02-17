.. _install-application-account:

.. index::
	single: Install Accounting

Accounting and Finance Application
==================================

.. note::
	Before you proceed for the installation you should know the difference between :ref:`OpenERP Apps vs Module <get-start-module-apps>`. If you are going to install modules that is available locally, make sure your are on latest version of that modules. Its better to work with the OpenERP Apps store that always deliver latest in terms of ``versions`` along with the ``bug fix`` and ``improvements``.

Install
-------
To install Accounting and Finance in OpenERP, Goto Settings → Apps → and click on Install button of Accounting and Finance Apps.

.. image:: images/account-module.png

Accounting and Finance

It may ask you for the username and password for OpenERP.com account on successfully login it will download best version for Accounting and Finance apps from apps store.

Post Install
------------
On successful installation of Accounting and Finance, OpenERP will start a configurations wizard which will ask many important informations to setup the accounting process for your company. 

Step 1: Chart of Account
~~~~~~~~~~~~~~~~~~~~~~~~
Prerequisite  for any company in the world to define the chart of accounts in order to define their legal statements like Trial Balance, Profit and Loss and Balance sheet and fiscal period depending on their county. OpenERP support almost 25+ countrie's charts of account ready to use.

.. image:: images/account-step001.png

Chart of Account and Fiscal Period selection

Select the Company and Chart of account depending on your country. Select the first and last date of your financial period. It is the actual fiscal period and not assessment period.

Depending on the closing periods practice you can choose Periods to create wither Monthly or 3 Monthly.

* Monthly : Small companies preferred to close their period by every months
* 3 Monthly : Almost all the listed companies have to produce the Profit and Loss and provisional Balance sheet quarterly, they should choose this options during configuration.


Step 2: Chart of Account
~~~~~~~~~~~~~~~~~~~~~~~~
Depending on the selection of Company and Chart of Account in Step1, you will get the default currency Sales and Purchase Tax and # of digits to generate the Journal code. 

.. image:: images/account-step002.png

Currency and Default Taxes

Depending on the majority of product and tax applied to that you have to choose default tax carefully, else each time you have to change the tax when you create a new product.

.. note::
    You can recall the same wizard in case if you want to configure the multiple companies from Settings → Configuration Wizards. Select the Wizard set it to TODO and Launch it.