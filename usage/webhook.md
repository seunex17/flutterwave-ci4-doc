# Webhook

{% hint style="info" %}
First make sure you place the bellow namespace at the topmost of you codebase to use the classes.
{% endhint %}

```php
use Seunex17\FlutterwaveCi4\Flutterwave\Webhook;
```

Webhooks are an important part of your payment integration. They allow Flutterwave notify you about events that happen on your account, such as a successful payment or a failed transaction.

A webhook URL is an endpoint on your server where you can receive notifications about such events. When an event occurs, we'll make a POST request to that endpoint, with a JSON body containing the details about the event, including the type of event and the data associated with it.

After creating and setting up your webhook url in flutterwave, You also need to disable CSRF in filter because flutterwave always send in a post request.

This package currently support successful payment event which you can access the same property as transaction verification above.

## **Webhook Verification**

When enabling webhooks, you have the option to set a secret hash. Since webhook URLs are publicly accessible, the secret hash allows you to verify that incoming requests are from Flutterwave. You can specify any value as your secret hash, but we recommend something random. You should also store it as an environment variable on your env file env file `<FLUTTERWAVE_WEBHOOK_SECRET>`

```php
   if (Webhook::verifyWebhook())
   {
      // Continue reading the webhook data
   }
```

***

## **Successful webhook data**

As said ealier this use the same property as transaction verification table above.

```php
   Webhook::data()->status(); // Return the status message. See table above for more properties
```

***

## **Retrieve webhook event**

```php
   Webhook::webhookEvent();
```
