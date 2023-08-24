# Rates

ChannelConnect will send through updates for rates using the **OTA\_HotelRateAmountNotifRQ**. The receiving channel should process the updates and response with the **OTA\_HotelRateAmountNotifRS** as a receipt of success or failure.

## OTA\_HotelRateAmountNotifRQ

A OTA\_HotelRateAmountNotifRQ message will be pushed to a connected channel's web service after the value changes in The Channel Manager. The message can be used to update the rates for one or more room types for a single hotel. Specifically :

* Room rates
* Room inclusions

Each OTA\_HotelRateAmountNotifRQ message contains a single **RateAmountMessages** element which indicates the hotel to update using the RateAmountMessages/@HotelCode attribute. The RateAmountMessages/RateAmountMessage elements will contain the updates to process over a date range. There can be several RateAmountMessage updates per request, however each request will be limited to one hotel and one room.

#### **Additional ChannelConnect Rate PUSH Features**

It should be noted that by default, The Channel Manager is room occupancy agnostic and does not support 'Occupancy Based Pricing' at present. The rate the hotel sets in The Channel Manager for a particular room rate is generally for the base occupancy level for that room. Optional features that can be added to your ChannelConnect integration allow more definition around occupancy and additional guest charges. Please see below.

There are a number of features listed below that allow more definition around occupancy and additional guest charges \(XML examples are shown below\):

* 'Included Occupancy' value to be specified for a base room rate.
* 'Single Guest Discount' rate to be specified relative to a higher occupancies base room rate amount.
* 'Extra Guest' charges to be specified relative to the base room rate \(with or without base occupancies defined\).

_**\*\*All the above mentioned features are optional, and should be discussed with the API Development team during your development phase if needed to satisfy any business logic/requirements.\*\***_

The basic structure of the message is as follows:

```text
<OTA_HotelRateAmountNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" TimeStamp="2005-08-01T09:30:47+08:00" Version="1.0" EchoToken="abc123">
  <RateAmountMessages HotelCode="HOTEL">
    <RateAmountMessage>
      <StatusApplicationControl Start="2010-01-01" End="2010-01-01" InvTypeCode="A1K" RatePlanCode="BAR"/>
      <!-- Content omitted -->
    </RateAmountMessage>
    <RateAmountMessage>
      <StatusApplicationControl Start="2010-01-02" End="2010-01-02" InvTypeCode="A1K" RatePlanCode="BAR"/>
      <!-- Content omitted -->
    </RateAmountMessage>
    <RateAmountMessage>
      <StatusApplicationControl Start="2010-01-04" End="2010-01-04" InvTypeCode="A1K" RatePlanCode="BAR"/>
      <!-- Content omitted -->
    </RateAmountMessage>
  </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

### StatusApplicationControl

This element must appear once in each RateAmountMessage element. The StatusApplicationControl element is used to specify the room type, rate code and dates for which the update applies. The dates affected by the update are controlled by the mandatory @Start and @End attributes.

#### Setting Rates 

ChannelConnect will send through rate updates using the BaseByGuestAmount element. The value of @AmountAfterTax will be a positive decimal value.

#### Setting Rate XML

NOTE: This is the default rate XML you will receive if no additional rate features are used for your integration to ChannelConnect. See above for more information on these features.

```text
<OTA_HotelRateAmountNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" TimeStamp="2005-08-01T09:30:47+08:00" Version="1.0" EchoToken="abc123">
  <RateAmountMessages HotelCode="HOTEL">
    <RateAmountMessage>
      <StatusApplicationControl InvTypeCode="A1K" RatePlanCode="BAR" Start="2010-01-01" End="2010-01-01"/>
      <Rates>
        <Rate>
          <BaseByGuestAmts>
            <BaseByGuestAmt AgeQualifyingCode="10" AmountAfterTax="123.00"/>
          </BaseByGuestAmts>
        </Rate>
      </Rates>
    </RateAmountMessage>
  </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

