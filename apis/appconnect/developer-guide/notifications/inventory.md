# Inventory

### OTA\_HotelAvailNotifRQ

An OTA\_HotelAvailNotifRQ message will be pushed from the channel mananger's web service after the value changes to The Partner's extranet. The message can be used to update the availability for one room type for a single hotel. Specifically:

* Room availability

Each OTA\_HotelAvailNotifRQ message contains a single **AvailStatusMessages** element which indicates the hotel to update using the AvailStatusMessages/@HotelCode attribute. The AvailStatusMessages/AvailStatusMessage elements will contain the updates to process over a date range. There can be several AvailStatusMessage updates per request, however each request will be limited to one hotel and one room.

#### The Request

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelAvailNotifRQ
    xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0"
    TimeStamp="2024-05-30T14:22:30+07:00"
    EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="000001">
        <AvailStatusMessage BookingLimit="10">
            <StatusApplicationControl Start="2022-04-08" End="2022-12-31" InvTypeCode="PdncX" />
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

#### Elements & Attributes <a href="#elements--attributesx20" id="elements--attributesx20"></a>

| Element / @Attribute                                                                                         | Occurrences | Description                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------ | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OTA\_HotelAvailNotifRQ                                                                                       | 1           |                                                                                                                                                                   |
| OTA\_HotelAvailNotifRQ / @xmlns                                                                              | 1           | http://www.opentravel.org/OTA/2003/05                                                                                                                             |
| OTA\_HotelAvailNotifRQ / @EchoToken                                                                          | 1           | Uuid v4 format                                                                                                                                                    |
| OTA\_HotelAvailNotifRQ / @Version                                                                            | 1           | 1.0                                                                                                                                                               |
| OTA\_HotelAvailNotifRQ / @TimeStamp                                                                          | 1           | ISO 8601 date, Example : 2024-05-30T14:22:30+07:00                                                                                                                |
| OTA\_HotelAvailNotifRQ / AvailStatusMessages                                                                 | 0..1        | Contains the availability messages.                                                                                                                               |
| OTA\_HotelAvailNotifRQ / AvailStatusMessages / @HotelCode                                                    | 1           | This is the code of the property whose availability is being updated.                                                                                             |
| OTA\_HotelAvailNotifRQ / AvailStatusMessages / AvailStatusMessage                                            | 1..n        |                                                                                                                                                                   |
| OTA\_HotelAvailNotifRQ / AvailStatusMessages / AvailStatusMessage / @BookingLimit                            | 1           | Sets the number of rooms available for sale per day. Room availability is always set at the room level.                                                           |
| OTA\_HotelAvailNotifRQ / AvailStatusMessages / AvailStatusMessage / StatusApplicationControl                 | 1           | Contains date and room identification information.                                                                                                                |
| OTA\_HotelAvailNotifRQ / AvailStatusMessages / AvailStatusMessage / StatusApplicationControl / @Start , @End | 1           | The start and end dates for which the availability update is being sent in ISO 8601 format (without time). These dates are inclusive and use the hotel time-zone. |
| OTA\_HotelAvailNotifRQ / AvailStatusMessages / AvailStatusMessage / StatusApplicationControl / @InvTypeCode  | 1           | Identifies the room.                                                                                                                                              |

#### Successful Response <a href="#successful-response" id="successful-response"></a>

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelAvailNotifRS
    xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0"
    TimeStamp="2024-05-30T15:18:49+07:00"
    EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <Success />
</OTA_HotelAvailNotifRS>
```

#### Failure Response <a href="#failure-response" id="failure-response"></a>

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelAvailNotifRS
    xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0"
    TimeStamp="2024-05-30T14:34:25+07:00"
    EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <Errors>
        <Error Type="6" Code="392">Hotel Identifier 000001 Not Found.</Error>
    </Errors>
</OTA_HotelAvailNotifRS>
```

#### Elements & Attributes <a href="#elements--attributes" id="elements--attributes"></a>

| Element / @Attribute                      | Occurrences | Description                                        |
| ----------------------------------------- | ----------- | -------------------------------------------------- |
| OTA\_HotelAvailNotifRS                    | 1           |                                                    |
| OTA\_HotelAvailNotifRS/@xmlns             | 1           | http://www.opentravel.org/OTA/2003/05              |
| OTA\_HotelAvailNotifRS/@Version           | 1           | 1.0                                                |
| OTA\_HotelAvailNotifRS/@TimeStamp         | 1           | ISO 8601 date, Example : 2024-05-30T14:22:30+07:00 |
| OTA\_HotelAvailNotifRS/@EchoToken         | 1           | Repeat the EchoToken from the Request.             |
| OTA\_HotelAvailNotifRS/Success            | 0..1        |                                                    |
| OTA\_HotelAvailNotifRS/Errors             | 0..1        |                                                    |
| OTA\_HotelAvailNotifRS/Errors/Error       | 1           | Short Description of the Error                     |
| OTA\_HotelAvailNotifRS/Errors/Error/@Type | 1           | Type                                               |
| OTA\_HotelAvailNotifRS/Errors/Error/@Code | 1           | Code                                               |
