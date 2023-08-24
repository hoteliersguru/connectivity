# Retrieve Rooms API

## Retrieve Room and Rate Codes <a href="#title-text" id="title-text"></a>

The partner will send a OTA\_HotelAvailRQ to retrieve a list of available rooms and rates. The Channel Manager should return a list of RoomStays with all active room and rate combinations for the hotel.

### The Request

```
<OTA_HotelAvailRQ
	xmlns="http://www.opentravel.org/OTA/2003/05" 
	Version="1.0" 
	TimeStamp="2022-04-08T14:22:30+07:00" 
	EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
	<AvailRequestSegments>
		<AvailRequestSegment>
			<HotelSearchCriteria>
				<Criterion>
					<HotelRef HotelCode="004956"/>
				</Criterion>
			</HotelSearchCriteria>
		</AvailRequestSegment>
	</AvailRequestSegments>
</OTA_HotelAvailRQ>
```

### Elements & Attributes&#x20;

The OTA\_HotelAvailRQ message has the following elements and attributes:

| Element / @Attribute                                                                                                     | Occurrences | Description                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------ | ----------- | -------------------------------------------------------------------------------------------------------------------- |
| OTA\_HotelAvailRQ                                                                                                        | 1           | The root element for the message.                                                                                    |
| OTA\_HotelAvailRQ / @xmlns                                                                                               | 1           | The XML namespace.                                                                                                   |
| OTA\_HotelAvailRQ / @EchoToken                                                                                           | 1           | Unique identifier for this request.                                                                                  |
| OTA\_HotelAvailRQ / @Version                                                                                             | 1           | Current version is 1.0                                                                                               |
| OTA\_HotelAvailRQ / @TimeStamp                                                                                           | 1           | Time of the transaction in ISO 8601 format.                                                                          |
| OTA\_HotelAvailRQ / AvailRequestSegments / AvailRequestSegment                                                           | 1..n        | A request will contain only one single AvailRequestSegment requesting room and rates for one single hotel at a time. |
| OTA\_HotelAvailRQ / AvailRequestSegments / AvailRequestSegment / HotelSearchCriteria / Criterion / HotelRef / @HotelCode | 1           | The code of the hotel queried.                                                                                       |

### Successful Response

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelAvailRS
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0"
	TimeStamp="2022-04-08T14:30:17+07:00"
	EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
	<Success />
	<RoomStays>
		<RoomStay>
			<RoomTypes>
				<RoomType RoomTypeCode="PdncX">
					<RoomDescription Name="Superior IBE">
						<Text>Superior Test</Text>
					</RoomDescription>
				</RoomType>
			</RoomTypes>
			<RatePlans>
				<RatePlan RatePlanCode="MNOPQ">
					<RatePlanDescription Name="Room Only" />
				</RatePlan>
			</RatePlans>
		</RoomStay>
		<RoomStay>
			<RoomTypes>
				<RoomType RoomTypeCode="PdncX">
					<RoomDescription Name="Superior IBE">
						<Text>Superior Test</Text>
					</RoomDescription>
				</RoomType>
			</RoomTypes>
			<RatePlans>
				<RatePlan RatePlanCode="CUJBT">
					<RatePlanDescription Name="Breakfast" />
				</RatePlan>
			</RatePlans>
		</RoomStay>
		<RoomStay>
			<RoomTypes>
				<RoomType RoomTypeCode="aQIPW">
					<RoomDescription Name="Deluxe IBE" />
				</RoomType>
			</RoomTypes>
			<RatePlans>
				<RatePlan RatePlanCode="MNOPQ">
					<RatePlanDescription Name="Room Only" />
				</RatePlan>
			</RatePlans>
		</RoomStay>
		<RoomStay>
			<RoomTypes>
				<RoomType RoomTypeCode="aQIPW">
					<RoomDescription Name="Deluxe IBE" />
				</RoomType>
			</RoomTypes>
			<RatePlans>
				<RatePlan RatePlanCode="CUJBT">
					<RatePlanDescription Name="Breakfast" />
				</RatePlan>
			</RatePlans>
		</RoomStay>
		<RoomStay>
			<RoomTypes>
				<RoomType RoomTypeCode="YSMeW">
					<RoomDescription Name="Suite IBE" />
				</RoomType>
			</RoomTypes>
			<RatePlans>
				<RatePlan RatePlanCode="MNOPQ">
					<RatePlanDescription Name="Room Only" />
				</RatePlan>
			</RatePlans>
		</RoomStay>
		<RoomStay>
			<RoomTypes>
				<RoomType RoomTypeCode="YSMeW">
					<RoomDescription Name="Suite IBE" />
				</RoomType>
			</RoomTypes>
			<RatePlans>
				<RatePlan RatePlanCode="CUJBT">
					<RatePlanDescription Name="Breakfast" />
				</RatePlan>
			</RatePlans>
		</RoomStay>
	</RoomStays>
