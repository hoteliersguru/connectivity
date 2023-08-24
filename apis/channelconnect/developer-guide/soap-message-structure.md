# SOAP Message Structure

## Overview <a id="SOAPMessageStructure-Overview"></a>

All messages to and from ChannelConnect must be soap messages. They include a SOAP Security header for authentication purposes and contain the SOAP Body which contains the OTA message. The following example is a complete SOAP message \(this one shows an OTA\_HotelAvailNotifRQ message payload\)

## Soap Security Header <a id="SOAPMessageStructure-SoapSecurityHeader"></a>

The Security Header structure conveys authentication information. It is mandatory and both the /wsse:UsernameToken/wsse:Username and /wsse:UsernameToken/wsse:Password elements are mandatory. The only acceptable value for the Password/@Type attribute is e.g "&lt;wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0\#PasswordText"&gt;SECRET&lt;/wsse:Password&gt;", indicating a plain text password. Plain text password are acceptable as all communication is done over encrypted HTTP.

### Credential and Endpoint Requirements <a id="SOAPMessageStructure-CredentialandEndpointRequirements"></a>

Partners will need to provide ChannelConnect with a _**single**_ username and password to be used for [Retrieve Rooms](retrieve-rooms-api.md) and [Inventory Push](inventory-push-api/) authentication. These credentials **must** be global for all hotels using the connection, not for each individual hotel. Partners should provide ChannelConnect with a single URI endpoint for all messages.

ChannelConnect partners will be provided with a _**single**_ username and password for Reservation authentication, once the [Retrieve Rooms API](retrieve-rooms-api.md) has been completed.

## XML Sample <a id="SOAPMessageStructure-XMLSample"></a>

```text
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">

  <SOAP-ENV:Header xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
    <wsse:Security soap:mustUnderstand="1" xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
      <wsse:UsernameToken>
        <wsse:Username>USERNAME</wsse:Username>
        <wsse:Password Type="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordText">SECRET</wsse:Password>
      </wsse:UsernameToken>
    </wsse:Security>
  </SOAP-ENV:Header>
 
  <SOAP-ENV:Body xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
    <OTA_HotelAvailNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" Version="1.0" TimeStamp="2020-09-10T16:20:32+0700">
      <AvailStatusMessages HotelCode="HOTEL">
        <AvailStatusMessage BookingLimit="10">
          <StatusApplicationControl Start="2010-01-01" End="2010-01-14" InvTypeCode="A1K" RatePlanCode="GLD"/>
        </AvailStatusMessage>
      </AvailStatusMessages>
    </OTA_HotelAvailNotifRQ>
  </SOAP-ENV:Body>
 
</SOAP-ENV:Envelope>
```

