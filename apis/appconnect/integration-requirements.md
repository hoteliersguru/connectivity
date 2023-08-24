# Integration Requirements

## Guidelines <a href="#integrationrequirements-guidelines" id="integrationrequirements-guidelines"></a>

These guidelines are in place to ensure efficient and proper use of the AppConnect API, and the following Integration Requirements must be adhered to by all App’s that have or wish to have an interface to AppConnect.

Failure to follow these guidelines could jeopardize the App interface and, if no action is taken by the App provider to rectify non-compliance within 3 months from notification, The Channel Manager reserves the right to disable the interface till such corrections have taken place.

Please note however, that if the non-compliance of the App puts the performance to the whole The Channel Manager production environment at risk, The Channel Manager reserves the right to disable the interface immediately.

### EchoTokens

EchoTokens are essential for all requests (namely _**OTA\_HotelResNotifRQ**_) being made over AppConnect. EchoTokens ensure that each request can be uniquely identified for troubleshooting purposes in both testing and production environments.

All requests you receive from AppConnect will contain an EchoToken, and your response must mirror the EchoToken as received in the request.

NOTE: Please ensure that you implement EchoTokens that are as 'unique' as possible to ensure that log trawling for troubleshooting purposes on either side is quick and efficient. Implementing GUIDs are recommended and more information about GUID can be found - [http://en.wikipedia.org/wiki/Globally\_unique\_identifier](http://en.wikipedia.org/wiki/Globally\_unique\_identifier).

### Line-spacing

All XML requests made to AppConnect should be contained on one line with no line-spacing.

### Content-Type

The ‘Content-Type’ for all XML requests made to AppConnect must be '_text/xml; charset=utf-8_'. Any other ‘Content-Type’ will not be accepted.

### SSL/TLS

AppConnect supports TLSv1.2 and above. AppConnect does not support self-signed SSL certificates.

### Error Handling

It is expected that your App has a robust error handling process in place. This includes a queuing mechanism and a robust retry strategy. Please refer to the [Error Handling](developer-guide/error-handling.md) section of the AppConnect documentation for more information.

### Mandatory Functionality

1. All AppConnect connections **MUST** be a 2-way XML connection.
2. Partner will PUSH availability, rates and restrictions to AppConnect. AppConnect will PUSH reservations to the Partner.
3. The following functionality is mandatory
   1. Availability
   2. Stop Sell
   3. Reservation Delivery

## AppConnect API



### **Ping API**

1. The partner uses _**OTA\_PingRQ**_ to validate that the connection is setup correctly, and all credentials are in place.

### **Room Retrieval API**

1. The partner uses _**OTA\_HotelAvailRQ**_ to PULL a list of room rates available on the Channel Manager for mapping purposes.
2. Room and rate codes returned by the Retrieve Rooms API should avoid using any special characters, such as ‘@’ ‘&’ ‘<’ ‘>’ etc. where possible.

## Certification

AppConnect certification will be undertaken once development of all functionality has been completed. It is important to note that testing (including negative testing) of all developed AppConnect API functionality should be completed prior to certification. The certification process is conducted by the partner, using a certification document that The Channel Manager will provide. The certification process must be completed using information presented on the partner system, not the information presented within the partners Channel Manager test account. There is no restriction to the amount of times a partner can attempt certification.

Once certification is completed, the results will be reviewed by The Channel Manager’s API Development team. The Channel Manager and the API Development team reserve the right to delay deployment to The Channel Manager’s production environments until they are satisfied with the results.

## Test Environment Access

A Channel Manager test account will be provided for use during development. Test account access is only guaranteed during active development and should not be used for ongoing testing or for demonstration purposes. Upon completion of AppConnect certification, the test account will be disabled.

