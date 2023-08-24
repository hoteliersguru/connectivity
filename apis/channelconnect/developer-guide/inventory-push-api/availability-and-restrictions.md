# Availability and Restrictions

ChannelConnect will send through updates for availability and restrictions using the **OTA\_HotelAvailNotifRQ**. The connected channel should process the updates and respond with the **OTA\_HotelAvailNotifRS** as a receipt of success or failure to process the request.

## OTA\_HotelAvailNotifRQ <a id="AvailabilityandRestrictions-OTA_HotelAvailNotifRQ"></a>

An OTA\_HotelAvailNotifRQ message will be pushed to a connected channel's web service after the value changes in The Channel Manager. The message can be used to update the availability and restrictions for one room type for a single hotel. Specifically:

* Room availability
* Stop sell or 'close out' of a room
* Closed to arrival
* Closed to departure
* Minimum stays
* Maximum stays

Each OTA\_HotelAvailNotifRQ message contains a single **AvailStatusMessages** element which indicates the hotel to update using the AvailStatusMessages/@HotelCode attribute. The AvailStatusMessages/AvailStatusMessage elements will contain the updates to process over a date range. There can be several AvailStatusMessage updates per request, however each request will be limited to one hotel and one room.

The basic structure of the message is as follows:

```text
<OTA_HotelAvailNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <AvailStatusMessages HotelCode="HOTEL">
    <AvailStatusMessage>
      <StatusApplicationControl Start="2010-01-01" End="2010-01-01" InvTypeCode="A1K" RatePlanCode="GLD" />
        <!-- Content omitted -->
    </AvailStatusMessage>
    <AvailStatusMessage>
      <StatusApplicationControl Start="2010-01-02" End="2010-01-02" InvTypeCode="A1K" RatePlanCode="GLD" />
        <!-- Content omitted -->
    </AvailStatusMessage>
    <AvailStatusMessage>
      <StatusApplicationControl Start="2010-01-03" End="2010-01-03" InvTypeCode="A1K" RatePlanCode="GLD" />
        <!-- Content omitted -->
    </AvailStatusMessage>
   </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

#### StatusApplicationControl <a id="AvailabilityandRestrictions-StatusApplicationControl"></a>

This element must appear once in each AvailStatusMessage element. The StatusApplicationControl element is used to specify the room type, rate code and dates for which the update applies. The dates affected by the update are controlled by the mandatory @Start and @End attributes.

### Setting Availability

ChannelConnect will send through availability updates using the **AvailStatusMessage/@BookingLimit** attribute. The value of @BookingLimit will be a positive integer value.

```text
<OTA_HotelAvailNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <AvailStatusMessages HotelCode="HOTEL">
    <AvailStatusMessage BookingLimit="10">
      <StatusApplicationControl Start="2012-01-01" End="2012-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <RestrictionStatus Status="Open" />
    </AvailStatusMessage>
  </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

### Setting Stop Sells, Closed to Arrival and Closed to Departure

Stop sell, closed to arrival and closed to departure updates will be sent through using the **RestrictionStatus** node.Below is a set of scenarios where SiteConnect will send an update through.

Note that stop sells, closed to arrival and closed to departure can be sent separately by SiteConnect so their status should be assumed as separate. For example a message which has a 'Open' status without a 'Restriction="Arrival"' should not change the state of the closed to arrival.

#### Set StopSell

```text
<OTA_HotelAvailNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <AvailStatusMessages HotelCode="HOTEL">
    <AvailStatusMessage BookingLimit="10">
      <StatusApplicationControl Start="2012-01-01" End="2012-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <RestrictionStatus Status="Close" />
    </AvailStatusMessage>
  </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

**Set Closed to Arrival**

```text
<OTA_HotelAvailNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <AvailStatusMessages HotelCode="HOTEL">
    <AvailStatusMessage>
      <StatusApplicationControl Start="2012-01-01" End="2012-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <RestrictionStatus Status="Close" Restriction="Arrival"/>
    </AvailStatusMessage>
  </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

**Set Closed to Departure**

