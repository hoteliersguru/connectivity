# Reservation

### OTA\_HotelResNotifRQ

An OTA\_HotelResNotifRQ message will be pushed from the channel mananger's web service after a reservation is made / modified or cancelled, to The Partner's extranet. The message can be used to keep track of reservations made to the hotel.

Each OTA\_HotelResNotifRQ message contains a single HotelReservations/HotelReservation element, each request will be limited to one hotel and one reservation.

#### The Request

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelResNotifRQ 
    xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" 
    TimeStamp="2024-05-30T16:22:10+07:00" 
    EchoToken="27450e78-d067-4cda-da5a-5872adc68fb9">
    <HotelReservations>
        <HotelReservation CreateDateTime="2024-05-29T21:26:31+07:00" ResStatus="Commit">
            <UniqueID Type="14" ID="841130"/>
            <RoomStays>
                <RoomStay>
                    <RoomRates>
                        <RoomRate NumberOfUnits="1" RoomTypeCode="1234" RatePlanCode="5678">
                            <Rates>
                                <Rate EffectiveDate="2024-07-01" ExpireDate="2024-07-01" 
                                    UnitMultiplier="1">
                                    <Base CurrencyCode="THB" AmountAfterTax="4815.0000"/>
                                </Rate>
                                <Rate EffectiveDate="2024-07-02" ExpireDate="2024-07-02" 
                                    UnitMultiplier="1">
                                    <Base CurrencyCode="THB" AmountAfterTax="4815.0000"/>
                                </Rate>
                            </Rates>
                        </RoomRate>
                    </RoomRates>
                    <TimeSpan Start="2024-07-01" End="2024-07-03"/>
                    <Total CurrencyCode="THB" AmountAfterTax="9330.0000"/>
                    <BasicPropertyInfo HotelCode="002509"/>
                </RoomStay>
            </RoomStays>
            <ResGlobalInfo>
                <Total CurrencyCode="THB" AmountAfterTax="8703.5600"/>
            </ResGlobalInfo>
        </HotelReservation>
    </HotelReservations>
