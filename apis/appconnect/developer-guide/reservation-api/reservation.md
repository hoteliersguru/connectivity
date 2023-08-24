# Reservation

### OTA\_ReadRQ



| Element / @Attribute                                         | Occurrences | Description                                                    |
| ------------------------------------------------------------ | ----------- | -------------------------------------------------------------- |
| OTA\_ReadRQ                                                  |             | Root element of the message.                                   |
| OTA\_ReadRQ/@EchoToken                                       | 1           | Unique identifier for request, is returned in the response.    |
| OTA\_ReadRQ/@Version                                         | 1           | Current version 1                                              |
| OTA\_ReadRQ/@TimeStamp                                       | 1           | Time of transaction, ISO 8601 date (2019-04-10T13:08:21+07:00) |
| OTA\_ReadRQ/HotelReadRequest                                 | 1           |                                                                |
| OTA\_ReadRQ/HotelReadRequest/@HotelCode                      | 1           |                                                                |
| OTA\_ReadRQ/HotelReadRequest/SelectionCriteria               | 1           |                                                                |
| OTA\_ReadRQ/HotelReadRequest/SelectionCriteria/SelectionType | 1           | Currently only "Undelivered" is supported.                     |

### OTA\_ResRetrieveRS

| Element / @Attribute                | Occurrences | Description                                                    |
| ----------------------------------- | ----------- | -------------------------------------------------------------- |
| OTA\_ResRetrieveRS                  |             | Root element of the message.                                   |
| OTA\_ResRetrieveRS/@EchoToken       | 1           | Unique identifier for request, is returned in the response.    |
| OTA\_ResRetrieveRS/@Version         | 1           | Current version 1                                              |
| OTA\_ResRetrieveRS/@TimeStamp       | 1           | Time of transaction, ISO 8601 date (2019-04-10T13:08:21+07:00) |
| OTA\_ResRetrieveRS/ReservationsList | 1           | See [ReservationsList](reservation.md#reservationslist).       |

### ReservationsList



| Element / @Attribute                                  | Occurrences | Description                                                                                                                           |
| ----------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| ReservationsList                                      |             |                                                                                                                                       |
| ReservationsList/HotelReservation                     | 1..n        |                                                                                                                                       |
| ReservationsList/HotelReservation/@CreateDateTime     | 1           | The date the booking was created.                                                                                                     |
| ReservationsList/HotelReservation/@LastModifyDateTime | 0..1        | For cancellations the date the booking was cancelled.                                                                                 |
| ReservationsList/HotelReservation/@ResStatus          | 1           | The type of operations reported. Valid values: Commit – for new bookings Cancel – for cancelled bookings, Modify – for modifications. |
| ReservationsList/HotelReservation/UniqueID            | 1           |                                                                                                                                       |
| ReservationsList/HotelReservation/UniqueID/@Type      | 1           | Type of reservation. Always 14 Reservation.                                                                                           |
| ReservationsList/HotelReservation/UniqueID/@ID        | 1           | The reservation identifier.                                                                                                           |
| ReservationsList/HotelReservation/RoomStays           | 1           | See [RoomStays](reservation.md#roomstays).                                                                                            |
| ReservationsList/HotelReservation/ResGlobalInfo       | 1           | See [ResGlobalInfo](reservation.md#total).                                                                                            |
|                                                       |             |                                                                                                                                       |

### RoomStays



| Element / @Attribute                                                 | Occurrences | Description                                                                                                                                                                                            |
| -------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| RoomStays                                                            |             | Root element for room stays. One for each room in the reservation.                                                                                                                                     |
| RoomStays/RoomStay                                                   | 1..n        |                                                                                                                                                                                                        |
| RoomStays/RoomStay/RoomRates                                         | 1           | See [RoomRates](reservation.md#roomrates).                                                                                                                                                             |
| RoomStays/RoomStay/TimeSpan                                          | 1           | The time duration this room is booked.                                                                                                                                                                 |
| RoomStays/RoomStay/TimeSpan/@Start, RoomStays/RoomStay/TimeSpan/@End | 1           | The start and end dates for which the availability update is being sent in ISO 8601 format (without time). Start date is the check-in date for the reservation and the End date is the check-out date. |
| RoomStays/RoomStay/Total                                             | 1           | The total amount changed for this room.                                                                                                                                                                |
| RoomStays/RoomStay/Total/@CurrencyCode                               | 1           | The currency code for the amount.                                                                                                                                                                      |
| RoomStays/RoomStay/Total/@AmountAfterTax                             | 1           | The amount charged for this room. This is the amount displayed to the guest at the time of booking and may not include all taxes.                                                                      |
| RoomStays/RoomStay/BasicPropertyInfo                                 | 1           | The hotel information.                                                                                                                                                                                 |
| RoomStays/RoomStay/BasicPropertyInfo/@HotelCode                      | 1           | The hotel code.                                                                                                                                                                                        |

### RoomRates



| Element / @Attribute | Occurrences | Description                                                                                      |
| -------------------- | ----------- | ------------------------------------------------------------------------------------------------ |
| RoomRates            |             |                                                                                                  |
| RoomRates/RoomRate   | 1           | The rate plan used and the type of room booked.                                                  |
| @RoomTypeCode        | 1           | The code identifying the room. This is the same as the @InvTypeCode attribute in other messages. |
| @NumberOfUnits       | 1           | Set to “1” each room has a RoomStay element.                                                     |
| @RatePlanCode        | 0..1        | The code for the rate plan.                                                                      |
| Rates                | 0..1        | See [Rates](reservation.md#rates).                                                               |

### Rates



| Element / @Attribute | Occurrences | Description                                                                                                                                                                                                                                                                                                                        |
| -------------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Rates                |             |                                                                                                                                                                                                                                                                                                                                    |
| Rates/Rate           | 0..n        |                                                                                                                                                                                                                                                                                                                                    |
| @EffectiveDate       | 1           | The start date the rate applies in ISO 8601 date format without time.                                                                                                                                                                                                                                                              |
| @ExpireDate          | 1           | The end date (not including) of the rate in ISO 8601 date format without time. Example, if rate is on 2018-12-16: 200, 2018-12-17: 200, 2018-12-18: 400. @EffectiveDate would be 2018-12-16 and @ExpireDate would be 2018-12-18 with the rate of 200. The next period would be, @EffectiveDate 2018-12-18, @ExpireDate 2018-12-19. |
| @UnitMultiplier      | 1           | “1” is the only acceptable value.                                                                                                                                                                                                                                                                                                  |
| Base                 | 1           | Base amount charged                                                                                                                                                                                                                                                                                                                |
| @CurrencyCode        | 1           | Currency Code                                                                                                                                                                                                                                                                                                                      |
| @AmountAfterTax      | 1           | Amount After Tax                                                                                                                                                                                                                                                                                                                   |

### ResGlobalInfo



| Element / @Attribute                | Occurrences | Description      |
| ----------------------------------- | ----------- | ---------------- |
| ResGlobalInfo                       |             | Res Global Info  |
| ResGlobalInfo/Total                 | 1           | Total            |
| ResGlobalInfo/Total/@CurrencyCode   | 1           | Currency Code    |
| ResGlobalInfo/Total/@AmountAfterTax | 1           | Amount After Tax |
