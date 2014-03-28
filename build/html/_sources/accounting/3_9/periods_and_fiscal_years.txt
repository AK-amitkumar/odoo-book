
Periods and Financial Years
===========================

.. note:: Periods and Fiscal Years

        A fiscal year (or financial year) corresponds to twelve months for a company.
        In many countries, the fiscal year corresponds to a calendar year. That may not be the case in other countries.

        The financial year can be divided into monthly or three-monthly accounting periods (when you have a quarterly declaration).

OpenERP's management of the fiscal year is flexible enough to enable you to work on several years at the same time. This gives you several advantages, such as the possibility to create three-year budgets.

.. index:: period
.. index:: fiscal year

.. _financialyear:

Defining a Period or a Financial Year
-------------------------------------

To define your fiscal year, use the menu :menuselection:`Settings --> Configuration --> Invoicing`, If there is no fiscal year define for your company then this form offer you to configure fiscal year for your company under the label `No Fiscal Year Define for This Company` you have to define your company fiscal year range and period and click on Apply button.

.. figure::  images/fiscal_config.png
   :scale: 55
   :align: center

   *Defining a Financial Year configuration*

You can create several years in advance to define long-term budgets, use the menu :menuselection:`Accounting --> Configuration --> Periods --> Fiscal Years`, click on `Create` First enter the date of the first day and the last day of your fiscal year. Then, to create the periods, click one of the two buttons depending on whether you want to create twelve 1-month or four 3-months periods:

.. figure::  images/account_period.png
   :scale: 75
   :align: center

   *Defining a Financial Year and Periods*

*  :guilabel:`Create Monthly Periods` ,

*  :guilabel:`Create 3 Months Periods` .

OpenERP automatically creates an opening period to allow you to post your outstanding balances from the previous fiscal year. Notice the ``Opening/Closing Period`` checkbox for such a period.

To close a fiscal year you can also use the menu :menuselection:`Accounting--> Periodical Processing --> End of Period --> Close a Period`.

Closing a Period
----------------

To close a financial period, for example when a tax declaration has been made, go to the menu :menuselection:`Accounting--> Configuration --> Periods --> Periods`, Select those period(s) which you want to close and from top centered `More` button click on ``Close a Period`` then select `Check this box` and on `Close Period` button.
You can also close period from form view of Periods by clicking on `Close Period` button.  

.. tip:: Opening Closed Periods

    The system administrator can re-open a period, which have been closed by mistake.

When a period is closed, you can no longer create or modify any transactions in that period. Closing a period is not obligatory, and you could easily leave periods open.

To close an accounting period you can also use the menu :menuselection:`Accounting--> Periodical Processing --> End of Period --> Close a Period`.

.. Copyright © Open Object Press. All rights reserved.

.. You may take electronic copy of this publication and distribute it if you don't
.. change the content. You can also print a copy to be read by yourself only.

.. We have contracts with different publishers in different countries to sell and
.. distribute paper or electronic based versions of this book (translated or not)
.. in bookstores. This helps to distribute and promote the OpenERP product. It
.. also helps us to create incentives to pay contributors and authors using author
.. rights of these sales.

.. Due to this, grants to translate, modify or sell this book are strictly
.. forbidden, unless Tiny SPRL (representing Open Object Press) gives you a
.. written authorisation for this.

.. Many of the designations used by manufacturers and suppliers to distinguish their
.. products are claimed as trademarks. Where those designations appear in this book,
.. and Open Object Press was aware of a trademark claim, the designations have been
.. printed in initial capitals.

.. While every precaution has been taken in the preparation of this book, the publisher
.. and the authors assume no responsibility for errors or omissions, or for damages
.. resulting from the use of the information contained herein.

.. Published by Open Object Press, Grand Rosière, Belgium
