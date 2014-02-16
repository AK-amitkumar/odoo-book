.. _setup-chart-of-accounts:

.. index::
	single: Chart of Account
		
Setup Books of Accounts
=======================
Accounting system is the hart of any Enterprise System as it is linked to every business process such as sales, purchase, human resource, manufacturing, etc... and financial statements are represent the performance of each company.

In order to setup the accounting system we need to configure some prerequisite like chart of account, financial period, journals (books), and taxes. We will setup below prerequisite objects to encode the sales and payment receipt transaction.

* Fiscal Period : Current financial periods
* Chart of Accounts : Local Sales, Export Sales, Bank Account, Cash Account
* Journals (Books) : Sales, Bank and Cash

Fiscal Periods
--------------
A fiscal year (or financial year, or sometimes budget year) is a period used for calculating annual ("yearly") financial statements in businesses and other organizations. In many jurisdictions, regulatory laws regarding accounting and taxation require such reports once per twelve months, but do not require that the period reported on constitutes a calendar year (that is, 1 January to 31 December). Fiscal years vary between businesses and countries. The "fiscal year" may also refer to the year used for income tax reporting.

.. image:: images/fiscal-periods.png

Fiscal Periods

So, depending on the country fiscal period need to define by the companies. If you want configure your multinational company in OpenERP you can define multiple companies and you can define fiscal year per country as well.

.. note::
	A default fiscal period may be created during the setup of database or when you install account or any related module, you can define a date during installation. If you want to change later either remove all periods and create a new periods after changing the dates of create a new fiscal year and remove the existing year. 