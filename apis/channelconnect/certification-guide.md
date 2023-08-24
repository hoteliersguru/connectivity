# Certification Guide

The following steps should be completed, for self-certification. If you don't support all options available then let us know which ones you don't support.

## Retrieve Rooms API

Setup three rooms in your extra-net, and two rate plans, and make sure each room is linked to each rate plan. Make sure all of your inventory is truncated to default values on setup. Allotment and Rates should be 0, all restrictions should be off.

#### Room types

* Superior, \*Occupancy 2 Adults, 1 Child.
* Deluxe, \*Occupancy 3 Adults, 2 Children.
* Family Suite - \*Occupancy 4 Adults, 3 Children.

#### Rate plans

* Breakfast
* Room Only

Initiate the call to Retrieve Rooms API, and save the XML request and response.

Now setup the similar rooms and rate plans in the Channel Manager, and map these as appropriate.

## Inventory Push API

Follow each step, and save the XML request and response for each, after each step, also validate in your extra-net that the correct updates have been done.

Repeat these steps for each Room type, increase values set by adding 2 for availability and restrictions, and by 2000 for rates.

### Room availability

* Set availability in the Channel Manager for 5 days, 10 rooms each.
* Set availability in the Channel Manager for 10 days, leave a gap of 2 days, and populate the 8 days with allotment 4.

### Stop sell or 'close out' of a room

* Set stop sell for the first two days of the period you updated above for 10 rooms, and set stop sell on the fourth day.
* Remove stop sell for the days.

### Closed to arrival, departure, minimum and maximum stays.

* Set closed to arrival on the first, the third and fourth day of the 10 days period you updated above.
* Set closed to departure on the second, fourth, eight and ninth day of the 10 days period.
* Set minimum stay to 3 on the first, second and set it to 2 on the seventh day of the 10 days period.
* Set maximum stay to 5 on the second, third, seventh day, and set it to 2 on the eight and tenth day.
* Remove each of the values you updated.

### Rates \(Rate per Room\)

* Set a 3 days period as follows, 1000 as base rate for Room only, 750 for extra adult, 300 for extra child.
* Remove extra adult rate for 1 of the days.
* Remove extra child rate for 1 of the days.
* Set a 10 days period with 2000 as base rate for Room only, and 2400 as base rate for Breakfast.
* Set a 5 days period with 1000 as base rate, and a 3 days period with 1500 as base rate for Breakfast.
* Set a 3 days period with 500 as base rate, and a 1 days period with 250 as base rate for Room only.

### Inclusions

* Set inclusion to text of your choice for 2 days, and update.
* Remove inclusion added.

### Rates \(Occupancy based\)

If your extra-net supports occupancy based rates, you will need to fully test occupancy based rates.

## Reservation API

Once you have completed testing Inventory API, and have your extra-net synced with the Channel Manager. You will need to complete the certification by testing the Reservation API. Push the following bookings to the Channel Manager, and save XML request / XML response.

* Two nights, 1 room, 2 adults, 1 child.
* Three nights, 2 rooms, 1 adult in each room.
* one night, 2 rooms, 3 adults.
* four nights, 1 room, 1 adult, 2 children.

This should complete the certification, now send all XML requests / responses to your contact point for verification.







