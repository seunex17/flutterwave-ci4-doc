# Collecting Payments

{% hint style="info" %}
First make sure you place the bellow namespace at the topmost of you codebase to use the classes.
{% endhint %}

```php
use Seunex17\FlutterwaveCi4\Flutterwave\CollectPayment;
```

## Flutterwave Standard

he SDK provides you with the easy methods of making collections via the hosted flutterwave standard method.

```php
   $data = [
	'tx_ref' => time(), // Can be replace with your unique ref code
	'amount' => '500',
	'currency' => 'NGN', // or EUR or GBP for EU Collection.
	'meta' => [
	    'product_id' => 1,
	    'product_sku' => 'sku_1234'
	  ], // This meta param is optional just to send extra info
	'customer_email' => 'johndoe@mail.com',
	'customer_name' => 'John Doe',
	'redirect_url' => base_url('verify'),
	];

  return CollectPayment::standard($data);
```

***

## Card Charge

You can also charge customer card directly from you website using the Card charge method.

```php
   $data = [
	  'card_number' => "***************",
	  'cvv' => '564',
	  'expiry_month' => '09',
	  'expiry_year' => '24',
	  'redirect_url' => base_url('verify'),
	  'currency' => 'NGN', // or EUR or GBP for EU Collection.
	  'amount' => '500',
	  'fullname' => 'John Doe',
	  'email' => 'john@mail.com',
	  'tx_ref' => time(), // Can be replace with your unique ref code
    ];

    echo '<pre>';
    var_dump(CollectPayment::card($data));
    echo '<pre>';
```

## Tokenize Charge

This feature allow you to charge customer card. It is usually used for recurring payment. Where you can automatically charge customer card without physical interaction. Customer must first make a payment on your website. After the payment was successful you can securely store teh customer card token in you database. This token will be used to chage customer card. And take note that the token must match the customer email every time you want to initiate a tokenized charge.

```php
  $data = [
      'token' => "flw-t1nf-2dd950bd8f3c966d5a5453128c1ed517-m03k",
      'country' => 'NG',
      'first_name' => 'John',
      'last_name' => "Doe",
      'currency' => 'NGN',
      'tx_ref' => time(),
      'amount' => '500',
      'email' => 'johndoe@mail.com',
      'narration' => 'Cable subscription'
   ];

   echo '<pre>';
   var_dump(CollectPayment::tokenizeCharge($data));
   echo '<pre>';
```
