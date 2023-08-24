# Samples

### Update BookingLimit

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="004956">
        <AvailStatusMessage BookingLimit="10">
            <StatusApplicationControl Start="2022-06-01" End="2022-12-31" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
                <RestrictionStatus Status="Open">
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

### Update Length Of Stay

#### Set Length Of Stay

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="004956">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-07" End="2022-06-07" InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <LengthsOfStay>
                <LengthOfStay MinMaxMessageType="SetMinLOS" Time="2"/>
                <LengthOfStay MinMaxMessageType="SetMaxLOS" Time="5"/>
            </LengthsOfStay>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-08" End="2022-06-08" InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <LengthsOfStay ArrivalDateBased="1">
                <LengthOfStay MinMaxMessageType="SetMinLOS" Time="10"/>
                <LengthOfStay MinMaxMessageType="SetMaxLOS" Time="20"/>
            </LengthsOfStay>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

#### Remove Length Of Stay

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="004956">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-07" End="2022-06-07" InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <LengthsOfStay>
                <LengthOfStay MinMaxMessageType="RemoveMinLOS"/>
                <LengthOfStay MinMaxMessageType="RemoveMaxLOS"/>
            </LengthsOfStay>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-08" End="2022-06-08" InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <LengthsOfStay ArrivalDateBased="1">
                <LengthOfStay MinMaxMessageType="RemoveMinLOS"/>
                <LengthOfStay MinMaxMessageType="RemoveMaxLOS"/>
            </LengthsOfStay>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

### Update Restriction Status

#### Open Sale

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="004956">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-01" End="2022-12-31" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <RestrictionStatus Status="Open">
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

#### Close Sale

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="004956">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-01" End="2022-12-31" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <RestrictionStatus Status="Close">
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

#### Open Sale on Arrival / Departure

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="004956">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-01" End="2022-06-05" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <RestrictionStatus Status="Open" Restriction="Arrival">
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-10" End="2022-06-15" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <RestrictionStatus Status="Open" Restriction="Departure">
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

#### Close Sale on Arrival / Departure

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="004956">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-01" End="2022-06-05" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <RestrictionStatus Status="Close" Restriction="Arrival">
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-10" End="2022-06-15" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <RestrictionStatus Status="Close" Restriction="Departure">
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

#### Set Min / Max AdvancedBookingOffset

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="004956">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-01" End="2022-06-05" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <RestrictionStatus MinAdvancedBookingOffset="1">
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-06-10" End="2022-06-15" 
                InvTypeCode="Eppyf-13796" RatePlanCode="XYOHO-8487"/>
            <RestrictionStatus MaxAdvancedBookingOffset="10">
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

### Generic Examples

Sets Number of Rooms Available to 10, Clear all restrictions.

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage BookingLimit="10">
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Open"/>
            <LengthsOfStay>
                <LengthOfStay MinMaxMessageType="RemoveMinLOS"/>
                <LengthOfStay MinMaxMessageType="RemoveMaxLOS"/>
            </LengthsOfStay>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <LengthsOfStay ArrivalDateBased="1">
                <LengthOfStay MinMaxMessageType="RemoveMinLOS"/>
                <LengthOfStay MinMaxMessageType="RemoveMaxLOS"/>
            </LengthsOfStay>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Open" Restriction="Arrival"/>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Open" Restriction="Departure"/>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus MinAdvancedBookingOffset="0" MaxAdvancedBookingOffset="0"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Set Booking Limit to 5, close sale, and set LOS 2 / 4, LOS Arrival 3 / 5, Close on Arrival / Departure, Set Min/Max Advanced booking to 1 / 10.

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage BookingLimit="5">
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Close"/>
            <LengthsOfStay>
                <LengthOfStay MinMaxMessageType="SetMinLOS" Time="2"/>
                <LengthOfStay MinMaxMessageType="SetMaxLOS" Time="4"/>
            </LengthsOfStay>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <LengthsOfStay ArrivalDateBased="1">
                <LengthOfStay MinMaxMessageType="SetMinLOS" Time="3"/>
                <LengthOfStay MinMaxMessageType="SetMaxLOS" Time="5"/>
            </LengthsOfStay>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Close" Restriction="Arrival"/>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Close" Restriction="Departure"/>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus MinAdvancedBookingOffset="1" MaxAdvancedBookingOffset="10"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Close Sale by Room

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574"/>
            <RestrictionStatus Status="Close"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Open Sale by Room

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574"/>
            <RestrictionStatus Status="Open"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Close Sale by Rate (Stop Sale by Rate)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Close"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Set BookingLimit

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage BookingLimit="10">
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Open Sale (Stop Sale by Rate)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Open"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Open Restriction on Arrival (CTA)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Open" Restriction="Arrival"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Open Restriction on Departure (CTD)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Open" Restriction="Departure"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Remove MinLOS (Min Night Stay)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <LengthsOfStay>
                <LengthOfStay MinMaxMessageType="RemoveMinLOS"/>
            </LengthsOfStay>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Remove MaxLOS (Max Night Stay)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <LengthsOfStay>
                <LengthOfStay MinMaxMessageType="RemoveMaxLOS"/>
            </LengthsOfStay>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Remove ArrivalDateBased MinLOS (Min Stay Arrival)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <LengthsOfStay ArrivalDateBased="1">
                <LengthOfStay MinMaxMessageType="RemoveMinLOS"/>
            </LengthsOfStay>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Remove ArrivalDateBased MaxLOS (Max Stay Arrival)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <LengthsOfStay ArrivalDateBased="1">
                <LengthOfStay MinMaxMessageType="RemoveMaxLOS"/>
            </LengthsOfStay>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Remove MinAdvancedBookingOffset (Cut Off Date)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus MinAdvancedBookingOffset="0"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Remove MaxAdvancedBookingOffset (Advance Purchase)

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus MaxAdvancedBookingOffset="0"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

### Don't Overlapping Periods in the same REQUEST!

Don't overlap periods for the similar message.

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage BookingLimit="3">
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
        </AvailStatusMessage>
        <AvailStatusMessage BookingLimit="8">
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Send only different periods for the same changes.

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage BookingLimit="3">
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
        </AvailStatusMessage>
        <AvailStatusMessage BookingLimit="8">
            <StatusApplicationControl Start="2022-05-11" End="2022-05-15" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

Update Two Rate Plans

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Close"/>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="RKUII-3231"/>
            <RestrictionStatus Status="Close"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

```
<OTA_HotelAvailNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <AvailStatusMessages HotelCode="002509">
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <RestrictionStatus Status="Close" Restriction="Arrival"/>
        </AvailStatusMessage>
        <AvailStatusMessage>
            <StatusApplicationControl Start="2022-05-05" End="2022-05-11" InvTypeCode="XsPHA-3574" RatePlanCode="RKUII-3231"/>
            <RestrictionStatus Status="Close" Restriction="Departure"/>
        </AvailStatusMessage>
    </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```
