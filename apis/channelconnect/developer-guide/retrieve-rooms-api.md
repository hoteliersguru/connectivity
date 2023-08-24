# Retrieve Rooms API

## Retrieve Room and Rate Codes <a href="#title-text" id="title-text"></a>

ChannelConnect will send a OTA\_HotelAvailRQ to retrieve a list of available rooms and rates. The connected channel should return a list of RoomStays with all active room and rate combinations for the hotel.

## OTA\_HotelAvailRQ

```
<OTA_HotelAvailRQ
    xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2020-09-10T16:20:32+0700" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" AvailRatesOnly="true">
    <AvailRequestSegments>
        <AvailRequestSegment>
            <HotelSearchCriteria>
                <Criterion>
                    <HotelRef HotelCode="0778" />
                </Criterion>
            </HotelSearchCriteria>
        </AvailRequestSegment>
    </AvailRequestSegments>
</OTA_HotelAvailRQ>
```

### Ref OTA\_HotelAvailRQ

| Element                                                              | Count | Description / Format                                                                                                                                                                                 |
| -------------------------------------------------------------------- | ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OTA\_HotelAvailRQ**                                                |       | The root element for the message.                                                                                                                                                                    |
| @EchoToken                                                           | 1     | Unique identifier for this request.                                                                                                                                                                  |
| @Version                                                             | 1     | Current version is 1.0                                                                                                                                                                               |
| @TimeStamp                                                           | 1     | Time of the transaction in ISO 8601 format.                                                                                                                                                          |
| AvailRatesOnly                                                       | 1     | Always set to "true".                                                                                                                                                                                |
| **OTA\_HotelAvailRQ / AvailRequestSegments / AvailRequestSegment**   | 1..n  | A request will contain only one single AvailRequestSegment requesting room and rates for one single hotel at a time.                                                                                 |
| **AvailRequestSegment / HotelSearchCriteria / Criterion / HotelRef** | 1     | The search criteria. The API only Hotel reference criteria, which returns results for a hotel based on the hotel code. If not specified all hotels managed through the channel manager are returned. |
| @HotelCode                                                           | 1     | The code of the hotel queried.                                                                                                                                                                       |

## OTA\_HotelAvailRS

{% hint style="info" %}
One room + rate combination per RoomStay.\
The RoomDescription@Name and RatePlanDescription@Name will be used to identify the room + rate combination.&#x20;

**Please ensure the 'Content Type' of your OTA\_HotelAvailRS is 'text/xml; charset=utf-8'**
{% endhint %}

### Successful Response