</OTA_HotelAvailRS>
```

### Failure Response

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelAvailRS
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0"
	TimeStamp="2022-04-08T14:34:25+07:00"
	EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
	<Errors>
		<Error Type="6" Code="392">Hotel Identifier ABC Not Found.</Error>
	</Errors>
</OTA_HotelAvailRS>
```

### Elements & Attributes

The OTA\_HotelAvailRS message has the following elements and attributes:

| Element / @Attribute                                                                                        | Occurrences | Description                                            |
| ----------------------------------------------------------------------------------------------------------- | ----------- | ------------------------------------------------------ |
| OTA\_HotelAvailRS                                                                                           | 1           | The root element for the message.                      |
| OTA\_HotelAvailRS / @xmlns                                                                                  | 1           | The XML namespace.                                     |
| OTA\_HotelAvailRS / @EchoToken                                                                              | 1           | Unique identifier for this request.                    |
| OTA\_HotelAvailRS / @Version                                                                                | 1           | Current version is 1.0                                 |
| OTA\_HotelAvailRS / @TimeStamp                                                                              | 1           | Time of the transaction in ISO 8601 format.            |
| OTA\_HotelAvailRS / Success                                                                                 | 0..1        | The success element marking the request as successful. |
| OTA\_HotelAvailRS / Errors                                                                                  | 0..1        | See Errors.                                            |
| OTA\_HotelAvailRS / RoomStays                                                                               | 0..n        |                                                        |
| OTA\_HotelAvailRS / RoomStays / RoomStay                                                                    | 1           |                                                        |
| OTA\_HotelAvailRS / RoomStays / RoomTypes                                                                   | 1           |                                                        |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType                                                        | 1           |                                                        |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType / @RoomTypeCode                                        | 1           | The code for the room.                                 |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType / RoomDescription                                      | 1           |                                                        |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType / RoomDescription / @Name                              | 1           | The name of the room.                                  |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType / RoomDescription / Text                               | 0..1        | Description of the room.                               |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType / TPA\_Extensions                                      | 0..1        |                                                        |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType / TPA\_Extensions / RoomRestriction                    | 0..1        |                                                        |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType / TPA\_Extensions / RoomRestriction / AllowExtraBed    | 0..1        | 0 = No Extrabed Allowed. 1 = Allowed                   |
| OTA\_HotelAvailRS / RoomStays / RoomTypes / RoomType / TPA\_Extensions / RoomRestriction / AllowExtraPerson | 0..1        | 0 = No Extra Person Allowed, 1 = Allowed               |
| RatePlans                                                                                                   | 1..n        |                                                        |
| RatePlans / RatePlan                                                                                        | 1           |                                                        |
| RatePlans / RatePlan / @RatePlanCode                                                                        | 1           | The code for the rate plan.                            |
| RatePlans / RatePlan / RatePlanDescription                                                                  | 1           |                                                        |
| RatePlans / RatePlan / RatePlanDescription / @Name                                                          | 1           | The name of the rate plan.                             |
| RatePlans / RatePlan / RatePlanDescription / Text                                                           | 0..n        | Description of the rate plan.                          |
