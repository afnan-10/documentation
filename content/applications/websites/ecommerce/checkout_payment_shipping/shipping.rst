========
Delivery
========

Odoo eCommerce allows you to configure various delivery methods, enabling customers to choose
their preferred option at :doc:`checkout <checkout>`. These methods include :ref:`external providers
<ecommerce/delivery/external-provider>`, :ref:`custom options <ecommerce/delivery/custom-method>`
such as flat-rate or free shipping, local carriers via
:doc:`Sendcloud <../../../inventory_and_mrp/inventory/shipping_receiving/setup_configuration/sendcloud_shipping>`
or :ref:`Based on Rules <inventory/shipping/rules>`, and :ref:`in-store pickup
<ecommerce/delivery/instore-pickup>`.

.. _ecommerce/delivery/external-provider:

External provider integration
=============================

To handle product delivery, you can connect your database to :doc:`third-party shipping carriers
<../../../inventory_and_mrp/inventory/shipping_receiving/setup_configuration/third_party_shipper>`
like :doc:`FedEx <../../../inventory_and_mrp/inventory/shipping_receiving/setup_configuration/fedex>`,
:doc:`UPS <../../../inventory_and_mrp/inventory/shipping_receiving/setup_configuration/ups_credentials>`,
or :doc:`DHL <../../../inventory_and_mrp/inventory/shipping_receiving/setup_configuration/dhl_credentials>`.
A shipping connector links to these providers, automating :doc:`tracking labels
<../../../inventory_and_mrp/inventory/shipping_receiving/setup_configuration/labels>` and shipping
processes.

To enable a third-party delivery provider, go to :menuselection:`Website --> Configuration -->
Settings`, scroll to the :guilabel:`Delivery` section, select the desired delivery provider(s),
and :guilabel:`Save`.

Go to :menuselection:`Website --> Configuration --> Delivery Methods` and select the delivery method
in the list to :ref:`configure it <inventory/shipping_receiving/configure-delivery-method>`.

.. seealso::
   :doc:`Third-party shipping carriers
   <../../../inventory_and_mrp/inventory/shipping_receiving/setup_configuration/third_party_shipper>`

.. important::
   The field used to define additional fees **must** be filled **in your third-party delivery
   provider account**, even if you do not plan to charge customers any additional fee. If you do not
   want to apply a fee, enter `0`. If the field is left empty, the delivery price cannot be
   calculated, and an error message prompts the customer to select an alternative delivery method.

Margin on delivery rate
-----------------------

To add an additional fee to the base shipping rate (e.g., to cover extra costs), log into your
carrier account and set the desired fee in the related field. The shipping connector retrieves this
fee and includes it in the final price at checkout. Contact your carrier for further assistance
with this configuration.

Alternatively, enter `0` in your third-party shipping provider account, then set the fee in Odoo.
To do so, access the desired :ref:`shipping method's form
<inventory/shipping_receiving/configure-delivery-method>` and enter the fee in the :guilabel:`Margin
on Rate` field to add a percentage to the shipping costs and/or the :guilabel:`Additional margin`
field to add a fixed amount.

.. important::
   The field used to define additional fees cannot be left empty in your third-party shipping
   provider account.

.. _ecommerce/delivery/custom-method:

Custom delivery method
======================

Custom delivery methods must be created, for example:

- to integrate delivery carriers through :doc:`Sendcloud
  <../../../inventory_and_mrp/inventory/shipping_receiving/setup_configuration/sendcloud_shipping>`;
- to configure specific rules (e.g., to offer free shipping for orders above a specific amount) for
  a specific provider;
- to configure :ref:`Fixed Price <inventory/shipping/fixed>` shipping or shipping
  :ref:`Based on Rules <inventory/shipping/rules>`.

To create a custom delivery method, go to :menuselection:`Website --> Configuration -->
delivery Methods`, click :guilabel:`New` and fill in the :ref:`fields
<inventory/shipping_receiving/shipping-methods-details>`.

In the :guilabel:`Provider` field, select :ref:`Based on Rules <inventory/shipping/rules>`,
:ref:`Fixed Price <inventory/shipping/fixed>`, or :ref:`Pickup in store <inventory/shipping/pickup>`
if the shiping method does not involve any specific provider.

.. tip::
   Upon :ref:`configuring <inventory/shipping_receiving/configure-delivery-method>` a delivery
   method, you can:

   - restrict it :doc:`to a specific website <../../website/configuration/multi_website>` by
     selecting it in :guilabel:`Website` field;
   - use the :guilabel:`Destination availability` tab to filter the delivery carriers displayed
     based on the customer's area;
   - click the :guilabel:`Test Environment` smart button to switch to
     the :guilabel:`Production Environment`, then click :guilabel:`Unpublished` to
     :guilabel:`Publish` the delivery method and make it available to website visitors.

.. _ecommerce/delivery/instore-pickup:

Pick up in store
================

To allow customers to reserve products online and pay for/collect them in-store, go to
:menuselection:`Website --> Configuration --> Settings`. Scroll to the :guilabel:`Delivery` section,
enable :guilabel:`Click & Collect`, and :guilabel:`Save`.

Next, click :icon:`fa-arrow-right` :guilabel:`Configure Pickup Locations` to
:ref:`set up <inventory/shipping_receiving/configure-delivery-method>` your delivery method.
Ensure the :guilabel:`Provider` field is set to :guilabel:`Pickup in store`. Under the
:guilabel:`Stores` tab, click :guilabel:`Add a line` to add the :guilabel:`Warehouse` and its
:guilabel:`Address` where customers can collect their orders, and the :guilabel:`Opening hours`.

Once your set up is complete, click the :guilabel:`Unpublish` button to change the status to
:guilabel:`Publish`, making the delivery method available to customers. When the product is in
stock, a **location selector** is displayed on :doc:`product <../products>` and
:doc:`checkout <checkout>` pages.

.. note::
   - Each warehouse must have a **complete address** to ensure its location is accurately displayed to
     customers. Incomplete addresses prevents the warehouse from being shown.
   - **Services** are not available for the pick up in store option.
   - Customers cannot select a pick-up location if the product is out of stock at that location. The
     :ref:`Continue selling <ecommerce/products/stock-management>` option for out-of-stock products
     is not supported.
   - If the :ref:`Show Available Qty <ecommerce/products/stock-management>` option is enabled for a
     product, customers can view the stock quantity available for each warehouse in the location
     selector on the product page.
   - Customers cannot complete the :doc:`checkout <checkout>` if the selected products are out of
     stock at the chosen pick-up location.

Delivery method's availability
==============================

You can tailor a delivery method’s availability based on the order’s content or destination.

To do so, go to :menuselection:`Website --> Configuration --> Delivery Methods` and select the
desired method.

From the :guilabel:`Destination` section you can restrict the availability to specific
:guilabel:`Countries`, and from the :guilabel:`Content` section you can set a :guilabel:`Max Weight`
or :guilabel:`Max Volume`, fill in the :guilabel:`Must Have Tags` or :guilabel:`Excluded Tags`
fields.
