HR Payroll
==========

The new :mod:`hr_payroll` module includes a generic payroll engine that handles everything required to compute hr salary slips, the taxes to pay, etc.
You can manage your company's payroll by using this module.
You have to select option :guilabel:`Manage payroll` from following menu :menuselection:`Settings --> Configuration --> Human Resources` and you can install your country payroll from that option  *Install your country's payroll*.
  
.. figure:: images/install_payroll.png
   :align: center
   :scale: 90

   *Configuration to install hr_payroll module*

OpenERP provides the following features for efficient payroll management process:-

- :guilabel:`Salary rule`: are used to compute data like allowances, deductions, net, taxes, contribution registers, etc. You can define salary rules by using the expression.
- :guilabel:`Salary structure`: Define a set of rules usually applied to a category of employees. Salary calculation after considering all the allowances, deductions and incentives (if any) etc.,
- :guilabel:`Contribution registers`: A register containing to whom the company or the employee have to pay taxes.
- :guilabel:`Employee and contract`: It includes everything required to compute the salary slip of an employee.
- :guilabel:`Salary processing on the basis of leaves taken or number of working days.`
- :guilabel:`Generating Reports.`
- :guilabel:`Integrated with Contracts and Holidays.`

Salary Rule Categories
----------------------

Salary Rule Categories are your Basic, Allowance, Deduction, Gross, Net, Company Contribution, etc by using which you can categorize your Salary Rule. You can define Salary Rule Categories by using the menu :menuselection:`Human Resources --> Configuration --> Payroll --> Salary Rule Categories` and click *Create.*

You can configure the following information:-

- *Name* : A name for the Salary Rule Category.
- *Code* : A code for the Salary Rule Category. It must be unique.
- *Parent* : It is used to create hierarchy for reporting purpose.

After entering the Salary Rule Category information click *Save.*

Salary Rules
------------

Salary Rules are the various types of Allowances, Deductions, etc.You can define Salary Rules by using the menu
:menuselection:`Human Resources --> Configuration --> Payroll --> Salary Rules` and click *Create.*


.. figure:: images/salary_rule.png
   :align: center
   :scale: 80

   *House Rent Allowance defined as Salary Rule*

There are list of Available Variables which will be used to specify field's value(as python code) on Salary Rules.

`Available variables:`

* ``payslip``: object containing the payslips.
* ``employee``: hr.employee object.
* ``contract``: hr.contract object.
* ``rules``: object containing the rules code (previously computed).
* ``categories``: object containing the computed salary rule categories (sum of amount of all rules belonging to that category).
* ``worked_days``: object containing the computed worked days.
* ``inputs``: object containing the computed inputs.

You can configure the following information:-

- *Name* : A name for the Salary Rule.
- *Code* : A code for the salary rule. It must be unique.
- *Category* : Select a category for a rule.
- *Sequence* : Provide the sequence(integer).

.. note:: Sequence

    Sequence plays a major role in the calculation and appearance of payslip lines. For example, a sequence defined on a rule calculating the Gross should always be greater than the sequence's given on Allowance's rules, else it won't be considered in the calculation of Gross value.

- *Active* : If **False**, it will allow you to hide the salary rule without removing it.
- *Appears on Payslip* : If **False**, it won't appear on the payslip but will be considered in the calculation.
- *Condition Based on* : Consider a rule on the basis of some condition.

1. ``Always True`` : As the name implies the condition is always True and hence rule will always be considered in the Payslip calculation.

2. ``Range`` : The rule will be considered if it falls under a particular range.

  - *Range Based on* : You can provide the base value for range by using the above mentioned variable. For example, ``contract.wage``. This will take the wages mentioned on contract.
  - *Minimum Range* : The minimum amount applied for this rule.
  - *Maximum Range* : The maximum amount, applied for this rule.

3. ``Python Expression`` : You can specify your condition by python expression.

  - *Python Condition* : The expression can be written using the above mentioned variable. For example, ``result = rules.NET > categories.NET * 0.10`` .

- *Contribution Register* : Eventual third party involved in the salary payment of the employees.Used in report.

