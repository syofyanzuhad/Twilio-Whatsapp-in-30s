# Send WhatsApp Messages using the Twilio API Within 30 Seconds

## Getting Started

Clone the Repo to your prefered directory. 
On your terrminal, run `cd Twilio-Whatsapp-Php` then 
run `composer install` to install project dependancies.

Rename file `.env.example` to `.env` file and add the following keys after obtaining the relevant values from your twilio dashboard
```
TWILIO_SID=your_twilio_sid
TWILIO_TOKEN=your_twilio_token
```
Activate your [WhatsApp Sandbox](https://www.twilio.com/blog/2018/08/twilio-whatsapp-api.html)

Edit your `twilioWhatsAppMessaging.php` with your whatsapp number.

```
<?php

require __DIR__ . "/vendor/autoload.php";

use Twilio\Rest\Client;

$dotenv = Dotenv\Dotenv::create(__DIR__);
$dotenv->load();

$twilioSid    = getenv('TWILIO_SID');
$twilioToken  = getenv('TWILIO_TOKEN');

$twilio = new Client($twilioSid, $twilioToken);

$message = $twilio->messages
                    ->create(
                        "whatsapp:+6281326743694",
                        array(
                                "body" => "Greetings from Twilio :-)",
                                "from" => "whatsapp:+14155238886"
                            )
                    );
```

Run `php twilioWhatsAppMessaging.php`

Voila! We have sent out first WhatsApp message!. 

## What you need 

1. Php (of course) must included php7.0 + php7.0-curl.
2. Composer.
3. Twilio account.
