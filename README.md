# Travis Virtual Assitant API
This document provides guidance on integrating the Travis API with your CRM system to automatically transfer contact information captured through Travis cards provided from https://traqr.co.uk 

Travis has one mission: to effortlessly schedule callbacks for you!
With a simple tap, Travis springs into action, engaging with the person and arranging a convenient time for you to connect.

To use the Travis API you need to purchase a Travis card from: https://traqr.co.uk/products/travis-virtual-assistant

## Retrieving Contact Information
The Travis API delivers contact information in JSON format, containing an array of objects. Each object represents a contact and includes the following properties:

* id: Unique identifier for the contact (integer)
* phone_number: Contact's phone number (string)
* profile_name: Contact's name (string)
* day: Preferred callback day (string)
* time: Preferred callback time (string)
* client_message: Message sent by the contact (string)

```
JSON
[
  {
    "id": 324241,
    "phone_number": "whatsapp:",
    "profile_name": "Tom Wayne",
    "day": "Monday",
    "time": "Morning",
    "client_message": "I'm interested in getting a social media manager"
  },
  {
    "id": 1322131,
    "phone_number": "whatsapp:",
    "profile_name": "Steve Manson",
    "day": "Monday",
    "time": "Morning",
    "client_message": null
  },
  {
    "id": ,
    "phone_number": "whatsapp:",
    "profile_name": "Craig",
    "day": "Monday",
    "time": "Afternoon",
    "client_message": "Please call me around 2pm"
  }
]
```

## Code Examples
The following code snippets demonstrate how to retrieve contact information using the Travis API in various programming languages:

```
Ruby
require 'net/http'
require 'uri'
require 'json'

# Replace with your actual API key
api_key = 'YOUR_API_KEY'

url = URI("https://traqr.co.uk/api-call-travis?api_key=#{api_key}")

req = Net::HTTP::Get.new(url)

res = Net::HTTP.start(url.host, url.port, use_ssl: true) { |http|
  http.request(req)
}

if res.is_a?(Net::HTTPSuccess)
  data = JSON.parse(res.body)
  puts data
else
  puts "Error: #{res.code}"
end
```

To see more code examples please visit: https://traqr.co.uk/docs/travis-api-now-connect-seamlessly-to-your-crm-through-our-api