- *Amount Type* : The computation type for the rule amount. There are three types available to compute the amount.i.e ``Fixed Amout, Percentage, Python Code``.

1. ``Fixed Amount`` : As the name indicates the amount is fixed.

  - *Quantity* : For e.g. A rule for Meal Voucher having fixed amount of 1€ per worked day can have its quantity defined in expression like ``worked_days.WORK100.number_of_days`` which will then be multiplied with the amount.
  - *Fixed Amount* : An amount for a rule.

2. ``Percentage`` : Here you can calculate the amount through percentage.

  - *Percentage based on* : You can provide a base value for type percentage by using the above mentioned variable. For example, If you want to give 5% of wages for Provident Fund then you have to specify percentage based on as contract.wage.
  - *Quantity* : For example, a rule for Meal Voucher having fixed amount of 1€ per worked day can have its quantity defined in expression like ``worked_days.WORK100.number_of_days`` which will then be multipied with the calculated percentage amount.
  - *Percentage* : Provide Percentage.

3. ``Python Code`` : You can specify your condition by python expression.

  - *Python condition* : For example, If you want to calculate Gross then you can write your expression like ``result = categories.BASIC + categories.ALW`` where ``BASIC`` and ``ALW`` are salary rule categories code.

- *Child Rules* : It is used to assign child rules.
- *Inputs* : It is used when you want to provide some Input.

  - *Code* : A code for an input that can be used in salary rule. Code must be unique.
  - *Salary Rule Input* : Selection of salary rule.
  - *Description* : Description for an input.

- *Description* : Description regarding the rule.

After entering the salary rule information click Save.

.. note::

    :guilabel:`Sign of amount`

    If you are defining a rule for Allowance then make sure that the **amount** , **percentage** or **python code** you enter is *positive*. And if its for Deduction then it has to be *negative*.

    :guilabel:`Python Expression`

    If you are using python code then returned value has to be set in the variable *result*.

    You can also use the method() in your expression.
    There is a sum() method available for three objects/variables i.e.payslip, worked_days, inputs. They are:

    * payslip.sum(code, from_date, to_date)
    * worked_days.sum(code, from_date, to_date)
    * inputs.sum(code, from_date, to_date)

Salary Structure
----------------

Using the menu :menuselection:`Human Resources --> Configuration --> Payroll --> Salary Structure` you can define salary structure.

.. figure:: images/salary_structure.png
   :align: center
   :scale: 80

   *Salary Structure for an employee*

You can configure the following information:-

- *Name* : A name for a salary structure.
- *Reference* : A code for a salary structure. It must be unique.
- *Parent* : Select a structure whose rules you want to inherit.
- *Salary Rules* : Add the salary rules which you want to provide under your structure.

After entering the salary structure information click Save.

Contracts
---------

We need to define a contract for an employee which will be used during the payslip generation.
Using the menu :menuselection:`Human Resources --> Human Resources --> Contracts` you can define contract.

.. figure:: images/payroll_contract.png
   :align: center
   :scale: 80


   *Contract for an employee*

Installation of payroll module adds the following fields on contract:-

- *Salary Structure* : Salary structure for payslip.
- *Scheduled Pay* : When a salary/wages are scheduled to be paid. e.g. monthly, weekly, quarterly, etc

After entering the contract information click Save.

Employee Payslips
-----------------

Using the menu :menuselection:`Human Resources --> Payroll --> Employee Payslips` you can generate payslips.

.. figure:: images/payslip.png
   :align: center
   :scale: 80

   *Employee Payslip*

You can configure the following information:-

- *Employee* : Select an employee.
- *Reference* : Slip number.
- *Contract* : Select a contract to be considered for payslip.
- *Structure* : Salary Structure for generating payslip lines.
- *Description* : Description of payslip.
- *Credit Note* : If **True**, indicates this payslip has refund of another.
- *Date From* : The beginning date of pay period.
- *Date To* : The last date of pay period.

On the selection of an employee the Reference, Contract, Structure, Description, Worked Days and Input data ( if you have a rule that has an input data) fields will be automatically filled.