```
<OTA_HotelAvailRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2020-09-10T16:20:32+0700" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc">
  <Success/>
  <HotelStays>
    <HotelStay>
      <BasicPropertyInfo HotelCode="123456" HotelName="My Hotel and SPA" CurrencyCode="THB"/>
    </HotelStay>
  </HotelStays>
  <RoomStays>
    <RoomStay>
      <RoomTypes>
        <RoomType RoomTypeCode="SGL">
          <RoomDescription Name="Single Room">
            <Text>Bedding is Queen sized bed. Continental breakfast for each guest.</Text>
          </RoomDescription>
        </RoomType>
      </RoomTypes>
      <RatePlans>
        <RatePlan RatePlanCode="BAR">
          <RatePlanDescription Name="Best Available Rate">
            <Text>Best available rate including breakfast.</Text>
          </RatePlanDescription>
        </RatePlan>
      </RatePlans>
    </RoomStay>
    <RoomStay>
      <RoomTypes>
        <RoomType RoomTypeCode="SGL">
          <RoomDescription Name="Single Room">
            <Text>Bedding is Queen sized bed. Continental breakfast for each guest.</Text>
          </RoomDescription>
        </RoomType>
      </RoomTypes>
      <RatePlans>
        <RatePlan RatePlanCode="LTS">
          <RatePlanDescription Name="Long Term Stay">
            <Text>Special offer for 3 nights stay, pay only for 2!  Rates include breakfast.</Text>
          </RatePlanDescription>
        </RatePlan>
      </RatePlans>
    </RoomStay>
    <RoomStay>
      <RoomTypes>
        <RoomType RoomTypeCode="DBX">
          <RoomDescription Name="Deluxe Double Room">
            <Text>Bedding is 1 x King sized bed and 1 x Single bed. Continental breakfast for each guest.</Text>
          </RoomDescription>
        </RoomType>
      </RoomTypes>
      <RatePlans>
        <RatePlan RatePlanCode="BAR">
          <RatePlanDescription Name="Best Available Rate">
            <Text>Best available rate including breakfast.</Text>
          </RatePlanDescription>
          <AdditionalDetails>
             <AdditionalDetail Code="NO_RATES"/>
             <AdditionalDetail Code="NO_AVAILABILITY"/>
          </AdditionalDetails>          
        </RatePlan>
      </RatePlans>
    </RoomStay>
    <RoomStay>
      <RoomTypes>
        <RoomType RoomTypeCode="DBL">
          <RoomDescription Name="Standard Double Room">
            <Text>Bedding is 2 x Queen sized bed. Continental breakfast for each guest.</Text>
          </RoomDescription>
        </RoomType>
      </RoomTypes>
      <RatePlans>
        <RatePlan RatePlanCode="BAR">
          <RatePlanDescription Name="Best Available Rate">
            <Text>Best available rate including breakfast.</Text>
          </RatePlanDescription>
          <AdditionalDetails>
            <AdditionalDetail Code="NO_UPDATES"/>
          </AdditionalDetails>          
        </RatePlan>
      </RatePlans>
    </RoomStay>
  </RoomStays>
</OTA_HotelAvailRS>
```

### Failure Response

```
<OTA_HotelAvailRS xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2020-09-10T16:20:32+0700" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc">
  <Errors>
    <Error Type="6" Code="392">Cannot find hotelier with code ABC</Error>
  </Errors>
</OTA_HotelAvailRS>
```

### Ref OTA\_HotelAvailRS

