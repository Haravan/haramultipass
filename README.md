haramultipass
============

Haravan Multipass module for Node.js



[Haravan](https://www.haravan.com/) provides a mechanism for single sign-on known as Multipass.  Multipass uses an AES encrypted JSON hash and haramultipass provides functions for generating tokens

More details on Multipass with Haravan can be found [here](https://docs.haravan.com/blogs/ui-integrations/1000017816-multipass).

## Installation
<pre>
    npm install haramultipass
</pre>

## Usage

To use Multipass an Enterprise / Plus plan is required. The Multipass secret can be found in your shop Admin (Settings > Checkout > Customer Accounts).
Make sure "Accounts are required" or "Accounts are optional" is selected and Multipass is enabled.

``` js
  var Haramultipass = require('haramultipass');

  // Construct the Haramultipass encoder
  var haramultipass = new Haramultipass("HARAVAN MULTIPASS SECRET");

  // Create your customer data hash
  var customerData = { email: 'test@example.com', remote_ip:'USERS IP ADDRESS', return_to:"http://some.url"};

  // Encode a Multipass token
  var token = haramultipass.encode(customerData);

  // Generate a Haravan multipass URL to your shop
  var url = haramultipass.generateUrl(customerData, "yourstorename.myharavan.com");

  // Generates a URL like:  https://yourstorename.myharavan.com/account/login/multipass/<MULTIPASS-TOKEN>
```