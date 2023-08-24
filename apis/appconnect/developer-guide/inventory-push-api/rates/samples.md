# Samples

Set Base amount to 123.

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <RateAmountMessages HotelCode="002509">
        <RateAmountMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <Rates>
                <Rate>
                    <BaseByGuestAmts>
                        <BaseByGuestAmt AmountAfterTax="123.00"/>
                    </BaseByGuestAmts>
                </Rate>
            </Rates>
        </RateAmountMessage>
    </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

Set Base amount to 150, set amount to 100 for additional adult guests, and 50 for additional children, also set Inclusion text.

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <RateAmountMessages HotelCode="002509">
        <RateAmountMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <Rates>
                <Rate>
                    <BaseByGuestAmts>
                        <BaseByGuestAmt AmountAfterTax="150"/>
                    </BaseByGuestAmts>
                    <AdditionalGuestAmounts>
                        <AdditionalGuestAmount Amount="100" AgeQualifyingCode="10"/>
                        <AdditionalGuestAmount Amount="50" AgeQualifyingCode="8"/>
                    </AdditionalGuestAmounts>
                    <RateDescription>
                        <Text>Inclusion with this rate</Text>
                    </RateDescription>
                </Rate>
            </Rates>
        </RateAmountMessage>
    </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

Set Base amount to 100, and remove Additional Guest Amounts, remove Inclusion text.

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <RateAmountMessages HotelCode="002509">
        <RateAmountMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-10" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <Rates>
                <Rate>
                    <BaseByGuestAmts>
                        <BaseByGuestAmt AmountAfterTax="100"/>
                    </BaseByGuestAmts>
                    <AdditionalGuestAmounts>
                        <AdditionalGuestAmount Amount="0" AgeQualifyingCode="10"/>
                        <AdditionalGuestAmount Amount="0" AgeQualifyingCode="8"/>
                    </AdditionalGuestAmounts>
                    <RateDescription>
                        <Text></Text>
                    </RateDescription>
                </Rate>
            </Rates>
        </RateAmountMessage>
    </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

Set Amount for Adults to 80

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <RateAmountMessages HotelCode="002509">
        <RateAmountMessage>
            <StatusApplicationControl Start="2022-05-05" End="2022-05-05" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <Rates>
                <Rate>
                    <AdditionalGuestAmounts>
                        <AdditionalGuestAmount Amount="80" AgeQualifyingCode="10"/>
                    </AdditionalGuestAmounts>
                </Rate>
            </Rates>
        </RateAmountMessage>
    </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

Set Amount for Children to 40.

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <RateAmountMessages HotelCode="002509">
        <RateAmountMessage>
            <StatusApplicationControl Start="2022-05-05" End="2022-05-15" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <Rates>
                <Rate>
                    <AdditionalGuestAmounts>
                        <AdditionalGuestAmount Amount="40" AgeQualifyingCode="8"/>
                    </AdditionalGuestAmounts>
                </Rate>
            </Rates>
        </RateAmountMessage>
    </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

Set Base Rate to 20, and Inclusion to "Super Deal".

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <RateAmountMessages HotelCode="002509">
        <RateAmountMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-05-04" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <Rates>
                <Rate>
                    <BaseByGuestAmts>
                        <BaseByGuestAmt AmountAfterTax="20"/>
                    </BaseByGuestAmts>
                    <RateDescription>
                        <Text>Super Deal</Text>
                    </RateDescription>
                </Rate>
            </Rates>
        </RateAmountMessage>
    </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

Set Inclusion

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <RateAmountMessages HotelCode="002509">
        <RateAmountMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <Rates>
                <Rate>
                    <RateDescription>
                        <Text>Free Tour of your selection, limited availability.</Text>
                    </RateDescription>
                </Rate>
            </Rates>
        </RateAmountMessage>
    </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

Set base amount to 1000, and clear adult and child amounts, removes inclusion text.

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2022-04-08T14:22:30+07:00" EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
    <RateAmountMessages HotelCode="002509">
        <RateAmountMessage>
            <StatusApplicationControl Start="2022-05-04" End="2022-12-31" InvTypeCode="XsPHA-3574" RatePlanCode="ZPPXJ-3230"/>
            <Rates>
                <Rate>
                    <BaseByGuestAmts>
                        <BaseByGuestAmt AmountAfterTax="1000"/>
                    </BaseByGuestAmts>
                    <AdditionalGuestAmounts>
                        <AdditionalGuestAmount Amount="0" AgeQualifyingCode="10"/>
                        <AdditionalGuestAmount Amount="0" AgeQualifyingCode="8"/>
                    </AdditionalGuestAmounts>
                    <RateDescription>
                        <Text></Text>
                    </RateDescription>
                </Rate>
            </Rates>
        </RateAmountMessage>
    </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```
