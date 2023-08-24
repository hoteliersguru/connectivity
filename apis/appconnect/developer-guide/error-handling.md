# Error Handling

Error messages all are of type 12, and have the Code 320, the message have just enough information for you to narrow down the issue.

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelRateAmountNotifRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-05-04T12:13:57+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <Errors>
        <Error Type="12" Code="320">Invalid value</Error>
    </Errors>
</OTA_HotelRateAmountNotifRS>
```

| Code | Message                                                              |
| ---- | -------------------------------------------------------------------- |
| 320  | Invalid value                                                        |
| 320  | TimeStamp missing or invalid                                         |
| 320  | EchoToken missing                                                    |
| 320  | HotelCode missing or invalid                                         |
| 320  | StatusApplicationControl:{DayOfTheWeek} missing or invalid           |
| 320  | AvailStatusMessage/RateAmountMessage missing or invalid              |
| 320  | AvailStatusMessage:BookingLimit invalid                              |
| 320  | BaseByGuestAmt:AmountAfterTax invalid                                |
| 320  | RestrictionStatus:Status invalid                                     |
| 320  | LengthOfStay:Time missing or invalid                                 |
| 320  | RestrictionStatus:MaxAdvancedBookingOffset missing or invalid        |
| 320  | AdditionalGuestAmount:Amount invalid                                 |
| 320  | StatusApplicationControl:Start/End missing or invalid                |
| 320  | StatusApplicationControl:InvTypeCode/RatePlanCode missing or invalid |
