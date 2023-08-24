# Payment XML Samples

### Credit Card Details and no Deposit <a id="PaymentXMLSamples-CreditCardDetailsandnoDeposit"></a>

Sample of reservations with guarantee credit card details.

**Credit card details**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
  <POS>
    <Source>
      <RequestorID Type="22" ID="BA1"/>
    </Source>
  </POS>
  <HotelReservations>
    <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
      <UniqueID Type="14" ID="3741"/>
      <RoomStays>
        <RoomStay>
          <RoomTypes>
            <RoomType RoomTypeCode="ROOM1">
              <RoomDescription Name="Standard Room"/>
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
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-15">
                  <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
                </Rate>
              </Rates>
            </RoomRate>
          </RoomRates>
          <GuestCounts IsPerRoom="1">
            <GuestCount AgeQualifyingCode="10" Count="2"/>
          </GuestCounts>
          <TimeSpan End="2012-03-15" Start="2012-03-12"/>
          <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
          <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel" />
          <ResGuestRPHs>
            <ResGuestRPH RPH="1"/>
          </ResGuestRPHs>
        </RoomStay>
      </RoomStays>
      <ResGuests>
        <ResGuest ResGuestRPH="1" ArrivalTime="14:00:00" PrimaryIndicator="1">
          <Profiles>
            <ProfileInfo>
              <Profile ProfileType="1">
                <Customer>
                  <PersonName>
                    <GivenName>John</GivenName>
                    <Surname>Smith</Surname>
                  </PersonName>
                  <Telephone PhoneNumber="44-69-66564100"/>
                  <Email>test@gmail.com</Email>
                </Customer>
              </Profile>
            </ProfileInfo>
          </Profiles>
        </ResGuest>
      </ResGuests>
      <ResGlobalInfo>
        <Total CurrencyCode="THB" AmountAfterTax="900.00"/>
        <Guarantee>
          <GuaranteesAccepted>
            <GuaranteeAccepted>
              <PaymentCard CardNumber="4010401040104010" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                <CardHolderName>John Smith</CardHolderName>
              </PaymentCard>
            </GuaranteeAccepted>
          </GuaranteesAccepted>
        </Guarantee>
      </ResGlobalInfo>
    </HotelReservation>
  </HotelReservations>
</OTA_HotelResNotifRQ>
```

### Credit Card Details with 3DS and no Deposit <a id="PaymentXMLSamples-CreditCardDetailswith3DSandnoDeposit"></a>

Sample of reservations with guarantee credit card details with 3DS.

**Credit card details and 3DS**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
  <POS>
    <Source>
      <RequestorID Type="22" ID="BA1"/>
    </Source>
  </POS>
  <HotelReservations>
    <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
      <UniqueID Type="14" ID="3741"/>
      <RoomStays>
        <RoomStay>
          <RoomTypes>
            <RoomType RoomTypeCode="ROOM1">
              <RoomDescription Name="Standard Room"/>
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
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-15">
                  <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
                </Rate>
              </Rates>
            </RoomRate>
          </RoomRates>
          <GuestCounts IsPerRoom="1">
            <GuestCount AgeQualifyingCode="10" Count="2"/>
          </GuestCounts>
          <TimeSpan End="2012-03-15" Start="2012-03-12"/>
          <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
          <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel" />
          <ResGuestRPHs>
            <ResGuestRPH RPH="1"/>
          </ResGuestRPHs>
        </RoomStay>
      </RoomStays>
      <ResGuests>
        <ResGuest ResGuestRPH="1" ArrivalTime="14:00:00" PrimaryIndicator="1">
          <Profiles>
            <ProfileInfo>
              <Profile ProfileType="1">
                <Customer>
                  <PersonName>
                    <GivenName>John</GivenName>
                    <Surname>Smith</Surname>
                  </PersonName>
                  <Telephone PhoneNumber="44-69-66564100"/>
                  <Email>test@gmail.com</Email>
                </Customer>
              </Profile>
            </ProfileInfo>
          </Profiles>
        </ResGuest>
      </ResGuests>
      <ResGlobalInfo>
        <Total CurrencyCode="THB" AmountAfterTax="900.00"/>
        <Guarantee>
          <GuaranteesAccepted>
            <GuaranteeAccepted>
              <PaymentCard CardNumber="4010401040104010" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                <CardHolderName>John Smith</CardHolderName>
                <ThreeDomainSecurity>
                  <Results>
                    <threeDSVersion>1.0.2</threeDSVersion>
                    <xid>z9UKb06xLziZMOXBEmWSVA1kwG0=</xid>
                    <cavv>MTIzNDU2Nzg5MDEyMzQ1Njc4OTA=</cavv>
                    <eci>05</eci>
                  </Results>
                </ThreeDomainSecurity>
              </PaymentCard>
            </GuaranteeAccepted>
          </GuaranteesAccepted>
        </Guarantee>
      </ResGlobalInfo>
    </HotelReservation>
  </HotelReservations>
</OTA_HotelResNotifRQ>
```

