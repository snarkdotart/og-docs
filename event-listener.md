---
icon: broadcast
order: 80
---

# Event Listener

We have three types of events that trigger NFT updates with our trait and artwork generators.

1/ The first type is events comes from the smart contract. These events will be used to trigger changes in metadata and traits. 

To understand the on-chain flow, we can break it down into several steps. Firstly, the user must provide the smart contract address. Then, the user needs to choose the specific type of event they wish to listen to. Our event listener will be able to detect and respond to these chosen events.

2/ The second type of events is chain events from the API. Developers can either pull our API endpoint or implement it in their frontend applications. This way, every user interaction will trigger changes in metadata and artwork.

3/ Lastly, we have time-based events. Similar to a Cron-based schedule, we will use these events to trigger changes in metadata and the artwork generator according to a predefined schedule.