| Element                           |      | Description / Format                                   |
| --------------------------------- | ---- | ------------------------------------------------------ |
| **OTA\_HotelAvailRS**             |      | Root element of the message.                           |
| @EchoToken                        | 1    | Unique identifier for this request.                    |
| @Version                          | 1    | Current version is 1.0.                                |
| @TimeStamp                        | 1    | Time of the transaction in ISO 8601 format.            |
| **OTA\_HotelAvailRS / Success**   | 0..1 | The success element marking the request as successful. |
| **OTA\_HotelAvailRS / Errors**    | 0..1 | See [Errors](error-handling.md#errors).                |
| **OTA\_HotelAvailRS / RoomStays** | 0..1 | See [RoomStays](retrieve-rooms-api.md#ref-roomstays).  |

### Ref RoomStays

| Element                                        |      | Description / Format                                    |
| ---------------------------------------------- | ---- | ------------------------------------------------------- |
| **HotelStays / HotelStay**                     | 0..n |                                                         |
| **HotelStays / HotelStay / BasicPropertyInfo** | 0..1 | Information about the hotel described in this RoomStay. |
| @HotelCode                                     | 1    | The code for the hotel.                                 |
| @HotelName                                     | 0..1 | The name of the hotel.                                  |
| @CurrencyCode                                  | 0..1 | The currency used by this hotel.                        |
| **RoomStays / RoomStay**                       | 1..n |                                                         |
| **RoomStays / RoomStay / RoomTypes**           | 1    | See [RoomTypes](retrieve-rooms-api.md#ref-roomtypes).   |
| **RoomStays / RoomStay / RatePlans**           | 1    | See [RatePlans](retrieve-rooms-api.md#ref-rateplans).   |

### Ref RoomTypes

| Element                                    |      | Description / Format                                                                                                   |
| ------------------------------------------ | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| **RoomTypes / RoomType**                   | 1    |                                                                                                                        |
| @RoomTypeCode                              | 1    | The code for the room.                                                                                                 |
| **RoomTypes / RoomType / RoomDescription** | 0..1 |                                                                                                                        |
| @Name                                      | 0..1 | The name of the room.                                                                                                  |
| Text                                       | 0..1 | Description of the room.                                                                                               |
| **RoomTypes / RoomType / Occupancy**       | 0..2 | The occupancy for the room. Up to two elements of this type may appear one for adults and optional children occupancy. |
| @MaxOccupancy                              | 1    | The maximum number of guest of this age range.                                                                         |
| @AgeQualifyingCode                         | 1    | The age qualifying code. Valid values: 10 – Adult 8 – Child.                                                           |

### Ref RatePlans

| Element                                                         |      | Description / Format                                                                                                                   |
| --------------------------------------------------------------- | ---- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **RatePlans / RatePlan**                                        | 1..n |                                                                                                                                        |
| @RatePlanCode                                                   | 1    | The code for the rate plan.                                                                                                            |
| **RatePlans / RatePlan / RatePlanDescription**                  | 0..1 |                                                                                                                                        |
| @Name                                                           | 1    | The name of the rate plan.                                                                                                             |
| Text                                                            | 0..1 | Description of the rate plan.                                                                                                          |
| **RatePlans / RatePlan / AdditionalDetails**                    | 0..1 | A collection of **AdditionalDetail**. Should only be included if there are additionalDetails that are to be included in the rate plan. |
| **RatePlans / RatePlan / AdditionalDetails / AdditionalDetail** | 1..n | Mandatory if **AdditionalDetails** is used.                                                                                            |
| @Code                                                           | 1    | <p>To limit updates use the following codes:</p><ul><li>NO_RATES</li><li>NO_AVAILABILITY</li><li>NO_UPDATES</li></ul>                  |

### Restrict Availability and or Rate Updates

{% hint style="info" %}
The connected channel can return a list of RoomStays with additional details for each room and rate plan combination. These additional functionality flags will disable their respective update types being sent from ChannelConnect to the connected channel.

These flags are only available for **OTA\_HotelAvailRS** messages that make use of our **@RatePlans** node. All additional nodes are optional.
{% endhint %}

```
<RoomStays>
  <RoomStay>
    <RoomTypes>
      <RoomType RoomTypeCode="SGL">
        <RoomDescription Name="Single Room">
          <Text>Bedding is Queen sized bed. Continental breakfast for each guest.</Text>
        </RoomDescription>
      </RoomType>
    </RoomTypes>
    <RatePlans>
      <RatePlan RatePlanCode="LTS">
        <RatePlanDescription Name="Long Term Stay">
          <Text>Special offer for 3 nights stay, pay only for 2!  Rates include breakfast.</Text>
        </RatePlanDescription>
        <AdditionalDetails>
             <AdditionalDetail Code="NO_RATES"/>
             <AdditionalDetail Code="NO_AVAILABILITY"/>
        </AdditionalDetails>
      </RatePlan>
    </RatePlans>
  </RoomStay>
</RoomStays>
```

### Reservation Only Room Rates

{% hint style="info" %}
ChannelConnect allows for Room Rates to be mapped that are only for the purpose of reservation delivery into the Channel Manager. If you have this requirement, you can use RoomStay / RatePlan / AdditionalDetails to send the below. Sending the below will instruct the Channel Manager to not send ARI updates, and the mapping of the Room Rate in question, will exist purely to allow for reservation delivery.
{% endhint %}

```
<RoomStays>
    <RoomStay>
        <RoomTypes>
            <RoomType RoomTypeCode="SGL">
                <RoomDescription Name="Single Room">
                    <Text>Bedding is Queen sized bed. Continental breakfast for each guest.</Text>
                </RoomDescription>
            </RoomType>
        </RoomTypes>
        <RatePlans>
            <RatePlan RatePlanCode="LTS">
                <RatePlanDescription Name="Long Term Stay">
                    <Text>Special offer for 3 nights stay, pay only for 2!  Rates include breakfast.</Text>
                </RatePlanDescription>
                <AdditionalDetails>
                    <AdditionalDetail Code="NO_UPDATES"/>
                </AdditionalDetails>
            </RatePlan>
        </RatePlans>
    </RoomStay>
</RoomStays>
```