Click on the :guilabel:`Compute Sheet` button will fill the payslip lines based on the rules defined in your salary structure.(In :guilabel:`Salary Computation` tab)
Payslip lines will appear and will be calculated based on the sequence provided on salary rules. Allowances and Deductions will be shown in positive and negative values respectively.

:guilabel:`Details By Salary Rule Category`: It displays the rules grouped by its categories.

:guilabel:`Worked Days & Inputs`:- It displays the worked days and inputs.

1.	*Worked Days* : The no of days and hours an employee has worked. It will be computed on employee onchange. It calculates the number of working days and hours on the basis of Working Schedule provided on contract. It also calculates the leaves.

    - *Description* : Description regarding your working or leave day.
    - *Code* :  Code for Payslip Worked Days.
      .. note:: You cannot change the code for working days i.e.'WORK100'.
    - *Number of Days* : Number of Days an employee has worked or taken leave.
    - *Number of Hours* : Number of Hours for which an employee has worked or taken leave.
    - *Contract* : Contract to be applied for Payslip Worked Days.

2.	*Other Input* : It is used when you want to provide some incentives, commissions, etc. Input Data comes from the rules having Inputs. You need to provide an amount through Input Data of payslip.

    - *Description* : Description for Payslip Input.
    - *Code* : A code for Payslip Input.
    - *Amount* : The amount for an incentive.
    - *Contract* : Contract to be applied for Payslip Input.

:guilabel:`Other Information` : - It holds the information regarding the company, payment, notes, etc.

 
- *Company* : The company.
- *Payslip Batches* : Name of Payslip Batch through which payslip is generated.
- *Made Payment Order* : If **True**, the payment is made.
- *Notes* : Some additional information related to payslip.

Click on the Confirm button when the payslip is fully calculated and the Payment is made. It will change the state to ``Done``.

Payslips Batch
--------------

Using the menu :menuselection:`Human Resources --> Payroll --> Payslips Batches` you can create payslips for various employees at a time.
Its like a register which holds payslips of various employees created through ``Generate Payslips`` wizard.

.. figure:: images/payslips_run.png
   :align: center
   :scale: 80

   *Payslips Batch*

You need to configure the following:-

- *Name* : A name for Payslips Run.
- *Date From* : The beginning date of pay period which will be the Date From for payslips to be created.
- *Date To* : The last date of pay period which will be the Date To for payslips to be created.
- *Credit Note* :If **True**, indicates that all payslips generated from here are refund payslips.

Click on the *Generate Payslips* wizard will let you choose the employees for which you want to generate payslips.

.. figure:: images/generate_payslip_wizard.png
   :align: center
   :scale: 80

   *Generate Payslips wizard*

- *Payslips* : It holds the newly generated Payslips through wizard.

A click on the Close button of Payslips Batch changes the state to ``Close``.

Contribution Registers
----------------------

Using the menu :menuselection:`Human Resources --> Configuration --> Payroll --> Contribution Registers` you can create a Contribution Register.

.. figure:: images/contribution_register.png
   :align: center
   :scale: 80

   *Contribution Registers*

You need to configure the following:-

- *Name* : A name for the Contribution Register.
- *Company* : Contribution Register belonging to a company.
- *Description* : Description related to Contribution Register.

After creating a register you can assign it on Salary rule.
When Payslip is created, payslip lines generated through salary rules having a contribution register will be linked with that register.
To see the payslip lines related to a contribution register go to that particular register and print the ``Payslip Lines report``.

Employee Payslip PDF Report
---------------------------

You can print the Employee Payslip PDF Report from the view of Employee Payslips from Print button.

.. figure:: images/payslip_report.png
   :align: center
   :scale: 80

Payslip Details PDF Report
--------------------------

You can print the Payslip Details report from the view of Employee Payslips. It prints the report grouped by Salary Rule Category.

.. figure:: images/payslip_details_report.png
   :align: center
   :scale: 80

Payslip Lines PDF Report
------------------------

You can print the Payslip Lines report from the view of Contribution Registers. It prints the Payslip Lines by Contribution Register.

.. figure:: images/contribution_register_report.png
   :align: center
   :scale: 80