#### Setting Rate With 'Inclusions' XML

NOTE: This feature is optional and must be added to your integration via certification with the API Development team.

```text
<OTA_HotelRateAmountNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" TimeStamp="2005-08-01T09:30:47+08:00" Version="1.0" EchoToken="abc123">
  <RateAmountMessages HotelCode="HOTEL">
    <RateAmountMessage>
      <StatusApplicationControl InvTypeCode="A1K" RatePlanCode="BAR" Start="2010-01-01" End="2010-01-01"/>
      <Rates>
        <Rate>
          <BaseByGuestAmts>
            <BaseByGuestAmt AgeQualifyingCode="10" AmountAfterTax="123.00"/>
          </BaseByGuestAmts>
          <RateDescription>
            <Text>Buffet Breakfast and ticket to Museum</Text>
          </RateDescription>
        </Rate>
      </Rates>
    </RateAmountMessage>
  </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

#### Setting Rate With Additional Guest Amounts XML

NOTE: This feature is optional and must be added to your integration via certification with the API Development team.

```text
<OTA_HotelRateAmountNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" TimeStamp="2005-08-01T09:30:47+08:00" Version="1.0" EchoToken="abc123">
  <RateAmountMessages HotelCode="HOTEL">
    <RateAmountMessage>
      <StatusApplicationControl InvTypeCode="A1K" RatePlanCode="BAR" Start="2010-01-01" End="2010-01-01"/>
      <Rates>
        <Rate>
          <BaseByGuestAmts>
             <BaseByGuestAmt AgeQualifyingCode="10" AmountAfterTax="123.00"/>
          </BaseByGuestAmts>
          <AdditionalGuestAmounts>
            <AdditionalGuestAmount AgeQualifyingCode="10" Amount="20"/>
            <AdditionalGuestAmount AgeQualifyingCode="8" Amount="10"/>
          </AdditionalGuestAmounts>
        </Rate>
      </Rates>
    </RateAmountMessage>
  </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

#### Setting Rate With Included Occupancy XML

NOTE: The included occupancy value is set manually in The Channel Manager by the hotelier \(if you are using this feature in your integration\). If an 'Included Occupancy' value is not set, you will receive a rate update as per the 'Setting Rate XML' example. This feature is optional and must be added to your integration via certification with the API Development team.

```text
<OTA_HotelRateAmountNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" TimeStamp="2005-08-01T09:30:47+08:00" Version="1.0" EchoToken="abc123">
  <RateAmountMessages HotelCode="HOTEL">
    <RateAmountMessage>
      <StatusApplicationControl InvTypeCode="A1K" RatePlanCode="BAR" Start="2010-01-01" End="2010-01-01"/>
      <Rates>
        <Rate>
          <BaseByGuestAmts>
            <BaseByGuestAmt AgeQualifyingCode="10" NumberOfGuests="2" AmountAfterTax="123.00"/>
          </BaseByGuestAmts>
        </Rate>
      </Rates>
    </RateAmountMessage>
  </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

#### Setting Rate with a Single Guest Discount XML

NOTE: Single Guest Discount is only for use when a discount applies to a room that normally includes more than 1 guest in the base room rate amount. So for a example you have a 1 Bedroom Apartment that usually includes 3 guests in the base rate, but you wish to also offer a discounted rate if only 1 guest stays in the same room, you would use the Single Guest Discount feature. If you wish to have a rate for a Single Room, then you would setup a separate room rate with a base rate for 1 guest. This feature is optional and must be added to your integration via certification with the API Development team.

```text
<OTA_HotelRateAmountNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" TimeStamp="2005-08-01T09:30:47+08:00" Version="1.0" EchoToken="abc123">
  <RateAmountMessages HotelCode="HOTEL">
    <RateAmountMessage>
      <StatusApplicationControl InvTypeCode="A1K" RatePlanCode="BAR" Start="2010-01-01" End="2010-01-01"/>
      <Rates>
        <Rate>
          <BaseByGuestAmts>
             <BaseByGuestAmt AgeQualifyingCode="10" NumberOfGuests="1" AmountAfterTax="112.00"/>
             <BaseByGuestAmt AgeQualifyingCode="10" AmountAfterTax="123.00"/>
          </BaseByGuestAmts>
        </Rate>
      </Rates>
    </RateAmountMessage>
  </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

