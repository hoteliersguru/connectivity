# Daily Rates XML Samples

## Daily Rates

Daily Rates allow for a more detailed rate breakdown of the reservation.

### Grouping Daily Rates

Consecutive dates that contain the same rate value can be bundled into a single Rate element, using the 'EffectiveDate' and 'ExpireDate' to specify the date range. The rate value should be an accumulative total of the dates and not the 'per night' pricing.

### **Same Rate Value Per Night - No Extras or Tax**

The example below shows daily rates when the same rate applies to both dates \(2012-03-12 and 2012-03-13\) and no extra fees and/or charges applies.

In the below example the 'Daily Rate' \(AfterTax\) would be 250.00 because the rate of 500.00 shown in Rates / Rate / Base is across a 2 day date span. For more information on handling 'Daily Rates' please see - [Reservation API / Rates / Rate](reservation.md#rates).

**Daily Rates**

```text
<RoomStay>
  <RoomRates>
    <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
      <Rates>
        <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-14">
          <Base AmountAfterTax="500.00" CurrencyCode="THB"/>
        </Rate>
      </Rates>
    </RoomRate>
  </RoomRates>
  <TimeSpan Start="2012-03-12" End="2012-03-14"/>
  <Total AmountAfterTax="500.00" CurrencyCode="THB">
</RoomStay>
```

**Same Rate Value Per Night - With Extras and Tax**

The example below shows daily rates when the same rate applies to both dates \(2012-03-12 and 2012-03-13\) and there are extra fees and/or charges. 

In the below example the 'Daily Rate' \(Base AmountAfterTax\) would be 225.00 because the rate of 550.00 shown in Rates / Rate / Base is across a 2 day date span. The 'Daily Rate' \(Total AmountAfterTax\) in Rates / Rate / Total is 295.00 as the base amount + extra charges have been spread across the 2 day date span. For more information on handling 'Daily Rates' please see - [Reservation API / Rates / Rate](reservation.md#rates).

**Daily Rates Base and Total Amounts**

```text
<RoomStay>
  <RoomRates>
    <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
      <Rates>
        <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-14">
          <Base AmountBeforeTax="495.50" AmountAfterTax="550.00" CurrencyCode="THB"/>
          <Total AmountBeforeTax="531.00" AmountAfterTax="590.00" CurrencyCode="THB"/>
        </Rate>
      </Rates>
    </RoomRate>
  </RoomRates>
  <TimeSpan Start="2012-03-12" End="2012-03-14"/>
  <Total AmountBeforeTax="531.00" AmountAfterTax="590.00" CurrencyCode="THB">
    <Taxes>
      <Tax Amount="59.00" CurrencyCode="THB"/>
    </Taxes>
  </Total>
</RoomStay>
```

**Differing Rate Values Per Night - With Tax**

The example below shows daily rates when the rate amount differs for the booked dates.

**Daily Rates - Multiple rate amounts**

```text
<RoomStay>
  <RoomRates>
    <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
      <Rates>
        <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-13">
          <Base AmountBeforeTax="252.00" AmountAfterTax="280.00" CurrencyCode="THB"/>
        </Rate>
        <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-13" ExpireDate="2012-03-14">
          <Base AmountBeforeTax="279.00" AmountAfterTax="310.00" CurrencyCode="THB"/>
        </Rate>
      </Rates>
    </RoomRate>
  </RoomRates>
  <TimeSpan Start="2012-03-12" End="2012-03-14"/>  
  <Total AmountBeforeTax="531.00" AmountAfterTax="590.00" CurrencyCode="THB">
    <Taxes>
      <Tax Amount="59.00" CurrencyCode="THB"/>
    </Taxes>
  </Total>
</RoomStay>
```

**Combination Differing Rate Values and Consecutive Rate Values Per Night - With Tax**

The example below shows a combination of rates, where a 4 night reservation is made containing consecutive rates for only 2 of the nights.

**Multiple Rate Amounts with Consecutive Rates**

```text
<RoomStay>
    <RoomRates>
        <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
            <Rates>
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-13" ExpireDate="2012-03-14">
                    <Base AmountBeforeTax="181.82" AmountAfterTax="200.00" CurrencyCode="THB"/>
                </Rate>
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-14" ExpireDate="2012-03-16">
                    <Base AmountBeforeTax="409.09" AmountAfterTax="450.00" CurrencyCode="THB"/>
                </Rate>
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-16" ExpireDate="2012-03-17">
                    <Base AmountBeforeTax="181.82" AmountAfterTax="200.00" CurrencyCode="THB"/>
                </Rate>
            </Rates>
        </RoomRate>
    </RoomRates>
    <TimeSpan Start="2012-03-13" End="2012-03-17"/>
    <Total AmountBeforeTax="772.73" AmountAfterTax="850.00" CurrencyCode="THB">
        <Taxes>
            <Tax Amount="77.27" CurrencyCode="THB"/>
        </Taxes>
    </Total>
</RoomStay>
```

