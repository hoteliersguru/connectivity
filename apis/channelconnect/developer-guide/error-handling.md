# Error Handling

## Error Responses to ChannelConnect <a id="ErrorHandling-ErrorResponsestoSiteConnect"></a>

{% hint style="info" %}
Returning Errors to ChannelConnect

Errors must be returned within a 'SOAP Envelope' and use the defined response message container depending on the message being responded to. Please see the relevant parts of our specification within the Room Retrieval & Inventory API and Inventory API sections for more information on each error response message.

If the error is specifically related to **application level** errors, please **do not** respond any other error types \(HTTP etc.\). If you have **server level** issues, then it is OK to respond with HTTP standard error codes.
{% endhint %}

It is expected that your OTA has a robust error handling process in place. This includes a queuing mechanism and a robust retry strategy. An error response should contain a short description of the error to assist our support teams.**Sample Error Response**

```text
<OTA_HotelAvailNotifRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2020-09-10T16:20:32+0700" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc">
    <Errors>
        <Error Type="6" Code="392">Cannot find hotelier with code ABC</Error>
    </Errors>
</OTA_HotelAvailNotifRS>
```

#### Errors

| Element |  | Description / Format |
| :--- | :--- | :--- |
| Errors | 0..n |  |
|   Error | 1 |  |
|    @Type | 1 | The type of error. For valid values see [OTA Error Warning Types](error-handling.md#ota-error-warning-types). |
|    @Code | 0..1 | The specific error code if any. See [OTA Error Codes](error-handling.md#ota-error-codes) and the errors returned by specific Operations. |
|    @Tag | 0..1 | For validation errors or missing fields errors; the tag in the XML request that caused this error \(in XPath format\). |

## Recommended OTA Error Codes

ChannelConnect recommends the following error codes from OTA Error Codes \(ERR\).

### OTA Error Warning Types

| Error Warning Type | Code | Description |
| :--- | :--- | :--- |
| Unknown | 1 | Indicates an unknown error. |
| No Implementation | 2 | Indicates that the target business system has no implementation for the intended request. |
| Biz rule | 3 | Indicates that the XML message has passed a low-level validation check, but that the business rules for the request message were not met. |
| Authentication | 4 | Indicates the message lacks adequate security credentials. |
| Authorization | 6 | Indicates the message lacks adequate security credentials. |
| Required field missing | 10 | Indicates that an element or attribute that is required in by the schema \(or required by agreement between trading partners\) is missing from the message. |
| Processing exception | 12 | Indicates that during processing of the request that a not further defined exception occurred. |

### OTA Error Codes

**Error Codes - General**

These are recommended Error Codes to be returned for general errors

| Error Codes | Code | Description |
| :--- | :--- | :--- |
| System currently unavailable | 187 |  |
| Invalid property code | 400 |  |
| System error | 448 |  |
| Unable to process | 450 |  |

**Error Codes - Updates**

These are recommended Error Codes to be returned for update errors

| Error Codes | Code | Description |
| :--- | :--- | :--- |
| Invalid date | 15 |  |
| Invalid rate code | 249 |  |
| Invalid value | 320 |  |
| Required field missing | 321 |  |
| Invalid hotel | 361 |  |
| Hotel not active | 375 |  |
| Invalid hotel code | 392 |  |
| Invalid room type | 402 |  |
| Rate does not exist | 436 |  |
| Authorization error | 497 |  |
| Room or rate not found | 783 |  |
| Rate not loaded | 842 |  |

## Error Responses from ChannelConnect <a id="ErrorHandling-ErrorResponsesfromSiteConnect"></a>

When contacting our Application Operations team, please provide as much information as possible in relation to the problematic request\(s\). This should at the very least be the EchoToken and TimeStamp related to the request. Where possible, the actual **redacted** request that was made to ChannelConnect will allow the quickest turn around time.

If the response contains an OTA message with an 'Error' element then the reservation can not be processed because some data is invalid. This could be, for example, if required data is missing or if the credentials/hotel code are incorrect and the message will not process until the error is fixed. If the error is that a required element or attributes are missing, the implementation will need to be adjusted to send the required data. If the error is to do with credentials, please check that the correct username/password is sent. If the error is an invalid hotel code, contact the hotel to make sure they have the correct hotel code configured in The Channel Manager.

### OTA Error Warning Types <a id="ErrorHandling-OTAErrorWarningTypes"></a>

ChannelConnect will use the following OTA error types from OTA Error Warning Type \(EWT\)

| Error Warning Type | Code | Description |
| :--- | :--- | :--- |
| Unknown | 1 | Indicates an unknown error. |
| Biz rule | 3 | Indicates that the XML message has passed a low-level validation check, but that the business rules for the request message were not met. |
| Authentication | 4 | Indicates the message lacks adequate security credentials. |
| Authorization | 6 | Indicates the message lacks adequate security credentials. |
| Required field missing | 10 | Indicates that an element or attribute that is required in by the schema \(or required by agreement between trading partners\) is missing from the message. |
| Processing exception | 12 | Indicates that during processing of the request that a not further defined exception occurred. |

### HTTP Status Codes

| Response Code | Description |
| :--- | :--- |
| 200 OK | When the message is successfully processed. The response content is a valid OTA/HTNG response success message. |
| 400 Bad Request | This code is returned in two cases: When the message could be parsed but resulted in one or more errors. In this case the response content is a valid OTA/HTNG response error message. When the message could not be parsed or is not recognized. In this case the response content is a generic OTA/HTNG “No Implementation” error response \(OTA\_ErrorRS\). |
| 401 Unauthorized | When authentication failed or is missing. When authentication fails the rest of the message is not parsed, the response content is a generic OTA/HTNG “Authentication” error response \(OTA\_ErrorRS\), and the WWW-Authenticate header is set. |
| 403 Forbidden | When the channel manager account is not authorized to make changes for a hotel in the request. The response content is a valid OTA response “Authorization” error message. |
| 406 Not Acceptable | If the Accept header is set in the request, but it does not contain text/xml. The response content is a generic OTA/HTNG “Processing Exception” error response \(OTA\_ErrorRS\). |
| 411 Length Required | If the Content-Size header is not set in the request. The response content is a generic OTA/HTNG “Processing Exception” error response \(OTA\_ErrorRS\). |
| 415 Unsupported Media Type | If the Content-Type header in the request is not set to “text/xml” or uses an unsupported charset. The response content is a generic OTA/HTNG “Processing Exception” error response \(OTA\_ErrorRS\). |
| 500 Internal Server Error | Unexpected server error. This error indicates an unforseen and unhandled condition in the server hence a generic error response is returned, which may contain further error information. Note: when this http status is returned the message should be retried. |

