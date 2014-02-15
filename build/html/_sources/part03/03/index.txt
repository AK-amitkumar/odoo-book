.. _setup-products:

.. index::
	single: Products
	single: Product Category
	single: Sale Price
	single: Cost Price
	
Setup Products and Category
===========================

.. image:: images/product.png

Product basic configuration

After :ref:`setup the customer and suppliers <setup-customer-supplier>` next to setup is Products in order to start sale or purchase. Two important fields need to enter to create a new product ``Name`` and ``Category`` of the product.

Can be Sold and Can be Purchase are the two checkbox used to define product is available for sales and purchase process. If you select product to to be sold you can get more options on product to configure Sales options. 

Product Information
-------------------
All prerequisite information for the product like it is stock-able to not sales price, and references. 

Product Type
~~~~~~~~~~~~
We can define product as a physical product or service in OpenERP. It support below list of options to define the product type. 

* Stockable Product : Use to define a product which valuation count in to the inventory and issues or transfer possible only if the stock available in warehouse. 
* Consumable : Movement in warehouse is possible but does in include in inventory valuations, as it does not takes care for the stock to do such movements in warehouse.
* Service : A product which can not be stock in warehouse, but can be sale or purchase.

Sale Price
~~~~~~~~~~
A fixed price use to define a price for the public. Sale order capture this price when we sale product.

Internal Reference
~~~~~~~~~~~~~~~~~~
Code name for the product used to search the product quickly during various operations like sale or purchase.

EAN 13 Barcode
~~~~~~~~~~~~~~

.. image:: images/barcode.png
   :height: 120px
   :width: 300 px

EAN 13 Barcode for 780672318863 product code
 
A 13 digit International Article Number use to define a barcode data. 

Description
~~~~~~~~~~~
Define the product specification use to describe product technically. 

Product Procurement
-------------------
Informations related to the product procurement & supply method, suppliers of the product.

.. image:: images/product-procurement.png

Product procurement configuration

Procurement Method
~~~~~~~~~~~~~~~~~~
Define the method of procuring when you sale product using any of and of the below methods.

* Make to Stock : When you sell this product, OpenERP will use the available inventory for the delivery order. 
* Make to Order : OpenERP will trigger a draft purchase order to buy the required quantities to the supplier. The delivery order will be ready after having received the products.

.. note::
	When your procure method is ``Make to Stock`` and if there are not enough quantities available, the delivery order will wait for new products. To fulfill the inventory, you should create others rules like orderpoints.

Supply Method
~~~~~~~~~~~~~
Supply method is working with the procurement method, combinations of the this two configuration define how to get the product when needed.

==================		=================		==========================================================================================
Procurement Method		Supply Method			Result
==================		=================		==========================================================================================
Make to Stock			Buy						If stock is available assigned from warehouse, else it will execute the orderpoints
Make to Order			Buy						Straight away create a purchase order for the defined first supplier available on product.
Make to Stock			Manufacture				If available assign from stock else create a manufacturing order
Make to Order			Manufacture				Create a manufacturing order when there is a Sales order
==================		=================		==========================================================================================

Cost Price
~~~~~~~~~~
Cost price for the product, either comes from the supplier or manufacturing cost for the product.

Delays
~~~~~~
Delay in days to process the manufacturing order.

Suppliers
~~~~~~~~~
All the suppliers who supply this product and possible to place order to any any form them. Yet no intelligent selection of the supplier is not implemented in OpenERP to select the supplier when need to create a Purchase Order through Procurement.

Description
~~~~~~~~~~~
Product specification use to describe product to supplier, it is simply supplier specific product description.

.. note::
	Document is not yet finished !
	