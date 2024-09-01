# Installation

### Installation via Composer

To install the package via Composer, run the following command.

```shell
composer require seunex17/flutterwave-ci4
```

### Initialization

Create a .env file and follow the format of the `env` file Save your PUBLIC\_KEY, SECRET\_KEY in the `.env` file

```shell
cp env .env
```

Your `.env` file should look this.

```
FLUTTERWAVE_PUBLIC_KEY=<YOUR FLUTTERWAVE PUBLIC KEY>
FLUTTERWAVE_SECRET_KEY=<YOUR FLUTTERWAVE SECRET KEY>
FLUTTERWAVE_ENCRTYPTION_KEY=<YOUR FLUTTERWAVE ENCRYPTION KEY>
FLUTTERWAVE_PAYMENT_TITLE=<YOUR BUSINESS NAME>
FLUTTERWAVE_PAYMENT_LOGO=<YOUR BUSINESS LOGO URL>
FLUTTERWAVE_WEBHOOK_SECRET=<YOUR WEBHOOK SECRET HASH>
```

{% hint style="info" %}
The infomation above are very sensitive make sure your .env file not public accessable.
{% endhint %}
