# Inventory Push API

ChannelConnect uses OTA\_HotelAvailNotifRQ to push availability and restrictions and OTA\_HotelRateAmountNotifRQ to push rates.

### Content

* [Availability and Restrictions](availability-and-restrictions.md)
* [Rates](rates.md)

{% hint style="warning" %}
#### Inventory API Expectations

* When processing Inventory Messages, your endpoint will need to be able to respond with either a 'Success' or 'Error' response in a reasonable amount of time. ChannelConnect will timeout an Inventory Push message after 15 seconds. It is important to note however that the 15 second timeout is a failsafe. **We expect your endpoint to be able to respond in under 5 seconds.** If any background processing will push response times out beyond 5 seconds, we highly recommend you respond with a 'Success' and continue the background processing without delaying your response.\

* It is important to remember the potential for large amounts of data to be pushed out from ChannelConnect. If a hotel enables their connection, you can potentially receive 1095 days worth of Inventory, Rates and Restrictions all within a short space of time. If you have several properties go live at the same time or push large updates, the data load can be quite large. **We urge that you complete stringent performance testing on your production servers/endpoint(s) to ensure they will scale with the number of hotels you'll have connected in production.**\
  ****
* Please keep in mind that ChannelConnect will PUSH inventory based on the hotel's local timezone as configured in The Channel Manager. You will need to consider this when accepting Inventory PUSH updates from ChannelConnect and ensure that you don't create any timezone conflicts when processing 'Inventory' messages. **Please ensure hotels are aware of any timezone settings that may need to be set within your OTA/Booking Channel extranet.**
{% endhint %}
