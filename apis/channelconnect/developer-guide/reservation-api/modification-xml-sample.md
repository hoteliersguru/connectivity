# Modification XML Sample

OTA\_HotelResNotifRQ message sample for a modification.

## Modification

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Modify" TimeStamp="2020-09-10T16:20:32+0700">
  <POS>
    <Source>
      <RequestorID Type="22" ID="BA1"/>
      <BookingChannel Primary="true">
        <CompanyName Code="GD">My GDS</CompanyName>
      </BookingChannel>
    </Source>
  </POS>
  <HotelReservations>
    <HotelReservation LastModifyDateTime="2012-03-09T21:31:52+02:00">
      <UniqueID Type="14" ID="3741"/>
      <RoomStays>
        <RoomStay PromotionCode="breakkie">
          <RoomTypes>
            <RoomType RoomTypeCode="ROOM2">
              <RoomDescription Name="Standard Room">Standard Room with double bed and single bed</RoomDescription>
            </RoomType>
          </RoomTypes>
          <RatePlans>
            <RatePlan RatePlanCode="RATE2">
              <RatePlanDescription>Breakfast rate</RatePlanDescription>
            </RatePlan>
          </RatePlans>
          <RoomRates>
            <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1">
              <Rates>
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-14">
                  <Base AmountBeforeTax="558.00" AmountAfterTax="620.00" CurrencyCode="AUD">
                    <Taxes>
                      <Tax Amount="62.00" CurrencyCode="AUD"/>
                    </Taxes>
                  </Base>
                  <Total AmountBeforeTax="558.00" AmountAfterTax="620.00" CurrencyCode="AUD">
                    <Taxes>
                      <Tax Amount="62.00" CurrencyCode="AUD"/>
                    </Taxes>
                  </Total>
                </Rate>
              </Rates>
            </RoomRate>
          </RoomRates>
          <GuestCounts>
            <GuestCount AgeQualifyingCode="10" Count="2"/>
            <GuestCount AgeQualifyingCode="8" Count="1"/>
            <GuestCount AgeQualifyingCode="7" Count="1"/>
          </GuestCounts>
          <TimeSpan Start="2012-03-12" End="2012-03-14"/>
          <Total AmountBeforeTax="558.00" AmountAfterTax="620.00" CurrencyCode="AUD">
            <Taxes>
              <Tax Amount="62.00" CurrencyCode="AUD"/>
            </Taxes>
          </Total>
          <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel" />
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
        <Total CurrencyCode="AUD" AmountBeforeTax="558.00" AmountAfterTax="620.00">
          <Taxes>
            <Tax Amount="62.00" CurrencyCode="AUD"/>
          </Taxes>
        </Total>
        <Guarantee>
          <GuaranteesAccepted>
            <GuaranteeAccepted>
              <PaymentCard CardNumber="4321432143214327" CardType="1" ExpireDate="0607" SeriesCode="123" CardCode="VI">
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
                  <VirtualCreditCard isVCC="true" VCCActivationDate="2020-08-23" VCCDeactivationDate="2020-09-19" VCCCurrentBalance="620.00" VCCCurrencyCode="AUD"/>
                </TPA_Extensions>
              </PaymentCard>
            </GuaranteeAccepted>
          </GuaranteesAccepted>
        </Guarantee>
        <Profiles>
          <ProfileInfo>
            <Profile>
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
                  <AddressLine></AddressLine>
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