```text
<OTA_HotelAvailNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <AvailStatusMessages HotelCode="HOTEL">
    <AvailStatusMessage>
      <StatusApplicationControl Start="2012-01-01" End="2012-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <RestrictionStatus Status="Close" Restriction="Departure"/>
    </AvailStatusMessage>
  </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

### Setting Minimum Stay

ChannelConnect will send through minimum stay updates using the LengthsOfStay element. This element contains a single **LengthOfStay** element with the attributes @MinMaxMessageType and @Time. MinMaxMessageType has a fixed value of "SetMinLOS" and the @Time it the minimum stay period in days.

**Set MinLOS 2**

```text
<OTA_HotelAvailNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <AvailStatusMessages HotelCode="HOTEL">
    <AvailStatusMessage>
      <StatusApplicationControl Start="2010-01-01" End="2010-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <LengthsOfStay>
        <LengthOfStay MinMaxMessageType="SetMinLOS" Time="2"/>
      </LengthsOfStay>
    </AvailStatusMessage>
  </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

### Setting Maximum Stay

Maximum stay updates will be delivered in the same LengthsOfStay element as minimum stay. If maximum stay is removed, the @Time element will be missing where @MinMaxMessageType is "SetMaxLOS".

**Set MaxLOS**

```text
<AvailStatusMessage>
  <StatusApplicationControl Start="2010-01-01" End="2010-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
  <LengthsOfStay>
    <LengthOfStay MinMaxMessageType="SetMaxLOS" Time="7"/>
  </LengthsOfStay>
</AvailStatusMessage>
```

**No MaxLOS**

```text
<AvailStatusMessage>
  <StatusApplicationControl Start="2010-01-01" End="2010-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
  <LengthsOfStay>
    <LengthOfStay MinMaxMessageType="SetMaxLOS"/>
  </LengthsOfStay>
</AvailStatusMessage>
```

### Update all values example request

Below is a sample request for a message that updates availability, stop sell, MinLOS, closed to arrival and closed to departure.

```text
<OTA_HotelAvailNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <AvailStatusMessages HotelCode="HOTEL">
    <AvailStatusMessage BookingLimit="10">
      <StatusApplicationControl Start="2012-01-01" End="2012-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <RestrictionStatus Status="Close" />
    </AvailStatusMessage>
    <AvailStatusMessage>
      <StatusApplicationControl Start="2012-01-01" End="2012-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <LengthsOfStay>
        <LengthOfStay MinMaxMessageType="SetMinLOS" Time="2"/>
        <LengthOfStay MinMaxMessageType="SetMaxLOS" Time="7"/>
      </LengthsOfStay>
    </AvailStatusMessage>
    <AvailStatusMessage>
      <StatusApplicationControl Start="2012-01-01" End="2012-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <RestrictionStatus Status="Close" Restriction="Arrival"/>
    </AvailStatusMessage>
    <AvailStatusMessage>
      <StatusApplicationControl Start="2012-01-01" End="2012-01-01" InvTypeCode="A1K" RatePlanCode="GLD"/>
      <RestrictionStatus Status="Close" Restriction="Departure"/>
    </AvailStatusMessage>
  </AvailStatusMessages>
</OTA_HotelAvailNotifRQ>
```

