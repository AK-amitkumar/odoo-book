.. _setup-customer-supplier:

.. index::
	single: Customers
	single: Suppliers
	single: Parties
	single: Contacts
	
Setup Customers and Suppliers
=============================
Customers and Suppliers are managed very smartly in OpenERP. You can manage customer and supplier in all business cases like B2C or B2B customer and supplier can be configured with the same name perspective to finance management.

To add new customer or supplier click on Create button and you will get the empty form same as below. 

.. image:: images/customer-supplier.png

Customer and Supplier

Company vs Individual
---------------------
To define customer or supplier in OpenERP we need to pass few required informations such like Name, Account Receivable and Account Payable. We can define customer or supplier as an Individual or as a Company. When you define some one as company you can define many different contacts for that company i.e. Purchase Manager, Account Manager, Product Manager, Etc.. If you define Individual you can link them with company later if required.
 
So, If we have customer or supplier as an Individual their Payable & Receivable accounts are maintain individual for them while contacts link to the company their accounts are maintain on the company.

Sales & Purchase Options
------------------------
All the configurations related to the sales & purchase are defined in here for customer or suppliers.

.. image:: images/sales-purchase.png

Sales & Purchase Options

Sales Person
~~~~~~~~~~~~
Usually a dedicated sales person who sales to this customer, this will fill automatically with the salesman who qualify the leads and convert in to Opportunity.

Sales Team
~~~~~~~~~~
You can assign customer to specifics sales team to cross sale when you are working in multi-sales team environment. Also this filed will filled with the salesman's team who qualify the leads and convert in to Opportunity.

Customer & Supplier
~~~~~~~~~~~~~~~~~~~
This is one of the great feature of OpenERP to manage the contact as a customer and suppliers using single contact. When you check both customer and supplier you can access that contact in both sales and purchase activities while creation sale order or purchase order or invoices. 

Language
~~~~~~~~
Use to personalize all the printing reports for specific customer or suppliers. Depending on the language selection OpenERP will print all reports specific to the contacts like Ledger or Overdue reports.

Reference
~~~~~~~~~
A short name related to the Customer or suppliers, used to quickly select through search during the various operations like sales, purchase or invoicing.

Date
~~~~
There is nothing special computations associate with this fields, still we can use this just to specify when we activate or start financial transaction with customer or suppliers.

Active
~~~~~~
This is a system field to hide the customer or supplier we can make it inactive to not get listed in any of the list.

Receive Message by Email
~~~~~~~~~~~~~~~~~~~~~~~~
Used when we assign portal access to customer or suppliers. It defines the email notification policy when they receive any news, email or notification to their wall in OpenERP. :ref:`Read more about Receive Message by Email <receive-message-by-email>`

Opt-Out
~~~~~~~
If this is checked contact has refuse to receive an mass-mails or email from marketing campaigns.

Accounting
----------
All the configurations related to the finance are defined in here for customer or suppliers.

.. image:: images/account-settings.png

Accounting Options

Fiscal Position
~~~~~~~~~~~~~~~
Use to define a customer location in terms of taxonomy, so depending on the locations of customer system can replace and compute the tax at the time of sales. Along with the tax if we would like our local, outside state and export sales we can switch accounts using the same Fiscal Position. 

Account Payable & Receivable
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Depending on the accounting transactions it is used to encode the accounting entries in all types of accounting entry system. i.e. Invoice, Vouchers, Journal Items or Entry, Etc..

Payment Terms
~~~~~~~~~~~~~
We can define payment terms for suppliers and for customer depending on what we get from respective. 

Total Receivable & Payable
~~~~~~~~~~~~~~~~~~~~~~~~~~
Compute and display a total of the receivable and payable amounts for the customer and supplier respectively. OpenERP has a mechanism to settle the payable vs receivable.

Credit Limit
~~~~~~~~~~~~
Yet it is not have any effect on the account or sales or purchase part, it is just a informations fields for the movement in OpenERP.