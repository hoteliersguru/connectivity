# Services XML Samples

The Service structure is used for passing on information about charges for extras and services. Services can be provided at the HotelReservation level \(no ServiceRPH\) or on a RoomStay or RoomRate level. The ServiceRPH serves only to link a charge to a room or a rate.

All Service totals provided should be considered full amounts added to the base reservation charge. In other words, the charges are not per person or per day but full charges. The total amounts provided for the RoomRate, RoomStay and Reservation should be considered as inclusive of extras, depending on where the service charge is applied.

#### Reservation Services <a id="ServicesXMLSample-ReservationServices"></a>

Example of a reservation with a service linked to the Reservation \(No ServiceRPH link\).  
Service cost is included in the ResGlobalInfo Total.  
Service cost is not included in the RoomRate Base, RoomRate Total and RoomStay Total.

**Reservation**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
    <POS>
        <Source>
            <RequestorID Type="22" ID="BA1"/>
            <BookingChannel Primary="true">
                <CompanyName Code="GD">My GDS</CompanyName>
            </BookingChannel>
        </Source>
    </POS>
    <HotelReservations>
        <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
            <UniqueID Type="14" ID="3741"/>
            <RoomStays>
                <RoomStay>
                    <RoomTypes>
                        <RoomType RoomTypeCode="ROOM1">
                            <RoomDescription Name="Standard Room">Standard Room with double bed and single bed</RoomDescription>
                        </RoomType>
                    </RoomTypes>
                    <RatePlans>
                        <RatePlan RatePlanCode="RATE1">
                            <RatePlanDescription>Breakfast rate</RatePlanDescription>
                        </RatePlan>
                    </RatePlans>
                    <RoomRates>
                        <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
                            <Rates>
                                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-14">
                                    <Total AmountBeforeTax="454.55" AmountAfterTax="500.00" CurrencyCode="THB"/>
                                </Rate>
                            </Rates>
                        </RoomRate>
                    </RoomRates>
                    <GuestCounts>
                        <GuestCount AgeQualifyingCode="10" Count="2"/>
                    </GuestCounts>
                    <TimeSpan Start="2012-03-12" End="2012-03-14"/>
                    <Total AmountAfterTax="500.00" CurrencyCode="THB">
                    </Total>
                    <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel"/>
                    <ResGuestRPHs>
                        <ResGuestRPH RPH="1"/>
                    </ResGuestRPHs>
                </RoomStay>
            </RoomStays>
            <Services>
                <Service Inclusive="true" ServiceInventoryCode="EXTRA" Quantity="1">
                    <Price>
                        <Total AmountAfterTax="33.00" CurrencyCode="THB"/>
                        <RateDescription>
                            <Text>Name: Car Park, Description: Undercover Parking (Clearance 2.2 meter or 7.2 feet), Category: Per Room Per Night</Text>
                        </RateDescription>
                    </Price>
                </Service>
            </Services>
            <ResGuests>
                <ResGuest ResGuestRPH="1" ArrivalTime="14:00:00" PrimaryIndicator="1">
                    <Profiles>
                        <ProfileInfo>
                            <Profile ProfileType="1">
                                <Customer>
                                    <PersonName>
                                        <NamePrefix>Mr</NamePrefix>
                                        <GivenName>John</GivenName>
                                        <Surname>Smith</Surname>
                                    </PersonName>
                                    <Telephone PhoneNumber="0266564100"/>
                                    <Email>test@gmail.com</Email>
                                    <Address>
                                        <AddressLine>George St</AddressLine>
                                        <AddressLine>CBD</AddressLine>
                                        <CityName>Bangkok</CityName>
                                        <PostalCode>2000</PostalCode>
                                        <StateProv>BKK</StateProv>
                                        <CountryName Code="AU">Thailand</CountryName>
                                    </Address>
                                </Customer>
                            </Profile>
                        </ProfileInfo>
                    </Profiles>
                </ResGuest>
            </ResGuests>
            <ResGlobalInfo>
                <HotelReservationIDs>
                    <HotelReservationID ResID_Type="14" ResID_Value="3741"/>
                </HotelReservationIDs>
                <Total CurrencyCode="THB" AmountAfterTax="533.00">
                </Total>
                <Guarantee>
                    <GuaranteesAccepted>
                        <GuaranteeAccepted>
                            <PaymentCard CardNumber="4321432143214327" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                                <CardHolderName>John Smith</CardHolderName>
                            </PaymentCard>
                        </GuaranteeAccepted>
                    </GuaranteesAccepted>
                </Guarantee>
                <Profiles>
                    <ProfileInfo>
                        <Profile ProfileType="1">
                            <Customer>
                                <PersonName>
                                    <NamePrefix>Mr</NamePrefix>
                                    <GivenName>John</GivenName>
                                    <Surname>Smith</Surname>
                                </PersonName>
                                <Telephone PhoneNumber="0266564100"/>
                                <Email>test@gmail.com</Email>
                                <Address>
                                    <AddressLine>George St</AddressLine>
                                    <AddressLine>CBD</AddressLine>
                                    <CityName>Bangkok</CityName>
                                    <PostalCode>2000</PostalCode>
                                    <StateProv>BKK</StateProv>
                                    <CountryName>Thailand</CountryName>
                                </Address>
                            </Customer>
                        </Profile>
                    </ProfileInfo>
                </Profiles>
            </ResGlobalInfo>
        </HotelReservation>
    </HotelReservations>
