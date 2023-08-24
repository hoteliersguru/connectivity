# Reservation

## OTA\_HotelResNotifRQ <a href="#reservation-ota_hotelresnotifrq" id="reservation-ota_hotelresnotifrq"></a>

The connected channel will send through reservations to ChannelConnect using the OTA\_HotelResNotifRQ message. ChannelConnect will process the reservation and respond with the OTA\_HotelResNotifRS as a receipt of success or failure to process the request. The Channel Manager only allows one hotel code per reservation. If a channel allows multiple hotels per reservation one reservation per hotel must be sent.

## XML Samples

[Reservation XML Sample](reservation-xml-sample.md) / [Modification XML Sample](modification-xml-sample.md) / [Cancellation XML Sample](cancellation-xml-sample.md)

## OTA\_HotelResNotifRQ Specification

{% hint style="info" %}
Note, column **count** indicates min/max required values, 1 = required, 0 = not required.
{% endhint %}

| Element                  | Count | Description / Format                                                                                                                                                                                                                                                           |
| ------------------------ | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **OTA\_HotelResNotifRQ** |       | Root element of the message.                                                                                                                                                                                                                                                   |
| @EchoToken               | 1     | Unique identifier for request, is returned in the response.                                                                                                                                                                                                                    |
| @Version                 | 1     | Current version 1                                                                                                                                                                                                                                                              |
| @TimeStamp               | 1     | Time of transaction, ISO 8601 date (2019-04-10T13:08:21+07:00)                                                                                                                                                                                                                 |
| @ResStatus               | 0..1  | <p>The type of operations reported. Valid values: Commit – for new bookings Cancel – for cancelled bookings, Modify – for modifications.</p><p>This attribute is optional, but if not set here, it must be set for each Reservation in HotelReservations/HotelReservation.</p> |
| POS                      | 0..1  | See [POS](reservation.md#pos).                                                                                                                                                                                                                                                 |
| HotelReservations        | 1     | See [HotelReservations](reservation.md#hotelreservations).                                                                                                                                                                                                                     |

### POS

| Element                                   |      | Description / Format                                                                                                                                                                                           |
| ----------------------------------------- | ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **POS**                                   |      | The point-of-sale data, contained in the element, communicates the information that allows the receiving system to identify the trading partner that is sending the request or the response message.           |
| **POS/Source**                            | 1    |                                                                                                                                                                                                                |
| **POS/Source/RequestorID**                | 1    | An identifier of the entity making the request (e.g. ATA/IATA/ID number, Electronic Reservation Service Provider (ERSP), Association of British Travel Agents (ABTA)).                                         |
| @Type                                     | 1    | Set to 22                                                                                                                                                                                                      |
| @ID                                       | 1    | Id that identifies the booking channel.                                                                                                                                                                        |
| **POS/Source/BookingChannel**             | 1..2 | Specifies the booking channel type and whether it is the primary means of connectivity of the source. \| Specifies the booking channel type and whether it is the primary means of connectivity of the source. |
| @Primary                                  | 1    | Set to true for the primary booking channel.                                                                                                                                                                   |
| **POS/Source/BookingChannel/CompanyName** | 1    | Identifies the company that is associated with the booking channel.                                                                                                                                            |
| @Code                                     | 0..1 | Code that identifies the booking channel.                                                                                                                                                                      |

### HotelReservations

| Element                                              |      | Description / Format                                                                                                                                                                                                                                                                                                                |
| ---------------------------------------------------- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **HotelReservations**                                |      |                                                                                                                                                                                                                                                                                                                                     |
| **HotelReservations/HotelReservation**               | 1..n |                                                                                                                                                                                                                                                                                                                                     |
| @CreateDateTime                                      | 1    | The date the booking was created.                                                                                                                                                                                                                                                                                                   |
| @LastModifyDateTime                                  | 0..1 | For cancellations the date the booking was cancelled.                                                                                                                                                                                                                                                                               |
| @ResStatus                                           | 0..1 | <p>The type of operations reported. Valid values: Commit – for new bookings Cancel – for cancelled bookings, Modify – for modifications.</p><p>This attribute is optional, but if not set here, it must be set as an attribute for OTA_HotelResNotifRQ. If set here, it will be used over the attribute in OTA_HotelResNotifRQ.</p> |
| **HotelReservations/HotelReservation/UniqueID**      | 1    |                                                                                                                                                                                                                                                                                                                                     |
| @Type                                                | 1    | Type of reservation. Always 14 Reservation.                                                                                                                                                                                                                                                                                         |
| @ID                                                  | 1    | The reservation identifier.                                                                                                                                                                                                                                                                                                         |
| **HotelReservations/HotelReservation/RoomStays**     | 1    | See [RoomStays](reservation.md#roomstays).                                                                                                                                                                                                                                                                                          |
| **HotelReservations/HotelReservation/Services**      | 0..1 | See [Services](reservation.md#services).                                                                                                                                                                                                                                                                                            |
| **HotelReservations/HotelReservation/ResGuests**     | 1    | See [ResGuests](reservation.md#resguests).                                                                                                                                                                                                                                                                                          |
| **HotelReservations/HotelReservation/ResGlobalInfo** | 1    | See [ResGlobalInfo](reservation.md#resglobalinfo).                                                                                                                                                                                                                                                                                  |

### RoomStays

| Element                                               |      | Description / Format                                                                                                                                                                                   |
| ----------------------------------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **RoomStays**                                         |      | Root element for room stays. One for each room in the reservation.                                                                                                                                     |
| **RoomStays/RoomStay**                                | 1..n |                                                                                                                                                                                                        |
| @PromotionCode                                        | 0..1 |                                                                                                                                                                                                        |
| **RoomStays/RoomStay/RoomeTypes**                     | 0..1 | See [RoomTypes](reservation.md#roomtypes).                                                                                                                                                             |
| **RoomStays/RoomStay/RatePlans**                      | 0..1 | See [RatePlans](reservation.md#rateplans).                                                                                                                                                             |
| **RoomStays/RoomStay/RoomRates**                      | 1    | See [RoomRates](reservation.md#roomrates).                                                                                                                                                             |
| **RoomStays/RoomStay/GuestCounts**                    | 1    | See [GuestCounts](reservation.md#guestcounts).                                                                                                                                                         |
| **RoomStays/RoomStay/TimeSpan**                       | 1    | The time duration this room is booked.                                                                                                                                                                 |
| @Start, @End                                          | 1    | The start and end dates for which the availability update is being sent in ISO 8601 format (without time). Start date is the check-in date for the reservation and the End date is the check-out date. |
| **RoomStays/RoomStay/Total**                          | 1    | See [Total](reservation.md#total).                                                                                                                                                                     |
| **RoomStays/RoomStay/BasicProprtyInfo**               | 1    | The hotel information.                                                                                                                                                                                 |
| @HotelCode                                            | 1    | The hotel code.                                                                                                                                                                                        |
| @HotelName                                            | 0..1 | The hotel name.                                                                                                                                                                                        |
| **RoomStays/RoomStay/ServiceRPHs**                    | 0..1 |                                                                                                                                                                                                        |
| **RoomStays/RoomStay/ServiceRPHs/ServiceRPH**         | 1..n | \*\*A service can be linked to the RoomStay using the below element/attribute                                                                                                                          |
| @RPH                                                  | 1    | \*\*This links a Service to the Service information provided at the HotelReservation level (if applicable)                                                                                             |
| **RoomStays/RoomStay/ResGuestRPHs**                   | 0..1 |                                                                                                                                                                                                        |
| **RoomStays/RoomStay/ResGuestRPHs/ResGuestRPH**       | 1..n | \*\*Used to link guests from the ResGuests list to the RoomStay. Should not be used if not all guests can be linked to RoomStays or not all RoomStays can be linked to guests.                         |
| @RPH                                                  | 1    | When set, ResGuests.ResGuest must have the attribute ResGuestRPH matching the RPH set here.                                                                                                            |
| **RoomStays/RoomStay/Comments**                       | 0..1 |                                                                                                                                                                                                        |
| **RoomStays/RoomStay/Comments/Comment**               | 1..n | \*\*Per RoomStay, there may be one comment                                                                                                                                                             |
| Text                                                  | 1    | \*\*The comment ([PCI sensitive data](https://www.pcisecuritystandards.org/pdfs/pci\_fs\_data\_storage.pdf) is prohibited)                                                                             |
| **RoomStays/RoomStay/SpecialRequests**                | 0..1 |                                                                                                                                                                                                        |
| **RoomStays/RoomStay/SpecialRequests/SpecialRequest** | 1..n |                                                                                                                                                                                                        |
| @Name                                                 | 1    | <p>**Special request type i.e:</p><p>bedding configuration</p><p>smoking</p><p>cot</p><p>extra bed</p>                                                                                                 |
| Text                                                  | 0..1 | \*\*Special request text                                                                                                                                                                               |

### RoomTypes

| Element                                |      | Description / Format            |
| -------------------------------------- | ---- | ------------------------------- |
| **RoomTypes**                          |      |                                 |
| **RoomTypes/RoomType**                 | 1..n |                                 |
| @RoomTypeCode                          | 1    | \*\*The code of the room booked |
| **RoomTypes/RoomType/RoomDescription** | 1    | \*\*Description of the room     |
| @Name                                  | 1    | \*\*Room name                   |

### RatePlans

| Element                                                   |      | Description / Format                                                        |
| --------------------------------------------------------- | ---- | --------------------------------------------------------------------------- |
| **RatePlans**                                             |      |                                                                             |
| **RatePlans/RatePlan**                                    | 1    |                                                                             |
| @RatePlanCode                                             | 1    | \*\*The code of the rate booked                                             |
| RatePlanDescription                                       | 1    | \*\*Description of the rate plan                                            |
| **RatePlans/RatePlan/Commission**                         | 0..1 | \*\*Commission amount associated with the rate plan                         |
| **RatePlans/RatePlan/Commission/CommissionPayableAmount** | 1    | \*\*The amount of commission to be paid                                     |
| @Amount                                                   | 1    |                                                                             |
| @CurrencyCode                                             | 1    | \*\*ISO currency code                                                       |
| **RatePlans/RatePlan/MealsIncluded**                      | 0..n | \*\*Used to identify the types of meals included with a rate plan           |
| @MealPlanCodes                                            | 1    | \*\*Meal plan codes outline meal inclusions within rate plan e.g. fullBoard |

### RoomRates

| Element                                          |      | Description / Format                                                                                                                                                                                                                                          |
| ------------------------------------------------ | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RoomRates                                        |      |                                                                                                                                                                                                                                                               |
|   RoomRate                                       | 1    | The rate plan used and the type of room booked. When the daily price breakdown option is set a RoomRate is generated for each night in the stay. When the daily price breakdown option is not set a single RoomRate is generated which covers the whole stay. |
|     @RoomTypeCode                                | 1    | The code identifying the room. This is the same as the @InvTypeCode attribute in other messages.                                                                                                                                                              |
|     @NumberOfUnits                               | 1    | Set to “1” each room has a RoomStay element.                                                                                                                                                                                                                  |
|     @RatePlanCode                                | 0..1 | The code for the rate plan.                                                                                                                                                                                                                                   |
|     @PromotionCode                               | 0..1 | The promotion used in the price for this room stay if any. The attribute will only be set if the daily breakdown of room rate option is enabled.                                                                                                              |
| <p>    @EffectiveDate,</p><p>    @ExpireDate</p> | 0..1 | The start and end dates the rate applies in ISO 8601 date format without time. These attributes will only be set if the daily breakdown of room rate option is enabled and signal the single night for this rate.                                             |
|     Total                                        | 0..1 | The total for this rate for this night. This element is generated only if the daily breakdown of room rate option is enabled.                                                                                                                                 |
|       @AmountAfterTax                            | 1    | The amount charged for this room for this night.                                                                                                                                                                                                              |
|       @CurrencyCode                              | 1    | The currency code for the amount.                                                                                                                                                                                                                             |
|     Rates                                        | 0..1 | See [Rates](reservation.md#rates).                                                                                                                                                                                                                            |
|     ServiceRPHs                                  | 0..1 |                                                                                                                                                                                                                                                               |
|       ServiceRPH                                 | 1..n |                                                                                                                                                                                                                                                               |
|         @RPH                                     | 1    | \*\*This links a Service to the Service information provided at the HotelReservation level (if applicable)                                                                                                                                                    |

### Rates

| Element                 |      | Description / Format                                                                                                                                                                                                                                                                                                               |
| ----------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Rates                   |      |                                                                                                                                                                                                                                                                                                                                    |
|   Rate                  | 1..n |                                                                                                                                                                                                                                                                                                                                    |
|     @RateTimeUnit       | 0..1 | If used, “Day” is the only acceptable value.                                                                                                                                                                                                                                                                                       |
|     @EffectiveDate      | 1    | The start date the rate applies in ISO 8601 date format without time.                                                                                                                                                                                                                                                              |
|     @ExpireDate         | 1    | The end date (not including) of the rate in ISO 8601 date format without time. Example, if rate is on 2018-12-16: 200, 2018-12-17: 200, 2018-12-18: 400. @EffectiveDate would be 2018-12-16 and @ExpireDate would be 2018-12-18 with the rate of 200. The next period would be, @EffectiveDate 2018-12-18, @ExpireDate 2018-12-19. |
|     @UnitMultiplier     | 1    | “1” is the only acceptable value.                                                                                                                                                                                                                                                                                                  |
|     Base                | 1    | Base amount charged                                                                                                                                                                                                                                                                                                                |
|       @CurrencyCode     | 1    | \*\*CurrencyCode uses ISO 4217 codes, that indicates the currency of the rate that is booked.                                                                                                                                                                                                                                      |
|       @AmountAfterTax   | 1    | Total amount after tax.                                                                                                                                                                                                                                                                                                            |
|       @AmountBeforeTax  | 0..1 | Total amount before tax.                                                                                                                                                                                                                                                                                                           |
|       Taxes             | 0..1 |                                                                                                                                                                                                                                                                                                                                    |
|         Tax             | 1..n |                                                                                                                                                                                                                                                                                                                                    |
|           @Type         | 0..1 | \*\*The Type attribute is an enumeration to indicate whether the tax is “inclusive”, “exclusive”, or “cumulative”.                                                                                                                                                                                                                 |
|           @Code         | 0..1 | \*\*The Code attribute refers to OpenTravel Alliance list FTT (fee tax type) and is used to indicate the specific tax or fee that is being transferred.                                                                                                                                                                            |
|           @Amount       | 0..1 | \*\*Amount of the specific tax/fee transferred.                                                                                                                                                                                                                                                                                    |
|           @CurrencyCode | 0..1 | \*\*Currency for the Amount of the specific tax/fee transferred.                                                                                                                                                                                                                                                                   |
|     Total               | 0..1 | Total amount charged including fees.                                                                                                                                                                                                                                                                                               |
|       @CurrencyCode     | 1    | \*\*CurrencyCode uses ISO 4217 codes to indicate the currency of the rate that is being booked.                                                                                                                                                                                                                                    |
|       @AmountAfterTax   | 1    | Total amount after tax.                                                                                                                                                                                                                                                                                                            |
|       @AmountBeforeTax  | 0..1 | Total amount before tax.                                                                                                                                                                                                                                                                                                           |
|       Taxes             | 0..1 |                                                                                                                                                                                                                                                                                                                                    |
|         Tax             | 1..n |                                                                                                                                                                                                                                                                                                                                    |
|           @Type         | 0..1 | \*\*The Type attribute is an enumeration to indicate whether the tax is “inclusive”, “exclusive”, or “cumulative”.                                                                                                                                                                                                                 |
|           @Code         | 0..1 | \*\*The Code attribute refers to OpenTravel Alliance list FTT (fee tax type) and is used to indicate the specific tax or fee that is being transferred.                                                                                                                                                                            |
|           @Amount       | 0..1 | \*\*Amount of the specific tax/fee transferred.                                                                                                                                                                                                                                                                                    |
|           @CurrencyCode | 0..1 | \*\*Currency for the Amount of the specific tax/fee transferred.                                                                                                                                                                                                                                                                   |

### GuestCounts

| Element                |      | Description / Format                                                                                         |
| ---------------------- | ---- | ------------------------------------------------------------------------------------------------------------ |
| GuestCounts            |      |                                                                                                              |
|   GuestCount           | 1..3 | Number of guests in the room. One entry for adults and an optional entry for children.                       |
|     @AgeQualifyingCode | 1    | The code for the age of the guests in this count. Valid values: 10 – Adult 8 – Child.                        |
|     @Count             | 1    | The number of guests.                                                                                        |
|     @ResGuestRPH       | 0..1 | The reference placeholder (RPH) of the guest profile for this room. Appears only on the “Adult” guest count. |

### Total

| Element             |      | Description / Format                                                                                                                                    |
| ------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Total**           |      | The total amount changed for this room.                                                                                                                 |
| @CurrencyCode       | 1    | The currency code for the amount.                                                                                                                       |
| @AmountAfterTax     | 1    | The amount charged for this room. This is the amount displayed to the guest at the time of booking and may not include all taxes.                       |
| @AmountBeforeTax    | 0..1 | \*\*The total amount before tax.                                                                                                                        |
| **Total/Taxes**     | 0..1 |                                                                                                                                                         |
| **Total/Taxes/Tax** | 1..n |                                                                                                                                                         |
| @Type               | 0..1 | \*\*The Type attribute is an enumeration to indicate whether the tax is “inclusive”, “exclusive”, or “cumulative”.                                      |
| @Code               | 0..1 | \*\*The Code attribute refers to OpenTravel Alliance list FTT (fee tax type) and is used to indicate the specific tax or fee that is being transferred. |
| @Amount             | 0..1 | \*\*Amount of the specific tax/fee transferred.                                                                                                         |
| @CurrencyCode       | 0..1 | \*\*Currency for the Amount of the specific tax/fee transferred.                                                                                        |

### Services

| Element                   |      | Description / Format                                                                                                                                                                                      |
| ------------------------- | ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Services                  |      |                                                                                                                                                                                                           |
|   Service                 | 1..n |                                                                                                                                                                                                           |
|     @ServiceInventoryCode | 1    | <p>**The identifier code for the service as given by the source booking channel will be provided here</p><p>Options are: event, extra, extra-bed, extra-person, meal, other, service, surcharge, tour</p> |
|     @ID                   | 0..1 | \*\*The reference id provided for a extra/service by the source booking channel (if provided)                                                                                                             |
|     @ServiceRPH           | 0..1 | \*\*This links a Service to a RoomStay or RatePlan. The absence of a ServiceRPH indicates that this is a HotelReservation level charge                                                                    |
|     @Inclusive            | 1    | \*\*This should always be TRUE because CM will report totals as inclusive of charges and extras                                                                                                           |
|     @Quantity             | 1    | \*\*The number of units included in the charge. This value does not affect the Total amount                                                                                                               |
|     Price                 | 0..1 | See [Price](reservation.md#price).                                                                                                                                                                        |
|     ServiceDetails        | 0..1 |                                                                                                                                                                                                           |
|       TimeSpan            | 0..1 |                                                                                                                                                                                                           |
|         @Start            | 0..1 | \*\*Start date of service. Format: YYYY-MM-DD                                                                                                                                                             |
|         @End              | 0..1 | \*\*Last date of service. Format: YYYY-MM-DD                                                                                                                                                              |

### Price

| Element                |      | Description / Format                                                     |
| ---------------------- | ---- | ------------------------------------------------------------------------ |
| Price                  |      |                                                                          |
|   Base                 | 0..1 |                                                                          |
|     @CurrencyCode      | 0..1 | \*\*The ISO currency code for the unit amount                            |
|     @AmountAfterTax    | 0..1 | \*\*The unit amount after tax                                            |
|     @AmountBeforeTax   | 0..1 | \*\*The unit amount before tax                                           |
|     Taxes              | 0..1 |                                                                          |
|       Tax              | 1..n |                                                                          |
|         @Code          | 1    | \*\*The type of tax being applied to the total. (OTA Fee Tax Type (FTT)) |
|         @Percentage    | 0..1 | \*\*Tax percentage                                                       |
|         @Amount        | 0..1 | \*\*Tax amount                                                           |
|         TaxDescription | 0..1 |                                                                          |
|           Text         | 0..1 | \*\*Text description of the tax                                          |
|   Total                | 1    |                                                                          |
|     @CurrencyCode      | 0..1 | \*\*The ISO currency code for the unit amount                            |
|     @AmountAfterTax    | 0..1 | \*\*The unit amount after tax                                            |
|     @AmountBeforeTax   | 0..1 | \*\*The unit amount before tax                                           |
|     Taxes              | 0..1 |                                                                          |
|       Tax              | 1..n |                                                                          |
|         @Code          | 1    | \*\*The type of tax being applied to the total. (OTA Fee Tax Type (FTT)) |
|         @Percentage    | 0..1 | \*\*Tax percentage                                                       |
|         @Amount        | 0..1 | \*\*Tax amount                                                           |
|         TaxDescription | 0..1 |                                                                          |
|           Text         | 0..1 | \*\*Text description of the tax                                          |
|   RateDescription      | 0..1 |                                                                          |
|     Text               | 0..1 | \*\*A text description of the service/extra                              |

### ResGuests

| Element                |      | Description / Format                                                                                                                     |
| ---------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| ResGuests              |      | Information about the guests in the reservation.                                                                                         |
|   ResGuest             | 1..n |                                                                                                                                          |
|     @ResGuestRPH       | 0..1 | \*\*This value links the ResGuest to RoomStay(s) where possible. You can find the links in RoomStay/ResGuestRPHs.                        |
|     @PrimaryIndicator  | 0..1 | Whether this is the primary guest. Valid values: 1 – for the primary guest 0 – for additional guests.                                    |
|     @ArrivalTime       | 0..1 | \*\*The arrival time of the guest in the form HH:mm:ss                                                                                   |
|     Profiles           | 1    |                                                                                                                                          |
|       ProfileInfo      | 1    |                                                                                                                                          |
|         Profile        | 1    |                                                                                                                                          |
|           @ProfileType | 1    | Type of profile. Set to 1 – Customer                                                                                                     |
|           @RPH         | 0..1 | The reference place holder for this guest profile. This value is used to link this guest to the room stay booked under the guest’s name. |
|         Customer       | 1    | See [Customer](reservation.md#customer).                                                                                                 |
|     ArrivalTransport   | 0..1 |                                                                                                                                          |
|       TransportInfo    | 1..n |                                                                                                                                          |
|         @Type          | 0..1 | \*\*The type of transport the guest used for travelling to destination as provided by booking channel                                    |
|         @ID            | 0..1 | \*\*The transport provider's ID for transportation mode the guest is using. e.g. Flight Number QF123                                     |
|         @Time          | 0..1 | \*\*The transportation arrival time to destination. Format yyyy-MM-ddThh:mm:ss                                                           |
|     DepartureTransport | 0..1 |                                                                                                                                          |
|       TransportInfo    | 1..n |                                                                                                                                          |
|         @Type          | 0..1 | \*\*The type of transport the guest used for travelling from destination as provided by booking channel                                  |
|         @ID            | 0..1 | \*\*The transport provider's ID for transportation mode the guest is using. e.g. Flight Number QF123                                     |
|         @Time          | 0..1 | \*\*The transportation departure time from destination. Format yyyy-MM-ddThh:mm:ss                                                       |

### Customer

| Element                                     |      | Description / Format                                                                                    |
| ------------------------------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| **Customer**                                |      |                                                                                                         |
| **Customer/PersonName**                     | 1    |                                                                                                         |
| NamePrefix                                  | 0..n | \*\*The title of the customer                                                                           |
| GivenName                                   | 0..n | Given name of guest.                                                                                    |
| Surname                                     | 1    | Surname of guest.                                                                                       |
| **Customer/PersonName/Telephone**           | 0..1 |                                                                                                         |
| @PhoneNumber                                | 1    | Contact telephone for guest.                                                                            |
| **Customer/PersonName/Email**               | 0..1 | Contact email guest.                                                                                    |
| **Customer/PersonName/Address**             | 0..1 |                                                                                                         |
| AddressLine                                 | 0..2 | Address line.                                                                                           |
| CityName                                    | 0..1 | City                                                                                                    |
| PostalCode                                  | 0..1 | Postal code.                                                                                            |
| StateProv                                   | 0..1 | \*\*State or province name                                                                              |
| **Customer/PersonName/Address/CountryName** | 0..1 | \*\*Country name                                                                                        |
| @Code                                       | 0..1 | Country code.                                                                                           |
| **Customer/CustLoyalty**                    | 0..n |                                                                                                         |
| @ProgramID                                  | 1    | \*\*The defined membership program name or ID applicable to program. e.g. Qantas                        |
| @MembershipID                               | 1    | \*\*The account identification number for this particular member in this particular program             |
| @ExpireDate                                 | 0..1 | \*\*The expiry date for this particular membership record in this particular program. Format yyyy-MM-dd |

### ResGlobalInfo

| Element                                                    |      | Description / Format                                                                                                                                                                                       |
| ---------------------------------------------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ResGlobalInfo**                                          |      |                                                                                                                                                                                                            |
| **ResGlobalInfo/HotelReservationIDs**                      | 0..1 |                                                                                                                                                                                                            |
| HotelReservationID                                         | 1    | Reservation ID.                                                                                                                                                                                            |
| @ResID\_Type                                               | 1    | Type of reservation ID, set to 14 – Reservation.                                                                                                                                                           |
| @ResID\_Value                                              | 1    | The reservation ID. This is the same number as @ID in UniqueID element of HotelReservation.                                                                                                                |
| **ResGlobalInfo/Comments**                                 | 0..1 |                                                                                                                                                                                                            |
| **ResGlobalInfo/Comments/Comment**                         | 1..n |                                                                                                                                                                                                            |
| Text                                                       | 1    | \*\*Comment text ([PCI sensitive data](https://www.pcisecuritystandards.org/pdfs/pci\_fs\_data\_storage.pdf) is prohibited)                                                                                |
| **ResGlobalInfo/SpecialRequests**                          | 1    |                                                                                                                                                                                                            |
| **ResGlobalInfo/SpecialRequests/SpecialRequest**           | 0..1 |                                                                                                                                                                                                            |
| Text                                                       | 0..1 | Special requests attached to the reservation. Special requests include any free text requests entered by the guests during booking and a description of all extras requested for all rooms in the booking. |
| **ResGlobalInfo/Total**                                    | 1    | See [Total](reservation.md#total).                                                                                                                                                                         |
| **ResGlobalInfo/Guarantee**                                | 0..1 | See [Guarantee](reservation.md#guarantee).                                                                                                                                                                 |
| **ResGlobalInfo/DepositPayments**                          | 0..1 | See [DepositPayments](reservation.md#depositpayments).                                                                                                                                                     |
| **ResGlobalInfo/Profiles**                                 | 1    |                                                                                                                                                                                                            |
| **ResGlobalInfo/Profiles/ProfileInfo**                     | 1    |                                                                                                                                                                                                            |
| **ResGlobalInfo/Profiles/ProfileInfo/UniqueID**            | 0..1 |                                                                                                                                                                                                            |
| @ID                                                        | 1    |                                                                                                                                                                                                            |
| **ResGlobalInfo/Profiles/ProfileInfo/Profile**             | 1    |                                                                                                                                                                                                            |
| @ProfileType                                               | 1    |                                                                                                                                                                                                            |
| **ResGlobalInfo/Profiles/ProfileInfo/Profile/Customer**    | 1..n | See [Customer](reservation.md#customer).                                                                                                                                                                   |
| **ResGlobalInfo/Profiles/ProfileInfo/Profile/CompanyInfo** | 0..n | See [CompanyInfo](reservation.md#companyinfo).                                                                                                                                                             |

### Guarantee

| Element                                                        |      | Description / Format                                                                                                                                       |
| -------------------------------------------------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Guarantee**                                                  |      |                                                                                                                                                            |
| **Guarantee/GuaranteesAccepted**                               | 1    |                                                                                                                                                            |
| **Guarantee/GuaranteesAccepted/GuaranteeAccepted**             | 1    |                                                                                                                                                            |
| **Guarantee/GuaranteesAccepted/GuaranteeAccepted/PaymentCard** | 1    |                                                                                                                                                            |
| @CardType                                                      | 0..1 | Set to 1 (Credit).                                                                                                                                         |
| @CardCode                                                      | 1    | Set to the 2 letter code of the credit card issuer. Valid values: AX – American Express DS – Discovery JC – Japan Credit Bureau MC – Mastercard VI – Visa. |
| @CardNumber                                                    | 0..1 | The number on the guest credit card.                                                                                                                       |
| @SeriesCode                                                    | 0..1 | The verification digits printed on the card (CID/CVV2/CVC2).                                                                                               |
| @ExpireDate                                                    | 0..1 | The expiry date for the card (in MMYY format).                                                                                                             |
| CardHolderName                                                 | 0..1 | The name of the card holder.                                                                                                                               |

### DepositPayments

| Element                                                                                         |      | Description / Format                                                                                                                                                                                                                                            |
| ----------------------------------------------------------------------------------------------- | ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DepositPayments**                                                                             |      |                                                                                                                                                                                                                                                                 |
| **DepositPayments/GuaranteePayment**                                                            | 1    |                                                                                                                                                                                                                                                                 |
| **DepositPayments/GuaranteePayment/AcceptedPayments**                                           | 1    |                                                                                                                                                                                                                                                                 |
| **DepositPayments/GuaranteePayment/AcceptedPayments/AcceptedPayment**                           | 1    |                                                                                                                                                                                                                                                                 |
| **DepositPayments/GuaranteePayment/AcceptedPayments/AcceptedPayment/PaymentCard**               | 1    |                                                                                                                                                                                                                                                                 |
| @CardType                                                                                       | 0..1 | \*\*Always 1 to indicate credit card                                                                                                                                                                                                                            |
| @CardCode                                                                                       | 1    | \*\*The 2 character code of the credit card issuer. Please see the OTA Payment Card Provider Codes table for reference                                                                                                                                          |
| @CardNumber                                                                                     | 0..1 | \*\*This is actual number of the credit card used for deposit/prepayment.                                                                                                                                                                                       |
| @SeriesCode                                                                                     | 0..1 | \*\*The SeriesCode attribute is used (Optionally) for the security number of the card. NOTE: While this attribute is supported in the reservation XML, the details of this attribute are not stored or passed through to the hotel due to PCI-DSS requirements. |
| @ExpireDate                                                                                     | 0..1 | \*\*This is the expiry date of the credit card used for deposit/prepayment. Format MMyy.                                                                                                                                                                        |
| CardHolderName                                                                                  | 0..1 | \*\*The name of the card holder.                                                                                                                                                                                                                                |
| **DepositPayments/GuaranteePayment/AcceptedPayments/AcceptedPayment/PaymentCard/AmountPercent** | 1    |                                                                                                                                                                                                                                                                 |
| @Amount                                                                                         | 1    | \*\*Amount charged as deposit                                                                                                                                                                                                                                   |
| @CurrencyCode                                                                                   | 1    | \*\*Currency of the deposit payment                                                                                                                                                                                                                             |

### CompanyInfo

| Element                                 |      | Description / Format                                                        |
| --------------------------------------- | ---- | --------------------------------------------------------------------------- |
| **CompanyInfo**                         |      |                                                                             |
| CompanyName                             | 1    | \*\*The company Name                                                        |
| **CompanyInfo/TelephoneInfo**           | 0..1 |                                                                             |
| @PhoneNumber                            | 1    | \*\*PhoneNumber, contains the actual number as a string of max 32 character |
| **CompanyInfo/Email**                   | 0..1 | \*\*Email address                                                           |
| **CompanyInfo/AddressInfo**             | 0..1 |                                                                             |
| AddressLine                             | 0..3 | \*\*Address lines                                                           |
| CityName                                | 0..1 | \*\*City                                                                    |
| PostalCode                              | 0..1 | \*\*Post code                                                               |
| StateProv                               | 0..1 | \*\*State or province name                                                  |
| **CompanyInfo/AddressInfo/CountryName** | 0..1 | \*\*Country name                                                            |
| @Code                                   | 1    |                                                                             |

## **ChannelConnect Reservation Email Notification**

CannelConnect has the ability (optional) to communicate reservation notification emails to The Channel Manager hotels (based on some of the key data sent in the OTA\_HotelResNotifRQ). If you are not able to send reservation email notifications to hotels please advise the Integration Analyst supporting you through the development to ChannelConnect. This feature is not automatically part of the ChannelConnect functionality, so you will need to request to have it activated.

## OTA\_HotelResNotifRS <a href="#reservation-ota_hotelresnotifrs" id="reservation-ota_hotelresnotifrs"></a>

### Success Response

```
<OTA_HotelResNotifRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2020-09-10T16:20:32+0700" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc">
  <Success/>
  <HotelReservations>
    <HotelReservation>
      <UniqueID Type="14" ID="0df8bfe7b7bd"/>
      <ResGlobalInfo>
        <HotelReservationIDs>
          <HotelReservationID ResID_Type="14" ResID_Value="000001-0df8bfe7b7bd"/>
        </HotelReservationIDs>
      </ResGlobalInfo>
    </HotelReservation>
  </HotelReservations>
</OTA_HotelResNotifRS>
```

### Failure Response

```
<OTA_HotelResNotifRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2020-09-10T16:20:32+0700" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc">
  <Errors>
    <Error Type="3" Code="402">Cannot find HOTEL</Error>
  </Errors>
</OTA_HotelResNotifRS>
```

### OTA\_HotelResNotifRS Ref.

| Element                  |      | Description / Format                                                                                                                          |
| ------------------------ | ---- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| OTA\_HotelResNotifRS     |      |                                                                                                                                               |
|   @EchoToken             | 1    | \*\*Return the EchoToken from the request message.                                                                                            |
|   @Version               | 1    | \*\*Current version is 1.0                                                                                                                    |
|   @TimeStamp             | 1    | \*\*Time of the transaction.                                                                                                                  |
|   @ResResponseType       | 0..1 | <p>**Shows if the original message was an addition, modification or cancellation.</p><p>Value is one of Committed, Modified,or Cancelled.</p> |
|   Success                | 0..1 | \*\*Should only be present if the request processed successfully. The Errors node should not be present if the Success node is present.       |
|   Errors                 | 0..1 | See [Errors](../error-handling.md#errors).                                                                                                    |
|   HotelReservations      | 0..1 |                                                                                                                                               |
|    HotelReservation      | 1..n |                                                                                                                                               |
|     UniqueID             | 1    |                                                                                                                                               |
|      @Type               | 1    | Always **14** (Reservation)                                                                                                                   |
|      @ID                 | 1    | Reference number/string supplied by the booking agent.                                                                                        |
|     ResGlobalInfo        | 0..1 |                                                                                                                                               |
|      HotelReservationIDs | 0..1 |                                                                                                                                               |
|       HotelReservationID | 1..n |                                                                                                                                               |
|        @ResID\_Type      | 1    | Always **14**                                                                                                                                 |
|        @ResID\_Value     | 1    | The identifier of the reservation created by the Channel Manager.                                                                             |