### Credit Card Details and Deposit Payment <a id="PaymentXMLSamples-CreditCardDetailsandDepositPayment"></a>

Sample of reservation with deposit payment and credit card details.

**Deposit and Credit Card details**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
  <POS>
    <Source>
      <RequestorID Type="22" ID="BA1"/>
    </Source>
  </POS>
  <HotelReservations>
    <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
      <UniqueID Type="14" ID="3741"/>
      <RoomStays>
        <RoomStay>
          <RoomTypes>
            <RoomType RoomTypeCode="ROOM1">
              <RoomDescription Name="Standard Room"/>
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
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-15">
                  <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
                </Rate>
              </Rates>
            </RoomRate>
          </RoomRates>
          <GuestCounts IsPerRoom="1">
            <GuestCount AgeQualifyingCode="10" Count="2"/>
          </GuestCounts>
          <TimeSpan End="2012-03-15" Start="2012-03-12"/>
          <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
          <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel" />
          <ResGuestRPHs>
            <ResGuestRPH RPH="1"/>
          </ResGuestRPHs>
        </RoomStay>
      </RoomStays>
      <ResGuests>
        <ResGuest ResGuestRPH="1" ArrivalTime="14:00:00" PrimaryIndicator="1">
          <Profiles>
            <ProfileInfo>
              <Profile ProfileType="1">
                <Customer>
                  <PersonName>
                    <GivenName>John</GivenName>
                    <Surname>Smith</Surname>
                  </PersonName>
                  <Telephone PhoneNumber="44-69-66564100"/>
                  <Email>test@gmail.com</Email>
                </Customer>
              </Profile>
            </ProfileInfo>
          </Profiles>
        </ResGuest>
      </ResGuests>
      <ResGlobalInfo>
        <Total CurrencyCode="THB" AmountAfterTax="900.00"/>
        <DepositPayments>
          <GuaranteePayment>
            <AcceptedPayments>
              <AcceptedPayment>
                <PaymentCard CardNumber="4010401040104010" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                  <CardHolderName>John Smith</CardHolderName>
                </PaymentCard>
              </AcceptedPayment>
            </AcceptedPayments>
            <AmountPercent Amount="90.00" CurrencyCode="THB"/>
          </GuaranteePayment>
        </DepositPayments>
      </ResGlobalInfo>
    </HotelReservation>
  </HotelReservations>
