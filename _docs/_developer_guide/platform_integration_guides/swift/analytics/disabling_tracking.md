---
nav_title: Disabling iOS SDK Tracking
article_title: Disabling SDK Tracking for iOS
platform: Swift
page_order: 8
description: "This article shows how to disable data collection for the Swift SDK."

---

# Disabling iOS SDK tracking

> To comply with data privacy regulations, data tracking activity on the iOS SDK can be stopped entirely by setting the [`enabled`](https://braze-inc.github.io/braze-swift-sdk/documentation/brazekit/braze/enabled) property on the Braze instance to `false`. 

When set to `false`, the Braze SDK ignores any call to the public API. The SDK also cancels all in-flight actions (network requests, event processing, etc.). If you wish to resume data collection, you can set the [`enabled`](https://braze-inc.github.io/braze-swift-sdk/documentation/brazekit/braze/enabled/) property to `true`.

Additionally, you can use the method [`wipeData()`](https://braze-inc.github.io/braze-swift-sdk/documentation/brazekit/braze/wipedata()) to fully clear locally stored SDK data on the device.

Prior to Swift SDK v5.7.0, IDFV was used as the default device ID. On these older SDK versions, or when setting `useUUIDAsDeviceId` to `false`, additional steps may be required to delete device information. In these cases, unless a user uninstalls all apps from a vendor on a given device, the next time the Braze SDK runs after calling `wipeData()` will result in our server re-identifying that user via their device identifier. In order to fully remove all user data, you should combine a call to `wipeData()` with a request to delete data on the server via the Braze [REST API]({{site.baseurl}}/api/endpoints/user_data/post_user_delete/).

Swift SDK versions 5.7.0 and above default to using a randomly generated UUID as the device ID, and calling `wipeData()` will result in a new device ID to be randomly generated.
