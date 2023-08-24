# Cancellation XML Sample

OTA\_HotelResNotifRQ message sample for a cancellation.

## **Cancellation**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Cancel" TimeStamp="2020-09-10T16:20:32+0700">
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
        <RoomStay>
          <RoomRates>
            <RoomRate RoomTypeCode="ROOM1" RatePlanCode="RATE1" NumberOfUnits="1"/>
          </RoomRates>
          <GuestCounts>
            <GuestCount AgeQualifyingCode="10" Count="2"/>
          </GuestCounts>
          <TimeSpan Start="2012-03-12" End="2012-03-13"/>
          <Total AmountAfterTax="290.00" CurrencyCode="AUD"/>
          <BasicPropertyInfo HotelCode="HOTEL1"/>
        </RoomStay>
      </RoomStays>
      <ResGuests>
        <ResGuest>
          <Profiles>
            <ProfileInfo>
              <Profile ProfileType="1">
                <Customer>
                  <PersonName>
                    <NamePrefix>Mr</NamePrefix>
                    <GivenName>John</GivenName>
                    <Surname>Smith</Surname>
                  </PersonName>
                </Customer>
              </Profile>
            </ProfileInfo>
          </Profiles>
        </ResGuest>
      </ResGuests>
      <ResGlobalInfo>
        <Total CurrencyCode="AUD" AmountAfterTax="290.00"/>
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
                  <VirtualCreditCard isVCC="true" VCCActivationDate="2020-08-23" VCCDeactivationDate="2020-09-19" VCCCurrentBalance="0.00" VCCCurrencyCode="AUD"/>
                </TPA_Extensions>
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
                </Customer>
              </Profile>
            </ProfileInfo>
         </Profiles>
      </ResGlobalInfo>
    </HotelReservation>
  </HotelReservations>
</OTA_HotelResNotifRQ>
```

