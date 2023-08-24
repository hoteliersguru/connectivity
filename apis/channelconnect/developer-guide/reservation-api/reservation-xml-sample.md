# Reservation XML Sample

OTA\_HotelResNotifRQ message sample for a reservation.

## Reservation

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
    <POS>
        <Source>
            <RequestorID Type="22" ID="BA1"/>
            <BookingChannel Primary="true">
                <CompanyName Code="GD">My GDS</CompanyName>
            </BookingChannel>
        </Source>
        <Source>
            <BookingChannel>
                <CompanyName Code="LC">Lodging</CompanyName>
            </BookingChannel>
        </Source>
    </POS>
    <HotelReservations>
        <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
            <UniqueID Type="14" ID="3741"/>
            <RoomStays>
                <RoomStay PromotionCode="breakkie">
                    <RoomTypes>
                        <RoomType RoomTypeCode="ROOM1">
                            <RoomDescription Name="Standard Room">Standard Room with double bed and single bed</RoomDescription>
                        </RoomType>
                    </RoomTypes>
                    <RatePlans>
                        <RatePlan RatePlanCode="RATE1">
                            <RatePlanDescription>Breakfast rate</RatePlanDescription>
                            <Commission>
                                <CommissionPayableAmount Amount="151.65" CurrencyCode="THB"/>
                            </Commission>
                             
                        </RatePlan>
                    </RatePlans>
                    <RoomRates>
                        <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
                            <Rates>
                                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-14">
                                    <Base AmountBeforeTax="563.63" AmountAfterTax="619.99" CurrencyCode="THB">
                                        <Taxes>
                                            <Tax Amount="56.36" CurrencyCode="THB"/>
                                        </Taxes>
                                    </Base>
                                    <Total AmountBeforeTax="568.63" AmountAfterTax="625.49" CurrencyCode="THB">
                                        <Taxes>
                                            <Tax Amount="56.86" CurrencyCode="THB"/>
                                        </Taxes>
                                    </Total>
                                </Rate>
                            </Rates>
                        <ServiceRPHs>
                            <ServiceRPH RPH="1"/>
                        </ServiceRPHs>
                        </RoomRate>
                    </RoomRates>
                    <GuestCounts>
                        <GuestCount AgeQualifyingCode="10" Count="2"/>
                        <GuestCount AgeQualifyingCode="8" Age="7" Count="1"/>
                        <GuestCount AgeQualifyingCode="8" Age="10" Count="1"/>
                        <GuestCount AgeQualifyingCode="7" Count="1"/>
                    </GuestCounts>
                    <TimeSpan Start="2012-03-12" End="2012-03-14"/>
                    <Total AmountBeforeTax="573.63" AmountAfterTax="630.99" CurrencyCode="THB">
                        <Taxes>
                            <Tax Amount="57.36" CurrencyCode="THB"/>
                        </Taxes>
                    </Total>
                    <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel"/>
                    <ServiceRPHs>
                        <ServiceRPH RPH="2"/>
                    </ServiceRPHs>                   
                    <ResGuestRPHs>
                        <ResGuestRPH RPH="1"/>
                    </ResGuestRPHs>
                    <Comments>
                        <Comment>
                            <Text>Will be Travelling with my friend so connected rooms please.</Text>
                        </Comment>
                    </Comments>
                    <SpecialRequests>
                        <SpecialRequest Name="extra bed">
                            <Text>Yes</Text>
                        </SpecialRequest>
                        <SpecialRequest Name="bedding configuration">
                            <Text>2 x Double</Text>
                        </SpecialRequest>
                    </SpecialRequests>
                </RoomStay>
            </RoomStays>
            <Services>
                <Service Inclusive="true" ServiceInventoryCode="EXTRA" Quantity='1'>
                    <Price>
                        <Total AmountAfterTax="33.00" CurrencyCode="THB"/>
                        <RateDescription>
                            <Text>Name: Car Park, Description: Undercover Parking (Clearance 2.2 meter or 7.2 feet), Category: Per Room Per Night</Text>
                        </RateDescription>
                    </Price>
                </Service>
                <Service Inclusive="true" ServiceInventoryCode="OTHER" ServiceRPH="1">
                    <Price>
                        <Total AmountAfterTax="5.00" CurrencyCode="THB"/>
                        <RateDescription>
                            <Text>Rate Drop Protection Guarantee</Text>
                        </RateDescription>
                    </Price>
                </Service>
                <Service Inclusive="true" ServiceInventoryCode="OTHER" ServiceRPH="2">
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
                                        <CountryName>Thailand</CountryName>
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
                <Total CurrencyCode="THB" AmountBeforeTax="606.63" AmountAfterTax="667.29">
                    <Taxes>
                        <Tax Amount="60.66" CurrencyCode="THB"/>
                    </Taxes>
                </Total>
                <!-- Either Guarantee or DepositPayments would be present if payments have been accepted against the reservation. -->
                <Guarantee>
                    <GuaranteesAccepted>
                        <GuaranteeAccepted>
                            <PaymentCard CardNumber="4321432143214327" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                                <CardHolderName>John Smith</CardHolderName>
                                <ThreeDomainSecurity>
                                    <Results>
                                        <threeDSVersion>1.0.2</threeDSVersion>
                                        <xid>z9UKb06xLziZMOXBEmWSVA1kwG0=</xid>
                                        <cavv>MTIzNDU2Nzg5MDEyMzQ1Njc4OTA=</cavv>
                                        <eci>05</eci>
                                    </Results>
                                </ThreeDomainSecurity>
                                <TPA_Extensions>
                                    <VirtualCreditCard isVCC="true" VCCActivationDate="2020-08-23" VCCDeactivationDate="2020-09-19" VCCCurrentBalance="100.00" VCCCurrencyCode="THB"/>
                                </TPA_Extensions>
                            </PaymentCard>
                        </GuaranteeAccepted>
                    </GuaranteesAccepted>
                </Guarantee>
                <DepositPayments>
                    <GuaranteePayment>
                        <AcceptedPayments>
                            <AcceptedPayment>
                                <PaymentCard CardNumber="4321432143214327" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                                    <CardHolderName>John Smith</CardHolderName>
                                    <ThreeDomainSecurity>
                                        <Results>
                                            <threeDSVersion>1.0.2</threeDSVersion>
                                            <xid>z9UKb06xLziZMOXBEmWSVA1kwG0=</xid>
                                            <cavv>MTIzNDU2Nzg5MDEyMzQ1Njc4OTA=</cavv>
                                            <eci>05</eci>
                                        </Results>
                                    </ThreeDomainSecurity>
                                    <TPA_Extensions>
                                        <VirtualCreditCard isVCC="true" VCCActivationDate="2020-08-23" VCCDeactivationDate="2020-09-19" VCCCurrentBalance="100.00" VCCCurrencyCode="THB"/>
                                    </TPA_Extensions>
                                </PaymentCard>
                            </AcceptedPayment>
                        </AcceptedPayments>
                        <AmountPercent Amount="100.00" CurrencyCode="THB"/>
                    </GuaranteePayment>
                </DepositPayments>
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
                    <ProfileInfo>
                        <Profile ProfileType="3">
                            <CompanyInfo>
                                <CompanyName>COMPANY</CompanyName>
                                <AddressInfo>
                                    <AddressLine>6 George St</AddressLine>
                                    <AddressLine/>
                                    <CityName>Bangkok</CityName>
                                    <PostalCode>2001</PostalCode>
                                    <StateProv>BKK</StateProv>
                                    <CountryName>Thailand</CountryName>
                                </AddressInfo>
                                <TelephoneInfo PhoneNumber="0266564101"/>
                                <Email>company@gmail.com</Email>
                            </CompanyInfo>
                        </Profile>
                    </ProfileInfo>
                    <ProfileInfo>
                        <UniqueID ID="123456"/>
                        <Profile ProfileType="4">
                            <CompanyInfo>
                                <CompanyName>TRAVEL AGENT LTD</CompanyName>
                                <AddressInfo>
                                    <AddressLine>5 George St</AddressLine>
                                    <AddressLine>CBD</AddressLine>
                                    <CityName>Bangkok</CityName>
                                    <PostalCode>2000</PostalCode>
                                    <StateProv>BKK</StateProv>
                                    <CountryName>Thailand</CountryName>
                                </AddressInfo>
                                <TelephoneInfo PhoneNumber="0266564100"/>
                                <Email>ota@gmail.com</Email>
                            </CompanyInfo>
                        </Profile>
                    </ProfileInfo>
                </Profiles>
            </ResGlobalInfo>
        </HotelReservation>
    </HotelReservations>
</OTA_HotelResNotifRQ>
```

