# Reservation XML Sample

```
<OTA_ReadRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
  <ReadRequests>
    <HotelReadRequest HotelCode="000001">
      <SelectionCriteria SelectionType="Undelivered"/>
    </HotelReadRequest>
  </ReadRequests>
</OTA_ReadRQ>
```

Response

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_ResRetrieveRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-05-26T16:16:37+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <Success/>
    <ReservationsList>
        <HotelReservation CreateDateTime="2019-09-17T15:14:28+07:00" LastModifyDateTime="2019-09-20T17:23:04+07:00" ResStatus="Cancel">
            <UniqueID Type="14" ID="1743938"/>
            <RoomStays>
                <RoomStay>
                    <RoomRates>
                        <RoomRate RoomTypeCode="peucw" NumberOfUnits="1" RatePlanCode="GHIJK">
                            <Rates>
                                <Rate EffectiveDate="2019-09-19" ExpireDate="2019-09-19" UnitMultiplier="1">
                                    <Base CurrencyCode="THB" AmountAfterTax="2500.0000"/>
                                </Rate>
                            </Rates>
                        </RoomRate>
                    </RoomRates>
                    <TimeSpan Start="2019-09-19" End="2019-09-20"/>
                    <Total CurrencyCode="THB" AmountAfterTax="2500.0000"/>
                    <BasicPropertyInfo HotelCode="000001"/>
                </RoomStay>
            </RoomStays>
            <ResGlobalInfo>
                <Total CurrencyCode="THB" AmountAfterTax="2500.0000"/>
            </ResGlobalInfo>
        </HotelReservation>
    </ReservationsList>
</OTA_ResRetrieveRS>
```
