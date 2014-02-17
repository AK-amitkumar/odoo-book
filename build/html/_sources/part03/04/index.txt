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
	
Chart of Account
----------------
While :ref:`installing the Accounting  or related module <install-application-account>` you have been asked to various configurations. Chart of Account is one of them. OpenERP support almost 25+ countries pre-configured charts of account.s

.. image:: images/chart-of-account.png

Chart of Accounts

You can still change the chart as the given chart may not gives you all the modules you need. You can create new or modify them from Accounting → Configuration → Accounts → Accounts.

.. image:: images/accoun.png

Configure Account

Account Code & Name
~~~~~~~~~~~~~~~~~~~
In each country, standard coding system defined to define an account, It will be easier for the Accountant and Auditors to process those account quickly depending on the codes. You can define those code and name as an Account code and name. 

Parent
~~~~~~
Many financial software have the concept of grouping the account under the heads sometimes they called it Groups too. In OpenERP you can define those groups or heads in terms of account with the type ``view``. You can choose all the account as a parent those who define as a internal type as ``view``. So, all account with internal type as can be called a groups or heads.

Internal Type
~~~~~~~~~~~~~
Internal Type define behaviour of the account in system. Depending on that it allows certain operations on certain account and restriction of the selecting some account is also works based on internal type as well.

* View : Define account as a Head / Group, we can not encode any financial transaction on view account.
* Regular : All the account who falls under the Profit and Loss account which does not need any special treatment can be define as a Regular Account
* Receivable & Payable : Used to define the customer or suppliers account.
* Liquidity :  To define all the assets which can be convert in to cash easily, all those types of account define as a Liquidity. i.e. Bank, Cash, Shares Purchased, Etc...
* Consolidation : Used to define groups / heads for multiple accounts. It is use in some special case like groups all bank accounts when working with the multi-company to get the overall bank balance.
* Closed : Once you define account as closed, we can not pass any entries to those accounts. It used in the reports but not available for the entry encoding.

Account Type
~~~~~~~~~~~~
Account type is used to configure the legal reports in the accounting system. Depending on the type selected account will be appear on the Balance sheet or Profit and Loss statement. You can define as many type you want, important fields on type are P&L / BS Category and Deferral Method.

* P&L / BS Category : You can choose when the account will be displayed. In Balance Sheet (Asset or Liability) or Profit & Loss (Income or Expense) side. 
* Deferral Method : You have to choose an option, when the financial year will get close, what to transfer in to the next financial year in the respective accounts ? Only Balance, All details including the reconciled items, or just Unreconciled items or select None to transfer nothing.