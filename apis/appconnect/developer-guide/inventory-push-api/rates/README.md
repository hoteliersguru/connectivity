# Rates

The partner will send through updates for rates using the **OTA\_HotelRateAmountNotifRQ**. The Channel Manager should process the updates and response with the **OTA\_HotelRateAmountNotifRS** as a receipt of success or failure.

### The Request

```
<OTA_HotelRateAmountNotifRQ
	xmlns="http://www.opentravel.org/OTA/2003/05"
	TimeStamp="2022-04-08T14:22:30+07:00" Version="1.0"
	EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
	<RateAmountMessages HotelCode="000001">
		<RateAmountMessage>
			<StatusApplicationControl
				InvTypeCode="PdncX" RatePlanCode="MNOPQ" Start="2022-04-08"
				End="2022-12-31" />
			<Rates>
				<Rate>
					<BaseByGuestAmts>
						<BaseByGuestAmt AgeQualifyingCode="10"
							AmountAfterTax="123.00" />
					</BaseByGuestAmts>
				</Rate>
			</Rates>
		</RateAmountMessage>
	</RateAmountMessages>
</OTA_HotelRateAmountNotifRQ>
```

### Elements & Attributes

The OTA\_HotelRateAmountNotifRQ message has the following elements and attributes:

| Element / @Attribute                                                                                                                                      | Occurrences | Description                                                                                                                                                                                                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| OTA\_HotelRateAmountNotifRQ                                                                                                                               | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / @xmlns                                                                                                                      | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / @EchoToken                                                                                                                  | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / @Version                                                                                                                    | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / @TimeStamp                                                                                                                  | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages                                                                                                          | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / @HotelCode                                                                                             | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage                                                                                      | 1..n        |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / @Start, @End                                                                       | 1           | The start and end dates for which the availability update is being sent in ISO 8601 format (without time). These dates are inclusive and use the hotel time-zone. If a time period is also specified in a Rate element it has precedence over this one. Either this or the Rate element time periods must be specified. |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / @InvTypeCode                                                                       | 1           | Identifies the room.                                                                                                                                                                                                                                                                                                    |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / @RatePlanCode                                                                      | 1           | Identifies the rate plan.                                                                                                                                                                                                                                                                                               |
| <p>OTA_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / @Mon, @Tue, @Weds,</p><p>        @Thur, @Fri, @Sat,</p><p>        @Sun</p>       | 0..1        | Used to communicate which days of the week the update applies to. If one is set, they must all be set. Valid values: “0” – Does not apply “1” – Applies.                                                                                                                                                                |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates                                                                              | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate                                                                       | 1..n        |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / BaseByGuestAmts                                                     | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / BaseByGuestAmts / BaseByGuestAmt                                    | 1           |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / BaseByGuestAmts / BaseByGuestAmt / @AmountAfterTax                  | 1           | The amount after tax for this base rate.                                                                                                                                                                                                                                                                                |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / AdditionalGuestAmounts                                              | 0..1        |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / AdditionalGuestAmounts / AdditionalGuestAmount                      | 1..2        | The rate for additional guests. This element is only valid if BaseByGuestAmt elements are present.                                                                                                                                                                                                                      |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / AdditionalGuestAmounts / AdditionalGuestAmount / @Amount            | 1           | The amount for an additional guest.                                                                                                                                                                                                                                                                                     |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / AdditionalGuestAmounts / AdditionalGuestAmount / @AgeQualifyingCode | 1           | The age group of the additional guest. Valid values: 10 – Additional Adult. 8 – Additional Child.                                                                                                                                                                                                                       |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / RateDescription                                                     | 0..1        |                                                                                                                                                                                                                                                                                                                         |
| OTA\_HotelRateAmountNotifRQ / RateAmountMessages / RateAmountMessage / Rates / Rate / RateDescription / Text                                              | 1           | Descriptive Text  goes with the rate also called Inclusions.                                                                                                                                                                                                                                                            |

### Successful Response

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelRateAmountNotifRS
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0"
	TimeStamp="2022-04-08T15:31:31+07:00"
	EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
	<Success />
</OTA_HotelRateAmountNotifRS>
```

### Failure Response

```
<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelRateAmountNotifRS
	xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0"
	TimeStamp="2022-04-08T14:34:25+07:00"
	EchoToken="c4ef4553-6575-440c-80c8-2be5a7092727">
	<Errors>
		<Error Type="6" Code="392">Hotel Identifier ABC Not Found.</Error>
	</Errors>
</OTA_HotelRateAmountNotifRS>
```

### Elements & Attributes

The OTA\_HotelRateAmountNotifRS message has the following elements and attributes:



| Element / @Attribute                           | Occurrences | Description |
| ---------------------------------------------- | ----------- | ----------- |
| OTA\_HotelRateAmountNotifRS                    | 1           |             |
| OTA\_HotelRateAmountNotifRS/@xmlns             | 1           |             |
| OTA\_HotelRateAmountNotifRS/@Version           | 1           |             |
| OTA\_HotelRateAmountNotifRS/@TimeStamp         | 1           |             |
| OTA\_HotelRateAmountNotifRS/@EchoToken         | 1           |             |
| OTA\_HotelRateAmountNotifRS/Success            | 0..1        |             |
| OTA\_HotelRateAmountNotifRS/Errors             | 0..1        |             |
| OTA\_HotelRateAmountNotifRS/Errors/Error       | 1           |             |
| OTA\_HotelRateAmountNotifRS/Errors/Error/@Type | 1           |             |
| OTA\_HotelRateAmountNotifRS/Errors/Error/@Code | 1           |             |