</OTA_HotelResNotifRQ>
```

#### RoomStay Services <a id="ServicesXMLSample-RoomStayServices"></a>

Example of a reservation with a service linked to the RoomStay.  
Service cost is included in the RoomStay Total and ResGlobalInfo Total.  
Service cost is not included in the RoomRate Base and RoomRate Total.

**Reservation**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
    <POS>
        <Source>
            <RequestorID Type="22" ID="BA1"/>
            <BookingChannel Primary="true">
                <CompanyName Code="GD">My GDS</CompanyName>
            </BookingChannel>
        </Source>
    </POS>
    <HotelReservations>
        <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
            <UniqueID Type="14" ID="3741"/>
            <RoomStays>
                <RoomStay>
                    <RoomTypes>
                        <RoomType RoomTypeCode="ROOM1">
                            <RoomDescription Name="Standard Room">Standard Room with double bed and single bed</RoomDescription>
                        </RoomType>
                    </RoomTypes>
                    <RatePlans>
                        <RatePlan RatePlanCode="RATE1">
                            <RatePlanDescription>Breakfast rate</RatePlanDescription>
                        </RatePlan>
                    </RatePlans>
                    <RoomRates>
                        <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
                            <Rates>
                                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-14">
                                    <Base AmountBeforeTax="454.55" AmountAfterTax="500.00" CurrencyCode="THB"/>
                                    <Total AmountBeforeTax="454.55" AmountAfterTax="500.00" CurrencyCode="THB"/>
                                </Rate>
                            </Rates>
                        </RoomRate>
                    </RoomRates>
                    <GuestCounts>
                        <GuestCount AgeQualifyingCode="10" Count="2"/>
                    </GuestCounts>
                    <TimeSpan Start="2012-03-12" End="2012-03-14"/>
                    <Total AmountAfterTax="505.00" CurrencyCode="THB">
                    </Total>
                    <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel"/>
                    <ServiceRPHs>
                        <ServiceRPH RPH="1"/>
                    </ServiceRPHs>
                    <ResGuestRPHs>
                        <ResGuestRPH RPH="1"/>
                    </ResGuestRPHs>
                </RoomStay>
            </RoomStays>
            <Services>
                <Service Inclusive="true" ServiceInventoryCode="OTHER" Quantity="2" ServiceRPH="1">
                    <Price>
                        <Total AmountAfterTax="5.00" CurrencyCode="THB"/>
                        <RateDescription>
                            <Text>Extra Bathrobe</Text>
                        </RateDescription>
                    </Price>
                </Service>
            </Services>
            <ResGuests>
                <ResGuest ResGuestRPH="1" ArrivalTime="14:00:00" PrimaryIndicator="1">
                    <Profiles>
                        <ProfileInfo>
                            <Profile ProfileType="1">
                                <Customer>
                                    <PersonName>
                                        <NamePrefix>Mr</NamePrefix>
                                        <GivenName>John</GivenName>
                                        <Surname>Smith</Surname>
                                    </PersonName>
                                    <Telephone PhoneNumber="0266564100"/>
                                    <Email>test@gmail.com</Email>
                                    <Address>
                                        <AddressLine>George St</AddressLine>
                                        <AddressLine>CBD</AddressLine>
                                        <CityName>Bangkok</CityName>
                                        <PostalCode>2000</PostalCode>
                                        <StateProv>BKK</StateProv>
                                        <CountryName Code="AU">Thailand</CountryName>
                                    </Address>
                                </Customer>
                            </Profile>
                        </ProfileInfo>
                    </Profiles>
                </ResGuest>
            </ResGuests>
            <ResGlobalInfo>
                <HotelReservationIDs>
                    <HotelReservationID ResID_Type="14" ResID_Value="3741"/>
                </HotelReservationIDs>
                <Total CurrencyCode="THB" AmountAfterTax="505.00">
                </Total>
                <Guarantee>
                    <GuaranteesAccepted>
                        <GuaranteeAccepted>
                            <PaymentCard CardNumber="4010401040104010" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                                <CardHolderName>John Smith</CardHolderName>
                            </PaymentCard>
                        </GuaranteeAccepted>
                    </GuaranteesAccepted>
                </Guarantee>
                <Profiles>
                    <ProfileInfo>
                        <Profile ProfileType="1">
                            <Customer>
                                <PersonName>
                                    <NamePrefix>Mr</NamePrefix>
                                    <GivenName>John</GivenName>
                                    <Surname>Smith</Surname>
                                </PersonName>
                                <Telephone PhoneNumber="0266564100"/>
                                <Email>test@gmail.com</Email>
                                <Address>
                                    <AddressLine>George St</AddressLine>
                                    <AddressLine>CBD</AddressLine>
                                    <CityName>Bangkok</CityName>
                                    <PostalCode>2000</PostalCode>
                                    <StateProv>BKK</StateProv>
                                    <CountryName>Thailand</CountryName>
                                </Address>
                            </Customer>
                        </Profile>
                    </ProfileInfo>
                </Profiles>
            </ResGlobalInfo>
        </HotelReservation>
    </HotelReservations>
</OTA_HotelResNotifRQ>
```

