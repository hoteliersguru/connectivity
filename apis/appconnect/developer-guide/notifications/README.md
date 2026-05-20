# Notifications

Notifications are pushed from the Channel Manager as they happen.

The request is pushed with a jwt, that can be validated with the Channel Manager's public key's found at:

```
https://hoteliers.guru/channel-manager/certs
```

Sample of jwt:

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjM1MWU0OTM0LTBjZDEtNGQ1MC1jZjk0LTE5YTU4NWVlNzM4YSJ9.eyJhdWQiOiJBSU9TRUxMIiwianRpIjoiMzUxZTQ5MzQtMGNkMS00ZDUwLWNmOTQtMTlhNTg1ZWU3MzhhIiwiaWF0IjoxNzE3MDEwMTkyLCJuYmYiOjE3MTcwMTAxOTIsImV4cCI6MTcxNzA5NjU5Miwic3ViIjoiMDAwMDAxIiwic2NvcGVzIjpudWxsfQ.KsOc9h7KwKV1p-4TFBgR_E-1rXilbT4kScCYsKmG-Y0HcduZQ7H9y7uOL1zvHtUK4uGntD68FGxNbHRoO6vYLd3cxHxplHxNycqYOXBlYZ3iui7vrp9NZvYe4seRnU8SgfAGLmo4Uj9X85LyFu16POyeEjhWNBh8lPUYyFW_0bmT03cLNf7Zg2qyi8HqYM0UD8dB13F8fOtKXC5aENNfquteef7XfXXuXV96TPGIwcrCWa-0QgdHQzvyO_ptu-Zn9JCLdGxRYz9E2ZYtRQeOpB7xADBRMCjnHjZ-pNM7jKbbNPjO5ZFa7xj_iNLj4VIzyMMmNeCuTmb8SkF-Ag6JPQ
```

Header

```
{
  "typ": "JWT",
  "alg": "RS256",
  "jti": "351e4934-0cd1-4d50-cf94-19a585ee738a"
}
```

Payload

```
{
  "aud": "{YOUR_APP_CODE}",
  "jti": "351e4934-0cd1-4d50-cf94-19a585ee738a",
  "iat": 1717010192,
  "nbf": 1717010192,
  "exp": 1717096592,
  "sub": "000001",
  "scopes": null
}
```

| Field  | Example                              | Description                                                                                                                     |
| ------ | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| aud    | CMAPP                                | Your Application Code assigned by the Channel Manager.                                                                          |
| jti    | 351e4934-0cd1-4d50-cf94-19a585ee738a | The channel manager client id.                                                                                                  |
| iat    | 1717010192                           | Time at which the JWT was issued.                                                                                               |
| nbf    | 1717010192                           | The "nbf" (not before) claim identifies the time before which the JWT MUST NOT be accepted for processing.                      |
| exp    | 1717096592                           | The "exp" (expiration time) claim identifies the expiration time on or after which the JWT MUST NOT be accepted for processing. |
| sub    | 000001                               | The hotel code used by the Channel Manager.                                                                                     |
| scopes | null                                 | Scopes assigned to the app if applicable.                                                                                       |

#### Sample PUSH

```
curl --location --request POST '{your_api_endpoint}' \
--header 'Content-Type: application/xml;charset=UTF-8' \
--header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjM1MWU0OTM0LTBjZDEtNGQ1MC1jZjk0LTE5YTU4NWVlNzM4YSJ9.eyJhdWQiOiJBSU9TRUxMIiwianRpIjoiMzUxZTQ5MzQtMGNkMS00ZDUwLWNmOTQtMTlhNTg1ZWU3MzhhIiwiaWF0IjoxNzE3MDEwMTkyLCJuYmYiOjE3MTcwMTAxOTIsImV4cCI6MTcxNzA5NjU5Miwic3ViIjoiMDAwMDAxIiwic2NvcGVzIjpudWxsfQ.KsOc9h7KwKV1p-4TFBgR_E-1rXilbT4kScCYsKmG-Y0HcduZQ7H9y7uOL1zvHtUK4uGntD68FGxNbHRoO6vYLd3cxHxplHxNycqYOXBlYZ3iui7vrp9NZvYe4seRnU8SgfAGLmo4Uj9X85LyFu16POyeEjhWNBh8lPUYyFW_0bmT03cLNf7Zg2qyi8HqYM0UD8dB13F8fOtKXC5aENNfquteef7XfXXuXV96TPGIwcrCWa-0QgdHQzvyO_ptu-Zn9JCLdGxRYz9E2ZYtRQeOpB7xADBRMCjnHjZ-pNM7jKbbNPjO5ZFa7xj_iNLj4VIzyMMmNeCuTmb8SkF-Ag6JPQ' \
--data-raw '<?xml version="1.0" encoding="UTF-8"?>
<OTA_HotelResNotifRQ xmlns="http://www.opentravel.org/OTA/2003/05" Version="1.0" TimeStamp="2024-05-30T02:14:33+07:00" EchoToken="b7373821-83d1-4146-c54b-5abbc422f4b8"><HotelReservations><HotelReservation CreateDateTime="2024-05-29T21:26:31+07:00" ResStatus="Commit"><UniqueID Type="14" ID="2124584"/><RoomStays><RoomStay><RoomRates><RoomRate RoomTypeCode="ACKmX" NumberOfUnits="1" RatePlanCode="EBMZC"><Rates><Rate EffectiveDate="2024-07-01" ExpireDate="2024-07-01" UnitMultiplier="1"><Base CurrencyCode="THB" AmountAfterTax="4815.0000"/></Rate><Rate EffectiveDate="2024-07-02" ExpireDate="2024-07-02" UnitMultiplier="1"><Base CurrencyCode="THB" AmountAfterTax="4815.0000"/></Rate></Rates></RoomRate></RoomRates><TimeSpan Start="2024-07-01" End="2024-07-03"/><Total CurrencyCode="THB" AmountAfterTax="9330.0000"/><BasicPropertyInfo HotelCode="000001"/></RoomStay></RoomStays><ResGlobalInfo><Total CurrencyCode="THB" AmountAfterTax="8703.5600"/></ResGlobalInfo></HotelReservation></HotelReservations></OTA_HotelResNotifRQ>'
```

* [Inventory](inventory.md)
* [Reservation](reservation.md)
