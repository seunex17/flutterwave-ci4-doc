# Verifications

{% hint style="info" %}
First make sure you place the bellow namespace at the topmost of you codebase to use the classes.
{% endhint %}

```php
use Seunex17\FlutterwaveCi4\Flutterwave\Verification;
```

## Verify transaction

After collecting payment from our customer. In the [Collecting Payment section](collecting-payments.md) we set a redirect page where flutterwave will send our user to either complete payment or cancel it. In the redrected page (method) add this below code to verify you payment.

```php
   if (!$txn = $this->request->getGet('transaction_id'))
   {
	  // Payment was cancel by customer or another thing else.
	  // Redirect user to error page
	  return 'payment was cancel';
   }

   try
   {
	  $response = Verification::transaction($txn);
	  echo $response->status();

	  // the response above give you an array of the transaction report
	  // You can now access each report value like this: $response->amount
	  // Remember to check if amount paid is same as you product amount.
   }
   catch (\Exception $e)
   {
      return $e->getMessage();
   }
```

### Available method for accessing verified transaction

| Method            | Type   | Description                                                         |
| ----------------- | ------ | ------------------------------------------------------------------- |
| id                | int    | Return the id of the transaction                                    |
| transactionRef    | string | Return the transaction references                                   |
| flutterwaveRef    | string | Flutterwave transaction references                                  |
| deviceFingerprint | string | Return the device fingerptin of the customer                        |
| amount            | float  | Return the amount set by the merchant                               |
| currency          | string | Return the ISO currency of the transaction                          |
| chargeAmount      | float  | Return the actual amount paid by teh customer                       |
| fee               | float  | Return the application fee impose by flutterwave on teh transaction |
| merchantFee       | float  | Return the flutterwave charged the merchant not the customer        |
| processorResponse | string | Return the payment processor response                               |
| authModel         | string | Return the payment auth model                                       |
| ipAddress         | string | Return the ip address of teh customer                               |
| narration         | string | Return the narration of the transaction                             |
| status            | string | Return the transaction status                                       |
| paymentType       | string | Retun the payment type e.g card, ussd, bank, etc                    |
| accountId         | int    | Return teh flutterwave account id number                            |
| firstCardPan      | string | Return the customer card first six digit                            |
| lastCardPan       | string | Return teh customer card last four digit                            |
| cardIssuer        | String | Return the customer card issuer                                     |
| cardCountry       | string | Return the country name of the card                                 |
| cardType          | string | Return teh customer card type                                       |
| cardToken         | string | Return the token of the card issue by flutterwave                   |
| cardExpire        | string | Return the card expiration date                                     |
| meta              | object | Return teh customer data you set when initializing the payment      |
| amountSettled     | float  | Return the total amount settle to the merchant account              |
| customerEmail     | string | Return customer email address                                       |
| customerName      | string | Return customer full name                                           |
| customerPhone     | string | Return customer phone number                                        |

\