#### Setting Rate With Included Occupancy & Single Guest Discount XML

```text
<OTA_HotelRateAmountNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" TimeStamp="2005-08-01T09:30:47+08:00" Version="1.0" EchoToken="abc123">
  <RateAmountMessages HotelCode="HOTEL">
    <RateAmountMessage>
      <StatusApplicationControl InvTypeCode="A1K" RatePlanCode="BAR" Start="2010-01-01" End="2010-01-01"/>
      <Rates>
        <Rate>
          <BaseByGuestAmts>
             <BaseByGuestAmt AgeQualifyingCode="10" NumberOfGuests="1" AmountAfterTax="112.00"/>
             <BaseByGuestAmt AgeQualifyingCode="10" NumberOfGuests="2" AmountAfterTax="123.00"/>
          </BaseByGuestAmts>
        </Rate>
      </Rates>
    </RateAmountMessage>
  </RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

### **Ref** OTA\_HotelRateAmountNotifRQ

<table>
  <thead>
    <tr>
      <th style="text-align:left">Element</th>
      <th style="text-align:left"></th>
      <th style="text-align:left">Description / Format</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">OTA_HotelRateAmountNotifRQ</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Root element of the message.</td>
    </tr>
    <tr>
      <td style="text-align:left">@EchoToken</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Unique identifier for this request.</td>
    </tr>
    <tr>
      <td style="text-align:left">@Version</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Current version is 1.0.</td>
    </tr>
    <tr>
      <td style="text-align:left">@TimeStamp</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Time of the transaction in ISO 8601 format.</td>
    </tr>
    <tr>
      <td style="text-align:left">RateAmountMessages</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">@HotelCode</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">RateAmountMessage</td>
      <td style="text-align:left">1..n</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">StatusApplicationControl</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Contains date and room identification information.</td>
    </tr>
    <tr>
      <td style="text-align:left">@Start, @End</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">The start and end dates for which the availability update is being sent
        in ISO 8601 format (without time). These dates are inclusive and use the
        hotel time-zone. If a time period is also specified in a Rate element it
        has precedence over this one. Either this or the Rate element time periods
        must be specified.</td>
    </tr>
    <tr>
      <td style="text-align:left">@InvTypeCode</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Identifies the room.</td>
    </tr>
    <tr>
      <td style="text-align:left">@RatePlanCode</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">Identifies the rate plan. If not provided the standard rate plan is assumed.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>@Mon, @Tue, @Weds,</p>
        <p>@Thur, @Fri, @Sat,</p>
        <p>@Sun</p>
      </td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">Used to communicate which days of the week the update applies to. If one
        is set, they must all be set. Valid values: &#x201C;0&#x201D; &#x2013;
        Does not apply &#x201C;1&#x201D; &#x2013; Applies.</td>
    </tr>
    <tr>
      <td style="text-align:left">Rates</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">See <a href="rates.md#ref-rates">Rates</a>.</td>
    </tr>
  </tbody>
</table>

### Ref Rates

<table>
  <thead>
    <tr>
      <th style="text-align:left">Element</th>
      <th style="text-align:left"></th>
      <th style="text-align:left">Description / Format</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Rates</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Rate</td>
      <td style="text-align:left">1..n</td>
      <td style="text-align:left">The root element for the rate of a room.</td>
    </tr>
    <tr>
      <td style="text-align:left">@CurrencyCode</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">@Start, @End</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">The start and end dates for which the rate update is being sent in ISO
        8601 format (without time). These dates are inclusive and use the hotel
        time-zone. This time period has precedence over the time period in the
        StatusApplicationControl element if specified. Either this or the StatusApplicationControl
        element time periods must be specified.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>@Mon, @Tue, @Weds, @Thur,</p>
        <p>@Fri, @Sat, @Sun</p>
      </td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">Used to communicate which days of the week the update applies to. If one
        is set, they must all be set. Valid values: &#x201C;0&#x201D; &#x2013;
        Does not apply &#x201C;1&#x201D; &#x2013; Applies.</td>
    </tr>
    <tr>
      <td style="text-align:left">BaseByGuestAmts</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">BaseByGuestAmt</td>
      <td style="text-align:left">1..n</td>
      <td style="text-align:left">The rate for the base number of guests in a room.</td>
    </tr>
    <tr>
      <td style="text-align:left">@AmountAfterTax</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">The amount after tax for this base rate. Either this attribute or @AmountBeforeTax
        must be specified.</td>
    </tr>
    <tr>
      <td style="text-align:left">@AmountBeforeTax</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">The amount before tax for this base rate. Either this attribute or @AmountAfterTax
        must be specified.</td>
    </tr>
    <tr>
      <td style="text-align:left">@NumberOfGuests</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">The base number of guests for the rate. If not present the rate is per
        room.</td>
    </tr>
    <tr>
      <td style="text-align:left">@AgeQualifyingCode</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">The age group this base rate refers to. Must be set to &#x201C;10&#x201D;
        (adult).</td>
    </tr>
    <tr>
      <td style="text-align:left">@CurrencyCode</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">AdditionalGuestAmounts</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">AdditionalGuestAmount</td>
      <td style="text-align:left">1..2</td>
      <td style="text-align:left">The rate for additional guests. This element is only valid if BaseByGuestAmt
        elements are present.</td>
    </tr>
    <tr>
      <td style="text-align:left">@Amount</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">The amount for an additional guest.</td>
    </tr>
    <tr>
      <td style="text-align:left">@TaxInclusive</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">Whether the @Amount is tax inclusive. Valid values: 1 &#x2013; true 0
        &#x2013; false.</td>
    </tr>
    <tr>
      <td style="text-align:left">@CurrencyCode</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">@AgeQualifyingCode</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">The age group of the additional guest. Valid values: 10 &#x2013; Additional
        Adult. 8 &#x2013; Additional Child.</td>
    </tr>
    <tr>
      <td style="text-align:left">RateDescription</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Text</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

## OTA\_HotelRateAmountNotifRS

The OTA\_HotelRateAmountNotifRS should be returned for any request pushed by ChannelConnect. It must be returned in a SOAP envelope, however the SOAP Header can be empty. The EchoToken received in the request should be mirrored back in the response.

#### Success Response XML <a id="Rates-SuccessResponseXML"></a>

```text
<OTA_HotelRateAmountNotifRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <Success/>
</OTA_HotelRateAmountNotifRS>
```

#### Error Response XML - For more information on error handling, please refer to our [Error Handling](../error-handling.md) page. <a id="Rates-ErrorResponseXML-Formoreinformationonerrorhandling,pleaserefertoourErrorHandlingpage."></a>

```text
<OTA_HotelRateAmountNotifRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <Errors>
    <Error Type="3" Code="402">Cannot find room with code RC1</Error>
  </Errors>
</OTA_HotelRateAmountNotifRS>
```

### Ref OTA\_HotelRateAmountNotifRS

| Element |  | Description / Format |
| :--- | :--- | :--- |
| OTA\_HotelRateAmountNotifRS |  |  |
|   @EchoToken | 1 |  |
|   @Version | 1 |  |
|   @TimeStamp | 1 |  |
|   Success | 0..1 |  |
|   Errors | 0..1 | See [Errors](../error-handling.md#errors). |

