# Transactions

{% hint style="info" %}
First make sure you place the bellow namespace at the topmost of you codebase to use the classes.
{% endhint %}

```php
use Seunex17\FlutterwaveCi4\Flutterwave\Transaction;
```

## List all transactions

You can retrieve all transactions carried out on you flutterwave account.

```php
  $transactions = Transaction::list(); // This return an object of array.
```

***

## Refaund a transaction

Whenever your customer pay you, it is advisable to store the transaction information return by flutterwave. To create a refund we needed the amount paid and transaction id (transaction\_id).

```php
  $transactionId = "4717164";
  $amount = 500;

  Transaction::refund($transactionId, $amount);
```

***

## List all refunds

You can retrieve all refunded transactions carried out on you flutterwave account.

```php
  $refunds = Transaction::refunds(); // This return an object of array.
```

***

## Get transaction fee

This methods helps you to query the fees expected to be paid for a particular transaction. This methods only returns fees for collections i.e. inflows.

### **Flutterwave Fee**

```php
  $data = [
      'amount' => 500,
      'currency' => 'NGN',
   ];
			
  Transaction::fees($data)->flutterwaveFee();
```

### **Merchant Fee**

```php
  $data = [
      'amount' => 500,
      'currency' => 'NGN',
   ];
			
  Transaction::fees($data)->stampDutyFee();
```

### **Stamp duty Fee**

```php
  $data = [
      'amount' => 500,
      'currency' => 'NGN',
   ];
			
  Transaction::fees($data)->stampDutyFee();
```