### **Ref** OTA\_HotelAvailNotifRQ

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
      <td style="text-align:left">OTA_HotelAvailNotifRQ</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Root element of the message</td>
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
      <td style="text-align:left">AvailStatusMessages</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Contains the availability messages.</td>
    </tr>
    <tr>
      <td style="text-align:left">@HotelCode</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">This is the code of the property whose availability is being updated.</td>
    </tr>
    <tr>
      <td style="text-align:left">AvailStatusMessage</td>
      <td style="text-align:left">1..n</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">@BookingLimit</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">Sets the number of rooms available for sale per day. Room availability
        is always set at the room level regardless of the value of the @RatePlanCode
        attribute.</td>
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
        hotel time-zone.</td>
    </tr>
    <tr>
      <td style="text-align:left">@InvTypeCode</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Identifies the room.</td>
    </tr>
    <tr>
      <td style="text-align:left">@RatePlanCode</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Identifies the rate plan.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>@Mon, @Tue, @Weds,</p>
        <p>@Thur, @Fri, @Sat,</p>
        <p>@Sun</p>
      </td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">Used to communicate which days of the week the update applies to. If one
        is set, they must all be set. Valid values:&#x2019; &#x201C;0&#x201D; &#x2013;
        Does not apply &#x201C;1&#x201D; &#x2013; Applies.</td>
    </tr>
    <tr>
      <td style="text-align:left">LengthsOfStay</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">The rate&#x2019;s minimum and maximum length of stay.</td>
    </tr>
    <tr>
      <td style="text-align:left">LengthOfStay</td>
      <td style="text-align:left">1..2</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">@MinMaxMessageType</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">The type of length of stay restriction set. Valid values: &#x201C;SetMinLOS&#x201D;,
        &#x201C;RemoveMinLOS&#x201D; &#x2013; Sets, removes the minimum length
        of stay. &#x201C;SetMaxLOS&#x201D;, &#x201C;RemoveMaxLOS&#x201D; &#x2013;
        Sets, removes the maximum length of stay.</td>
    </tr>
    <tr>
      <td style="text-align:left">@Time</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">The number of days for the length of stay restriction. This attribute
        is required when setting the restriction and must not be set when removing
        it.</td>
    </tr>
    <tr>
      <td style="text-align:left">RestrictionStatus</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">The rate&#x2019;s open/close restrictions.</td>
    </tr>
    <tr>
      <td style="text-align:left">@Status</td>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Status of the restriction. Valid values &#x201C;Close&#x201D; &#x2013;
        Specifies a Close restriction. The room is closed for sales and cannot
        be sold. &#x201C;Open&#x201D; &#x2013; Specifies an Open restriction. The
        room is Open for sale. This removes a previous Close restriction.</td>
    </tr>
    <tr>
      <td style="text-align:left">@Restriction</td>
      <td style="text-align:left">0..1</td>
      <td style="text-align:left">Specifies the type of restriction. Valid values are: &#x201C;Arrival&#x201D;
        &#x2013; Closed or opened for arrival at this date. A room closed for arrival
        cannot be sold if the guest arrives during the dates the restriction applies.
        &#x201C;Departure&#x201D; &#x2013; Closed or opened for departure. A room
        closed for departure cannot be sold if the guest departs during the dates
        the restriction applies. &#x201C;Master&#x201D; &#x2013; Fully closed or
        opened for sale. If a room is fully closed it cannot be sold if the guest
        stays at any of the dates the restriction applies. This is the default
        value.</td>
    </tr>
  </tbody>
</table>

## OTA\_HotelAvailNotifRS <a id="AvailabilityandRestrictions-OTA_HotelAvailNotifRS"></a>

The OTA\_HotelAvailNotifRS should be returned for any request pushed by SiteConnect. It must be returned in a SOAP envelope, however the SOAP Header can be empty. The EchoToken received in the request should be mirrored back in the response.

#### Success Response XML <a id="AvailabilityandRestrictions-SuccessResponseXML"></a>

```text
<OTA_HotelAvailNotifRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <Success/>
</OTA_HotelAvailNotifRS>
```

#### Error Response XML - For more information on error handling, please refer to our [Error Handling](../error-handling.md) page <a id="AvailabilityandRestrictions-ErrorResponseXML-Formoreinformationonerrorhandling,pleaserefertoourErrorHandlingpage"></a>

**Failure Response**

```text
<OTA_HotelAvailNotifRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2005-08-01T09:30:47+08:00" EchoToken="abc123">
  <Errors>
    <Error Type="6" Code="392">Cannot find hotelier with code ABC</Error>
  </Errors>
</OTA_HotelAvailNotifRS>
```

### **Ref** OTA\_HotelAvailNotifRS

| Element |  | Description / Format |
| :--- | :--- | :--- |
| OTA\_HotelAvailNotifRS |  |  |
|   @EchoToken | 1 |  |
|   @Version | 1 |  |
|   @TimeStamp | 1 |  |
|   Success | 0..1 |  |
|   Errors | 0..1 | See [Errors](../error-handling.md#errors). |

