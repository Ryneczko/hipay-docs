# Split payments

## How it works

When an order is created with a HiPay Fullservice split payment method, x installments are created (x depending on the selected payment profile).

A split order is validated when the payment is captured.
Upon payment capture, x installments are generated for this order.
The order is fully invoiced (but not fully captured in the HiPay Fullservice platform) and you can get ready for shipment.

The first installment is always debited on the payment date in Capture mode or when you capture manually in Authorization mode.

Then, with a Cron task (please see [[Cron configuration and task information]]), each installment is debited on its respective payment date.

## Split payment methods

The HiPay Fullservice module for Magento 2 includes two payment methods for split payments:

* HiPay Fullservice Hosted Page Split Payment,
* HiPay Fullservice Credit Card Split Payment,

based on the **HOSTED** or **API** mode.  

Before using them, you need to create payment profiles.

## Payment profiles

A payment profile defines how the payment is split.

In your Magento Admin Panel, select `Sales` => [HiPay Fullservice] `Payment Profiles`.

![legend](images/payment_profiles_list.png)

Click on *"Create New Payment Profile"*.

Fill in the form:

* *Name*: Public name for your payment profile
* *Period Unit*: Unit for billing during the subscription period
* *Period Frequency*: Number of billing periods that make up one billing cycle
* *Period Max Cycles*: Number of billing cycles for the payment period

E.g.: If you want to split the amount in 3 installments with 1 billing per month:
* Period Unit: `month`
* Period Frequency: `1`
* Period Max Cycles: `3`

Don't forget to save the information.

![legend](images/new_payment_profile.png)

### Split payment method configuration

Once you have at least one payment profile, you can configure a split payment method.

For general configuration, please refer to [[Payment methods configuration]].

Specific configuration:

|Field|Description|
|-----|----|
|Split Payment Profile|Enables to select active split payment profiles, which will be displayed during checkout so that customers can choose one of them.|

![legend](images/split_payment_config.png)

### Split payment overview

A split payment overview is available in your Magento Admin Panel in `Sales => [HiPay Fullservice] Split Payment`.

For each installment, you can edit, delete or pay it immediately.  
You can also change the payment date or the amount to pay.

**Be careful: if you are not sure what to do, please contact HiPay's Business IT Services for technical support.**

![legend](images/split_payment_list.png)

![legend](images/split_payment_edit.png)