</OTA_HotelResNotifRQ>
```

### Deposit Payment by Virtual Credit Card <a id="PaymentXMLSamples-DepositPaymentbyVirtualCreditCard"></a>

Sample of reservation with deposit payment and virtual credit card details.

**Deposit Payment by Virtual Credit Card**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
  <POS>
    <Source>
      <RequestorID Type="22" ID="BA1"/>
    </Source>
  </POS>
  <HotelReservations>
    <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
      <UniqueID Type="14" ID="3741"/>
      <RoomStays>
        <RoomStay>
          <RoomTypes>
            <RoomType RoomTypeCode="ROOM1">
              <RoomDescription Name="Standard Room"/>
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
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-15">
                  <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
                </Rate>
              </Rates>
            </RoomRate>
          </RoomRates>
          <GuestCounts IsPerRoom="1">
            <GuestCount AgeQualifyingCode="10" Count="2"/>
          </GuestCounts>
          <TimeSpan End="2012-03-15" Start="2012-03-12"/>
          <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
          <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel" />
          <ResGuestRPHs>
            <ResGuestRPH RPH="1"/>
          </ResGuestRPHs>
        </RoomStay>
      </RoomStays>
      <ResGuests>
        <ResGuest ResGuestRPH="1" ArrivalTime="14:00:00" PrimaryIndicator="1">
          <Profiles>
            <ProfileInfo>
              <Profile ProfileType="1">
                <Customer>
                  <PersonName>
                    <GivenName>John</GivenName>
                    <Surname>Smith</Surname>
                  </PersonName>
                  <Telephone PhoneNumber="44-69-66564100"/>
                  <Email>test@gmail.com</Email>
                </Customer>
              </Profile>
            </ProfileInfo>
          </Profiles>
        </ResGuest>
      </ResGuests>
      <ResGlobalInfo>
        <Total CurrencyCode="THB" AmountAfterTax="900.00"/>
        <DepositPayments>
          <GuaranteePayment>
            <AcceptedPayments>
              <AcceptedPayment>
                <PaymentCard CardNumber="4010401040104010" CardType="1" ExpireDate="0614" SeriesCode="123" CardCode="VI">
                  <CardHolderName>John Smith</CardHolderName>
                  <TPA_Extensions>
                    <VirtualCreditCard isVCC="true" VCCActivationDate="2020-08-23" VCCDeactivationDate="2020-09-19" VCCCurrentBalance="100.00" VCCCurrencyCode="THB"/>
                  </TPA_Extensions>
                </PaymentCard>
              </AcceptedPayment>
            </AcceptedPayments>
            <AmountPercent Amount="90.00" CurrencyCode="THB"/>
          </GuaranteePayment>
        </DepositPayments>
      </ResGlobalInfo>
    </HotelReservation>
  </HotelReservations>
</OTA_HotelResNotifRQ>
```

### Deposit Payment <a id="PaymentXMLSamples-DepositPayment"></a>

Sample of reservation with deposit payment.

**Deposit payment**

```text
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" EchoToken="f540ac67-d066-4b06-8f74-8fc616f2e8fc" ResStatus="Commit" TimeStamp="2020-09-10T16:20:32+0700">
  <POS>
    <Source>
      <RequestorID Type="22" ID="BA1"/>
    </Source>
  </POS>
  <HotelReservations>
    <HotelReservation CreateDateTime="2012-03-09T21:31:52+02:00">
      <UniqueID Type="14" ID="3741"/>
      <RoomStays>
        <RoomStay>
          <RoomTypes>
            <RoomType RoomTypeCode="ROOM1">
              <RoomDescription Name="Standard Room"/>
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
                <Rate UnitMultiplier="1" RateTimeUnit="Day" EffectiveDate="2012-03-12" ExpireDate="2012-03-15">
                  <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
                </Rate>
              </Rates>
            </RoomRate>
          </RoomRates>
          <GuestCounts IsPerRoom="1">
            <GuestCount AgeQualifyingCode="10" Count="2"/>
          </GuestCounts>
          <TimeSpan End="2012-03-15" Start="2012-03-12"/>
          <Total AmountAfterTax="900.00" CurrencyCode="THB"/>
          <BasicPropertyInfo HotelCode="HTL1" HotelName="The Beach Side Hotel" />
          <ResGuestRPHs>
            <ResGuestRPH RPH="1"/>
          </ResGuestRPHs>
        </RoomStay>
      </RoomStays>
      <ResGuests>
        <ResGuest ResGuestRPH="1" ArrivalTime="14:00:00" PrimaryIndicator="1">
          <Profiles>
            <ProfileInfo>
              <Profile ProfileType="1">
                <Customer>
                  <PersonName>
                    <GivenName>John</GivenName>
                    <Surname>Smith</Surname>
                  </PersonName>
                  <Telephone PhoneNumber="44-69-66564100"/>
                  <Email>test@gmail.com</Email>
                </Customer>
              </Profile>
            </ProfileInfo>
          </Profiles>
        </ResGuest>
      </ResGuests>
      <ResGlobalInfo>
        <Total CurrencyCode="THB" AmountAfterTax="900.00"/>
        <DepositPayments>
          <GuaranteePayment>
            <AmountPercent Amount="90.00" CurrencyCode="THB"/>
          </GuaranteePayment>
        </DepositPayments>
      </ResGlobalInfo>
    </HotelReservation>
  </HotelReservations>
</OTA_HotelResNotifRQ>
```

