# XML Message Structure

## Overview <a href="#soapmessagestructure-overview" id="soapmessagestructure-overview"></a>

All messages to and from AppConnect must be XML messages. And must be sent with a Bearer Token for authentication purposes. The following example is a complete XML message (this one shows an OTA\_PingRQ message payload)

### Bearer Token

The App will have to exchange credentials for a bearer token, by POSTING a JSON request to  the URL:

```
https://hoteliers.guru/channel-manager/interface/app/token
```

#### Request

Replace the values with credential details and id's received from the Channel Manager. If any of the details are wrong, or don't match, you will receive a 403 response.

```
{
  "aud": "<< YOUR APP CODE IN CHANNEL MANAGER >>",
  "sub": {
    "hotel_id": "<< CHANNEL MANAGER HOTEL ID >>"
  },
  "credentials": {
    "client_id":"<< YOUR GIVEN client_id >>", 
    "client_secret":"<< YOUR GIVEN client_secret >>"
  }
}
```

#### Response

Once token is received, you can proceed and use it for requests until it expires.

```
{
  "token":"<< BEARER TOKEN >>"
}
```

## XML Sample <a href="#soapmessagestructure-xmlsample" id="soapmessagestructure-xmlsample"></a>

Use the token received in the Authorization Header, as Bearer Token. If the token are invalid or has expired, you will receive a 403 response.

#### Request

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_PingRQ xmlns="http://www.opentravel.org/OTA/2003/05" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727" TimeStamp="2022-04-08T14:22:30+07:00" Version="1.0">
    <EchoData>Hello App</EchoData>
</OTA_PingRQ>
```

#### Response

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_PingRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:31+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <EchoData>Hello App</EchoData>
</OTA_PingRS>
```