</OTA_HotelResNotifRQ>
```

#### Elements & Attributes

| Element / @Attribute                   | Occurrences | Description                                                    |
| -------------------------------------- | ----------- | -------------------------------------------------------------- |
| OTA\_HotelResNotifRQ                   | 1           | Root element of the message.                                   |
| OTA\_HotelResNotifRQ/@xmlns            | 1           | http://www.opentravel.org/OTA/2003/05                          |
| OTA\_HotelResNotifRQ/@Version          | 1           | Current version 1.0                                            |
| OTA\_HotelResNotifRQ/@TimeStamp        | 1           | Time of transaction, ISO 8601 date (2019-04-10T13:08:21+07:00) |
| OTA\_HotelResNotifRQ/@EchoToken        | 1           | Unique identifier for request, is returned in the response.    |
| OTA\_HotelResNotifRQ/HotelReservations | 1           |                                                                |

#### HotelReservations

| Element / @Attribute                                                   | Occurrences | Description                                                                                                                           |
| ---------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| HotelReservations                                                      |             |                                                                                                                                       |
| HotelReservations/HotelReservation                                     | 1..n        |                                                                                                                                       |
| HotelReservations/HotelReservation/@CreateDateTime                     | 1           | The date the booking was created.                                                                                                     |
| HotelReservations/HotelReservation/@LastModifyDateTime                 | 0..1        | For cancellations the date the booking was cancelled.                                                                                 |
| HotelReservations/HotelReservation/@ResStatus                          | 1           | The type of operations reported. Valid values: Commit – for new bookings Cancel – for cancelled bookings, Modify – for modifications. |
| HotelReservations/HotelReservation/UniqueID                            | 1           |                                                                                                                                       |
| HotelReservations/HotelReservation/UniqueID/@Type                      | 1           | Type of reservation. Always 14 Reservation.                                                                                           |
| HotelReservations/HotelReservation/UniqueID/@ID                        | 1           | The reservation identifier.                                                                                                           |
| HotelReservations/HotelReservation/RoomStays                           | 1           |                                                                                                                                       |
| HotelReservations/HotelReservation/ResGlobalInfo                       | 1           | Res Global Info                                                                                                                       |
| HotelReservations/HotelReservation/ResGlobalInfo/Total                 | 1           | Total                                                                                                                                 |
| HotelReservations/HotelReservation/ResGlobalInfo/Total/@CurrencyCode   | 1           | Currency Code                                                                                                                         |
| HotelReservations/HotelReservation/ResGlobalInfo/Total/@AmountAfterTax | 1           | Amount After Tax                                                                                                                      |

#### RoomStays

| Element / @Attribute                                                 | Occurrences | Description                                                                                                                                                                                            |
| -------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| RoomStays                                                            |             | Root element for room stays. One for each room in the reservation.                                                                                                                                     |
| RoomStays/RoomStay                                                   | 1..n        |                                                                                                                                                                                                        |
| RoomStays/RoomStay/RoomRates                                         | 1           |                                                                                                                                                                                                        |
| RoomStays/RoomStay/TimeSpan                                          | 1           | The time duration this room is booked.                                                                                                                                                                 |
| RoomStays/RoomStay/TimeSpan/@Start, RoomStays/RoomStay/TimeSpan/@End | 1           | The start and end dates for which the availability update is being sent in ISO 8601 format (without time). Start date is the check-in date for the reservation and the End date is the check-out date. |
| RoomStays/RoomStay/Total                                             | 1           | The total amount changed for this room.                                                                                                                                                                |
| RoomStays/RoomStay/Total/@CurrencyCode                               | 1           | The currency code for the amount.                                                                                                                                                                      |
| RoomStays/RoomStay/Total/@AmountAfterTax                             | 1           | The amount charged for this room. This is the amount displayed to the guest at the time of booking and may not include all taxes.                                                                      |
| RoomStays/RoomStay/BasicPropertyInfo                                 | 1           | The hotel information.                                                                                                                                                                                 |
| RoomStays/RoomStay/BasicPropertyInfo/@HotelCode                      | 1           | The hotel code.                                                                                                                                                                                        |

#### RoomRates

| Element / @Attribute              | Occurrences | Description                                                                                      |
| --------------------------------- | ----------- | ------------------------------------------------------------------------------------------------ |
| RoomRates                         |             |                                                                                                  |
| RoomRates/RoomRate                |             | The rate plan used and the type of room booked.                                                  |
| RoomRates/RoomRate/@NumberOfUnits | 1           | Set to “1” each room has a RoomStay element.                                                     |
| RoomRates/RoomRate/@RoomTypeCode  | 1           | The code identifying the room. This is the same as the @InvTypeCode attribute in other messages. |
| RoomRates/RoomRate/@RatePlanCode  | 0..1        | The code for the rate plan.                                                                      |
| RoomRates/RoomRate/Rates          |             |                                                                                                  |

#### Rates

| Element / @Attribute            | Occurrences | Description                                                                                                                                                                                                                                                                                                                        |
| ------------------------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Rates                           |             |                                                                                                                                                                                                                                                                                                                                    |
| Rates/Rate                      | 0..n        |                                                                                                                                                                                                                                                                                                                                    |
| Rates/Rate/@EffectiveDate       | 1           | The start date the rate applies in ISO 8601 date format without time.                                                                                                                                                                                                                                                              |
| Rates/Rate/@ExpireDate          | 1           | The end date (not including) of the rate in ISO 8601 date format without time. Example, if rate is on 2018-12-16: 200, 2018-12-17: 200, 2018-12-18: 400. @EffectiveDate would be 2018-12-16 and @ExpireDate would be 2018-12-18 with the rate of 200. The next period would be, @EffectiveDate 2018-12-18, @ExpireDate 2018-12-19. |
| Rates/Rate/UnitMultiplier       | 1           | “1” is the only acceptable value.                                                                                                                                                                                                                                                                                                  |
| Rates/Rate/Base                 | 1           | Base amount charged                                                                                                                                                                                                                                                                                                                |
| Rates/Rate/Base/@CurrencyCode   | 1           | Currency Code                                                                                                                                                                                                                                                                                                                      |
| Rates/Rate/Base/@AmountAfterTax | 1           | Amount After Tax                                                                                                                                                                                                                                                                                                                   |

#### Successful Response

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelResNotifRS 
    xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" 
    TimeStamp="2024-05-30T16:22:10+07:00" 
    EchoToken="27450e78-d067-4cda-da5a-5872adc68fb9">
    <Success/>
    <HotelReservations>
        <HotelReservation>
            <UniqueID Type="14" ID="841130"/>
            <ResGlobalInfo>
                <HotelReservationIDs>
                    <HotelReservationID ResID_Type="14" ResID_Value="841130"/>
                </HotelReservationIDs>
            </ResGlobalInfo>
        </HotelReservation>
    </HotelReservations>
</OTA_HotelResNotifRS>
```