#### RoomRate Services <a id="ServicesXMLSample-RoomRateServices"></a>

Example of a reservation with a service linked to the RoomRate.  
Service cost is included in the RoomRate Total, RoomStay Total and ResGlobalInfo Total.  
Service cost is not included in the RoomRate Base

**Reservation**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
    <POS>
        <Source>
            <RequestorID Type="22" ID="BA1"/>
            <BookingChannel Primary="true">
                <CompanyName Code="GD">My GDS</CompanyName>
            </BookingChannel>
        </Source>
    </POS>
    <HotelReservations>
        <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
            <UniqueID Type="14" ID="3741"/>
            <RoomStays>
                <RoomStay>
                    <RoomTypes>
                        <RoomType RoomTypeCode="ROOM1">
                            <RoomDescription Name="Standard Room">Standard Room with double bed and single bed</RoomDescription>
                        </RoomType>
                    </RoomTypes>
                    <RatePlans>
                        <RatePlan RatePlanCode="RATE1">
                            <RatePlanDescription>Breakfast rate</RatePlanDescription>
                        </RatePlan>
                    </RatePlans>
                    <RoomRates>
                        <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
                            <Rates>
                                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-14">
                                    <Base AmountBeforeTax="454.55" AmountAfterTax="500.00" CurrencyCode="THB"/>
                                    <Total AmountBeforeTax="459.09" AmountAfterTax="505.00" CurrencyCode="THB"/>
                                </Rate>
                            </Rates>
                            <ServiceRPHs>
                                <ServiceRPH RPH="1"/>
                            </ServiceRPHs>
                        </RoomRate>
                    </RoomRates>
                    <GuestCounts>
                        <GuestCount AgeQualifyingCode="10" Count="2"/>
                    </GuestCounts>
                    <TimeSpan Start="2012-03-12" End="2012-03-14"/>
                    <Total AmountAfterTax="505.00" CurrencyCode="THB">
                    </Total>
                    <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel"/>
                    <ResGuestRPHs>
                        <ResGuestRPH RPH="1"/>
                    </ResGuestRPHs>
                </RoomStay>
            </RoomStays>
            <Services>
                <Service Inclusive="true" ServiceInventoryCode="OTHER" ServiceRPH="1">
                    <Price>
                        <Total AmountAfterTax="5.00" CurrencyCode="THB"/>
                        <RateDescription>
                            <Text>Rate Drop Protection Guarantee</Text>
                        </RateDescription>
                    </Price>
                </Service>
            </Services>
            <ResGuests>
                <ResGuest ResGuestRPH="1" ArrivalTime="14:00:00" PrimaryIndicator="1">
                    <Profiles>
                        <ProfileInfo>
                            <Profile ProfileType="1">
                                <Customer>
                                    <PersonName>
                                        <NamePrefix>Mr</NamePrefix>
                                        <GivenName>John</GivenName>
                                        <Surname>Smith</Surname>
                                    </PersonName>
                                    <Telephone PhoneNumber="0266564100"/>
                                    <Email>test@gmail.com</Email>
                                    <Address>
                                        <AddressLine>George St</AddressLine>
                                        <AddressLine>CBD</AddressLine>
                                        <CityName>Bangkok</CityName>
                                        <PostalCode>2000</PostalCode>
                                        <StateProv>BKK</StateProv>
                                        <CountryName Code="AU">Thailand</CountryName>
                                    </Address>
                                </Customer>
                            </Profile>
                        </ProfileInfo>
                    </Profiles>
                </ResGuest>
            </ResGuests>
            <ResGlobalInfo>
                <HotelReservationIDs>
                    <HotelReservationID ResID_Type="14" ResID_Value="3741"/>
                </HotelReservationIDs>
                <Total CurrencyCode="THB" AmountAfterTax="505.00">
                </Total>
                <Guarantee>
                    <GuaranteesAccepted>
                        <GuaranteeAccepted>
                            <PaymentCard CardNumber="4010401040104010" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                                <CardHolderName>John Smith</CardHolderName>
                            </PaymentCard>
                        </GuaranteeAccepted>
                    </GuaranteesAccepted>
                </Guarantee>
                <Profiles>
                    <ProfileInfo>
                        <Profile ProfileType="1">
                            <Customer>
                                <PersonName>
                                    <NamePrefix>Mr</NamePrefix>
                                    <GivenName>John</GivenName>
                                    <Surname>Smith</Surname>
                                </PersonName>
                                <Telephone PhoneNumber="0266564100"/>
                                <Email>test@gmail.com</Email>
                                <Address>
                                    <AddressLine>George St</AddressLine>
                                    <AddressLine>CBD</AddressLine>
                                    <CityName>Bangkok</CityName>
                                    <PostalCode>2000</PostalCode>
                                    <StateProv>BKK</StateProv>
                                    <CountryName>Thailand</CountryName>
                                </Address>
                            </Customer>
                        </Profile>
                    </ProfileInfo>
                </Profiles>
            </ResGlobalInfo>
        </HotelReservation>
    </HotelReservations>
</OTA_HotelResNotifRQ>
```

