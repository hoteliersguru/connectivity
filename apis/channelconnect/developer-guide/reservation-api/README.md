# Reservation API

### Content

* [Reservation](reservation.md)
* [Reservation XML Sample](reservation-xml-sample.md)
* [Modification XML Sample](modification-xml-sample.md)
* [Cancellation XML Sample](cancellation-xml-sample.md)
* [Daily Rates XML Samples](daily-rates-xml-samples.md)
* [Payment XML Samples](payment-xml-samples.md)
* [Services XML Samples](services-xml-sample.md)

ChannelConnect uses the **OTA\_HotelResNotifRQ** to receive reservations, modifications and cancellations. The state of the reservation is determined by the OTA\_HotelResNotifRQ **ResStatus** attribute for which values **Commit**, **Modify** and **Cancel** are allowed. ChannelConnect only allows one hotel code per reservation. If a channel allow multiple hotels per reservation one reservation per hotel must be sent. Multiple rooms and rates are allowed in one reservation request.

### EchoToken Implementation for  OTA\_HotelResNotifRQ

EchoTokens are essential for all requests \(namely OTA\_HotelResNotifRQ\) being made over the ChannelConnect. EchoTokens ensure that each request can be uniquely identified for troubleshooting purposes in both testing and production environments.

All requests you receive from ChannelConnect will contain an EchoToken, and your response must include the same EchoToken as received in the request.

**NOTE:** Please ensure that you implement EchoTokens that are as 'unique' as possible to ensure that log trawling for troubleshooting purposes on either side is quick and efficient. Implementing GUIDs are recommended and more information about GUID can be found - [http://en.wikipedia.org/wiki/Globally\_unique\_identifier](http://en.wikipedia.org/wiki/Globally_unique_identifier).

### Required Information <a id="ReservationAPI-RequiredInformation"></a>

ChannelConnect follows the OTA reservation specification and allows a lot of information to be send through regarding reservations. Not all of that information is mandatory for ChannelConnect to be able to process the reservation. Please refer to the Reservation Specification to see what information is mandatory.

### Reservation confirmation <a id="ReservationAPI-Reservationconfirmation"></a>

It's important to note that ChannelConnect **does not** act as an authority on allowing or denying a reservation to take place. The OTA\_HotelResNotifRS ChannelConnect responds with \('Success' or 'Error'\) will simply indicate whether ChannelConnect is able to receive the reservation delivery message/notification request or not.

With the above in mind, the OTA\_HotelResNotifRQ ↔ OTA\_HotelResNotifRS pair carrying the reservation message/notification to ChannelConnect **should not** be linked to your front end customer booking process. The customer/agent making a reservation on your booking channel should be able to make a reservation irrespective of the response \(or lack thereof\) being received back from ChannelConnect.

### Error Handling <a id="ReservationAPI-ErrorHandling"></a>

If the response is type OTA\_HotelResNotifRS with an Error message then the reservation can not be processed because some data is invalid. This could be for example if required data is missing or if the credentials or hotel code is incorrect and the reservation will not process until the error is fixed. If the error is that required element or attributes are missing the implementation will need to be adjusted to send the required data. If the error is to do with credentials, check that the correct username/password is sent. If the error is an invalid hotel code, contact the hotel to make sure they are setup in the Channel Manager to receive reservations.

If the response is a http error response code in the 500 range then it is expected that the connecting channel will retry the sending of the reservation until it is successfully delivered or a pre-defined timeout period is reached example 60 minutes. In the case that a reservation cannot be delivered within the timeout period a problem case should be raised with The Channel Managers's Application Support team. For the live production ChannelConnect service you will be informed when there are scheduled outages.