#### Failure Response

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelResNotifRS
    xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0"
    TimeStamp="2022-04-08T14:34:25+07:00"
    EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <Errors>
        <Error Type="6" Code="392">Hotel Identifier ABC Not Found.</Error>
    </Errors>
</OTA_HotelResNotifRS>
```

#### Elements & Attributes

| Element / @Attribute                                                                                                                   | Occurrences | Description                                        |
| -------------------------------------------------------------------------------------------------------------------------------------- | ----------- | -------------------------------------------------- |
| OTA\_HotelResNotifRS                                                                                                                   |             |                                                    |
| OTA\_HotelResNotifRS / @xmlns                                                                                                          | 1           | http://www.opentravel.org/OTA/2003/05              |
| OTA\_HotelResNotifRS / @Version                                                                                                        | 1           | 1.0                                                |
| OTA\_HotelResNotifRS / @TimeStamp                                                                                                      | 1           | ISO 8601 date, Example : 2024-05-30T14:22:30+07:00 |
| OTA\_HotelResNotifRS / @EchoToken                                                                                                      | 1           | Repeat the EchoToken from the Request.             |
| OTA\_HotelResNotifRS / Success                                                                                                         | 0..1        |                                                    |
| OTA\_HotelResNotifRS / Errors                                                                                                          | 0..1        |                                                    |
| OTA\_HotelResNotifRS / Errors / Error                                                                                                  | 1           | Short Description of the Error                     |
| OTA\_HotelResNotifRS / Errors / Error / @Type                                                                                          | 1           | Type                                               |
| OTA\_HotelResNotifRS / Errors / Error / @Code                                                                                          | 1           | Code                                               |
| OTA\_HotelResNotifRS / HotelReservations                                                                                               | 0..1        |                                                    |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation                                                                            | 1           |                                                    |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation / UniqueID                                                                 | 1           |                                                    |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation / UniqueID / @Type                                                         | 1           | Type of reservation. Always 14 Reservation.        |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation / UniqueID / @ID                                                           | 1           | The reservation identifier.                        |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation / ResGlobalInfo                                                            | 1           |                                                    |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation / ResGlobalInfo / HotelReservationIDs                                      | 0..1        |                                                    |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation / ResGlobalInfo / HotelReservationIDs / HotelReservationID                 | 1           |                                                    |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation / ResGlobalInfo / HotelReservationIDs / HotelReservationID / @ResID\_Type  | 1           | Type of reservation. Always 14 Reservation.        |
| OTA\_HotelResNotifRS / HotelReservations / HotelReservation / ResGlobalInfo / HotelReservationIDs / HotelReservationID / @ResID\_Value | 1           | The reservation identifier.                        |
