.. _qualify-lead:

.. index::
	single: Make a Proposal
	single: Create Quote
	
Make a Proposal to Customer
===========================
We know you are smart salesman, you have convince customer to get the best proposal to implement the digital solutions to spread the newspapers to thousand of subscribers. Once you enter in to propositions stage you can make an proposal form the opportunity itself. 

.. image:: images/make-quote.png

Create a Proposal

.. tip::
	You need to install a module named ``sale_crm`` from OpenERP Apps store, that place button "Convert to Quotation" allow you to prepare a proposal based on the opportunity.

Create a Quotation
------------------
After Installation of ``sale_crm`` you will get "Convert to Quotation" button allow you to create a proposal. Click on "Convert to Quotation", it will ask customer name if you have not define customer on opportunity else select the available on opportunity. If sale is confirmed you can check mark won else leave unchecked. 

.. image:: images/quotation.png

Proposal

Quotation Number
~~~~~~~~~~~~~~~~
Generated automatically based on the sequence, and displayed on the top of the proposal.

Customer
~~~~~~~~
Name of the customer to whom we are going to send the proposal. In edit mode we can see the name and after saving the proposal in view mode we can see customer name along with the full contact details. 

.. image:: images/quotation-readonly.png

Customer along with Address

Date
~~~~
Date on which the proposal made and send to the customer. 

Products
~~~~~~~~
Products we are going to propose to the customer in terms of Online Publication Solutions and Customization services. We can add tax depending on the product and unit price, click on compute button (link) beside Total to get the proposal value along with Taxes.

Terms and Conditions
~~~~~~~~~~~~~~~~~~~~
A multi line textbox, we can enter any text we want. We can place the terms and conditions additional to the proposal.

Other Informations on Quotation
-------------------------------
Quotation have other informations too, where we can define additional key parameters to the quotation. 

.. image:: images/quotation-otherinfo.png

Other Information on Quotation

Salesperson
~~~~~~~~~~~
A Salesman who made this proposal and who is responsible to follow up for this proposal. You can also count commission depending on this field when the quotation get confirmed.

Sales Team
~~~~~~~~~~
Linked automatically from the opportunity when we create a quotation. This field is use to compute the achievements (confirmed sales orders) of team and what is achievable (quotation).

Categories
~~~~~~~~~~
Important when we do analysis of what we sale by categories based on the confirmed sales orders.

Source Document
~~~~~~~~~~~~~~~
When we create a quotation from opportunity it contains the id of that opportunity to cross reference, In other case it can be empty.

.. note::
	Value of Salesperson, Sales Team, Categories and Source Document comes to Sales order automatically, when Order/Quotation created form the opportunity.

Payment Term
~~~~~~~~~~~~
Payment terms, defines how customer have to pay against the delivery of product / service, it comes from the Accounting modules.

Fiscal Position
~~~~~~~~~~~~~~~
Depending on the customer location, we have to choose the value of this fiscal position. It is used to select the correct account for sales, sales tax, depending on the locations of the customer, i.e. Local Sales, Sales Outside State, Export Sales, etc...

Send to Customer
----------------
Once the proposal has been created we can send this proposal to customer through various ways. You can print quotation and send it through courier or today email is the fastest ways to deliver any digital documents. Send quotation through email is a best options as OpenERP generate all documents in PDF format it is easy to send the same to customer.

Send by Email
~~~~~~~~~~~~~
You can send a proposal by Email to customer on their register email address, by clicking on the "Send by Email" button on proposal. 

Print
~~~~~
By clicking on the print button you can get the proposal in pdf format, you can print that on paper and send it through courier.

Confirm Sales
-------------
Once the proposal get approved by the customer, we can confirm the quotation to convert in to sales order. It changes the title from ``Quotation SO009`` to ``Sales Order SO009``. In OpenERP 8.0 you can install a module ``website_quote`` to discuss and approve or reject the proposal along with the customer signature online.

We can create a invoice based on the confirmed Sales Order, as the default invoice  policy is "Invoice based on Sales". There are other invoice policy too, appear after installation of module ``stock``.