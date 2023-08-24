# Integration Requirements

## Guidelines <a href="#integrationrequirements-guidelines" id="integrationrequirements-guidelines"></a>

These guidelines are in place to ensure efficient and proper use of the ChannelConnect API, and the following Integration Requirements must be adhered to by all OTA’s that have or wish to have an interface to ChannelConnect.

Failure to follow these guidelines could jeopardize the OTA interface and, if no action is taken by the OTA provider to rectify non-compliance within 3 months from notification, The Channel Manager reserves the right to disable the interface till such corrections have taken place.

Please note however, that if the non-compliance of the OTA puts the performance to the whole The Channel Manager production environment at risk, The Channel Manager reserves the right to disable the interface immediately.

### EchoTokens

EchoTokens are essential for all requests (namely _**OTA\_HotelResNotifRQ**_) being made over ChannelConnect. EchoTokens ensure that each request can be uniquely identified for troubleshooting purposes in both testing and production environments.

All requests you receive from ChannelConnect will contain an EchoToken, and your response must mirror the EchoToken as received in the request.

NOTE: Please ensure that you implement EchoTokens that are as 'unique' as possible to ensure that log trawling for troubleshooting purposes on either side is quick and efficient. Implementing GUIDs are recommended and more information about GUID can be found - [http://en.wikipedia.org/wiki/Globally\_unique\_identifier](http://en.wikipedia.org/wiki/Globally\_unique\_identifier).

### Line-spacing

All Soap XML requests made to ChannelConnect should be contained on one line with no line-spacing.

### Content-Type

The ‘Content-Type’ for all Soap XML requests made to ChannelConnect must be '_text/xml; charset=utf-8_'. Any other ‘Content-Type’ will not be accepted.

### SSL/TLS

ChannelConnect supports TLSv1.2 and above. ChannelConnect does not support self-signed SSL certificates.

### Error Handling

It is expected that your OTA has a robust error handling process in place. This includes a queuing mechanism and a robust retry strategy. Please refer to the [Error Handling](developer-guide/error-handling.md) section of the ChannelConnect documentation for more information.

### Mandatory Functionality

1. All ChannelConnect connections **MUST** be a 2-way XML connection.
2. ChannelConnect will PUSH availability, rates and restrictions to the partner. The partner will PUSH reservations to ChannelConnect.
3. The following functionality is mandatory
   1. Availability
   2. Stop Sell
   3. Reservation Delivery

## ChannelConnect API

### **Room Retrieval API**

1. ChannelConnect uses _**OTA\_HotelAvailRQ**_ to PULL a list of room rates available on the partner channel.
2. The OTA partner must ensure only “active” room rates should be returned in the _**OTA\_HotelAvailRS**_.
3. Room and rate codes returned by the Retrieve Rooms API should avoid using any special characters, such as ‘@’ ‘&’ ‘<’ ‘>’ etc. where possible
4. Rooms rates returned by the Retrieve Rooms API should contain a clear and concise _RoomDescription_ (and _RatePlanDescription_ when using both room and rate codes) to ensure Channel Manager hoteliers can quickly and easily map/link their Channel Manager room rates to your booking channel.

### **Inventory Push API**

1. ChannelConnect uses _**OTA\_HotelAvailNotifRQ**_ to PUSH availability and restrictions and _**OTA\_HotelRateAmountNotifRQ**_ to PUSH rates.
2. The partner should always response with either a “_success_” or “_error_” response. Under **no** circumstances should a request be ignored and a response not sent.
3. For performance reasons, ChannelConnect expects **all** messages to receive a response from the partner within five (5) seconds. If a response is **not** received within a twenty (20) second timeframe, the request will timeout and the message will be re-queued to be sent again on the next update cycle. If any background processing will push response times out beyond five (5) seconds, we highly recommend you respond with a '_Success_' message and continue the background processing without delaying your response.
4. The maximum update period for ChannelConnect can update is one-thousand and ninety-five (1095) days. The default update period is three-hundred and sixty-five (365) days. The minimum update period is fourteen (14) days. We always recommend a buffer be in place on the partner side, especially if you are a last minute booking site. Ie: if you only sell the next fourteen (14) days, the hotelier should be able to upload information a minimum of twenty-one (21) to thirty (30) days.
5. It is important to remember the potential for large amounts of data to be pushed out from ChannelConnect. If a hotel enables their connection, you can potentially receive one-thousand and ninety-five (1095) days worth of Inventory, Rates and Restrictions all within a short space of time. If you have several properties go live at the same time or push large updates, the data load can be quite large. **We urge that you complete stringent performance testing on your production servers/endpoint(s) to ensure they will scale with the number of hotels you'll have connected in production.**
6. Stop Sells are a mandatory functionality. If your system does not have the concept of stop sells, the _RestrictionStatus_ ‘Close’ should be seen as zero (0) availability.

### **Reservation API**

1. ChannelConnect follows the OTA reservation specification and allows a lot of information to be sent through regarding reservations. Not all of that information is mandatory for ChannelConnect to be able to process the reservation. Please refer to the Reservation API documentation for more information.
2. The state of the reservation is determined by the _**OTA\_HotelResNotifRQ**_ _ResStatus_ attribute for which values _Commit_, _Modify_ and _Cancel_ are allowed.
3. ChannelConnect only allows one (1) hotel code per reservation. If a partner allows multiple hotels per reservation, one (1) reservation per hotel must be sent.
4. ChannelConnect only allows one (1) reservation per request sent.
5. ChannelConnect allows multiple rooms and rate plans in a single reservation request, as long as they are part of the same reservation.
6. If you choose to send through Payment Information, it will be passed onto any Hotels PMS system should one support this functionality.

#### **Modifications**

1. Modifications will be identified by the ‘_Modify_’ _ResStatus_.
2. The modification must contain the full reservation data, as it stands at the modification has been made.
3. The _LastModifyDateTime_ should reflect the time the reservation was modified within the partner system

#### **Cancellations**

1. Cancellations will be identified by the ‘_Cancel_’ _ResStatus_.
2. The cancellation must contain the full reservation data, as it stands at the time of the cancellation.
3. The _LastModifyDateTime_ should reflect the time the reservation was cancelled within the partner system
4. Availability will not automatically be made available within The Channel Manager when a cancellation message is received.

## Certification

ChannelConnect certification will be undertaken once development of all functionality has been completed. It is important to note that testing (including negative testing) of all developed ChannelConnect API functionality should be completed prior to certification. The certification process is conducted by the partner, using a certification document that The Channel Manager will provide. The certification process must be completed using information presented on the partner system, not the information presented within the partners Channel Manager test account. There is no restriction to the amount of times a partner can attempt certification.

Once certification is completed, the results will be reviewed by The Channel Manager’s API Development team. The Channel Manager and the API Development team reserve the right to delay deployment to The Channel Manager’s production environments until they are satisfied with the results.

## Test Environment Access

A Channel Manager test account will be provided for use during development. Test account access is only guaranteed during active development and should not be used for ongoing testing or for demonstration purposes. Upon completion of ChannelConnect certification, the test account will be disabled.
