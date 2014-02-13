.. _setup-header-footer:

.. index::
	single: Report Header
	single: Report Footer
	single: RML Header
	single: Custom Header
	
Setup the Report Header and Footer
==================================

It is necessary for every business to keep the format of all documents as it is, event though  business process may transform through next generation business application or ERP system. OpenERP offers you to configure your letterhead to have same as your letterhead for any legal or external documents such as Invoice, Sales Orders, Purchase Orders, Delivery Orders, Etc..

To change the company header and footer configuration goto Settings → Companies, Select the company for which you would like to change the header and footer.

Before we begging the configuration of company letterhead, all the information should be filled without missing of any fields. There are mainly 3 different formats for the document printing listed as below

* RML Header
* RML Internal Header
* RML Internal Header for Landscape Report

RML Header is used to print all legal and external documents as it contains all the informations required to have on the legal document such as mailing address, contact details like phone and email, company’s tagline, bank and other details like tax numbers and contact person related to that document.

RML Internal and RML Internal for Landscape are the formats use to print all internal documents which are user internally for the company use such as Party Ledgers, Account Ledgers, Some statistical reports, etc..

Standard Header
---------------

RML Header provides configurations to print  the view of company Letterhead as per our need. If you understand any of the markup language it is very easy to change  configurations. There is main section which we are going to change is Page header.

.. image:: images/rml-header.png

Report Header

Look at the below configuration, It generates the above header format for your all your reports.

.. code-block:: xml

	<!-- Set here the default font to use for all <drawString> tags -->
	<setFont name="DejaVu Sans" size="8"/>
	<!-- You Logo - Change X,Y,Width and Height -->
	<image x="1.3cm" y="27.7cm" height="40.0" >[[ company.logo or removeParentNode('image') ]]</image>
	<fill color="black"/>
	<stroke color="black"/>
	 
	<!-- page header -->
	<lines>1.3cm 27.7cm 20cm 27.7cm</lines>
	<drawRightString x="20cm" y="27.8cm">[[ company.rml_header1 ]]</drawRightString>
	<drawString x="1.3cm" y="27.3cm">[[ company.partner_id.name ]]</drawString>
	<place x="1.3cm" y="25.3cm" height="1.8cm" width="15.0cm">
	    <para style="main_header">[[ display_address(company.partner_id) or  '' ]]</para>
	</place>
	<drawString x="1.3cm" y="25.0cm">Phone:</drawString>
	<drawRightString x="7cm" y="25.0cm">[[ company.partner_id.phone or '' ]]</drawRightString>
	<drawString x="1.3cm" y="24.6cm">Mail:</drawString>
	<drawRightString x="7cm" y="24.6cm">[[ company.partner_id.email or '' ]]</drawRightString>
	<lines>1.3cm 24.5cm 7cm 24.5cm</lines>

Custom Header
-------------

OpenERP allows you to change the header of the reports without changing in the source code, as explained you can change form the company configurations, Lets make the changes in header to make it right align.

.. image:: images/rml-header-right.png

Report Header

If you are good at drawing graphs, it will be very easy for you to change the coordinates for some of the elements, and you will get the perfect header for your company. To generate this format you need the below code replace in RML Header configuration.

.. code-block:: xml

	<!-- Set here the default font to use for all <drawString> tags -->
	<setFont name="DejaVu Sans" size="8"/>
	<!-- You Logo - Change X,Y,Width and Height -->
	<image x="14.6cm" y="27.7cm" height="40.0" >[[ company.logo or removeParentNode('image') ]]</image>
	<fill color="black"/>
	<stroke color="black"/>
	 
	<!-- page header -->
	<lines>1.3cm 27.7cm 20cm 27.7cm</lines>
	<drawRightString x="4.5cm" y="27.8cm">[[ company.rml_header1 ]]</drawRightString>
	<drawString x="14.6cm" y="27.3cm">[[ company.partner_id.name ]]</drawString>
	<place x="14.6cm" y="25.3cm" height="1.8cm" width="15.0cm">
	    <para style="main_header">[[ display_address(company.partner_id) or  '' ]]</para>
	</place>
	<drawString x="14.6cm" y="25.0cm">Phone:</drawString>
	<drawRightString x="18cm" y="25.0cm">[[ company.partner_id.phone or '' ]]</drawRightString>
	<drawString x="14.6cm" y="24.6cm">Mail:</drawString>
	<drawRightString x="19cm" y="24.6cm">[[ company.partner_id.email or '' ]]</drawRightString>
	<lines>14.6cm 24.5cm 20cm 24.5cm</lines>

Same way you can change the configuration of the footer too. If you change the configuration of one company does not implies effect for all companies, you have to change the format of letterhead for each company individually.