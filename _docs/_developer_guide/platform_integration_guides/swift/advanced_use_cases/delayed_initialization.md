---
nav_title: Delayed Initialization
article_title: Delayed Initialization for iOS
platform: Swift
page_order: 6
description: "This article covers how to implement the Swift SDK delayed initialization to preserve push notification handling when the SDK is initialized asynchronously."

---

# Delayed Initialization

Delayed initialization is a feature that allows you to initialize the Braze SDK asynchronously while ensuring that push notification handling is preserved. This feature is useful when you need to perform additional setup before initializing the SDK, such as fetching configuration data from a server or waiting for user consent.

## Step 1: Preparing the SDK for delayed initialization

By default, push notifications received and clicked while your application is in the terminated state cannot be processed before the SDK is initialized. Since the version [9.1.0][1] of the Braze Swift SDK, we offer a new static helper method to handle this scenario: [Braze.prepareForDelayedInitialization(pushAutomation:)][2].

This method prepares the SDK for delayed initialization by setting up the push automation system. All push notifications originating from Braze will be captured, queued, and processed by the SDK once it is initialized. This method must be called as early as possible in your application lifecycle, in or before the `application(_:didFinishLaunchingWithOptions:)` method of your `AppDelegate`.

> Non-Braze push notifications will not be captured by the SDK and will be handled by the system delegate methods as usual.

{% tabs %}
{% tab Swift (UIKit) %}

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
  // Prepare the SDK for delayed initialization
  Braze.prepareForDelayedInitialization()

  // ... Additional non-Braze setup code

  return true
}
```

{% endtab %}
{% tab Swift (SwiftUI) %}

SwiftUI applications that do not implement the [@UIApplicationDelegateAdaptor][3] property wrapper can add the call to `prepareForDelayedInitialization()` in the `init` method of the `App` struct.

```swift
@main
struct MyApp: App {

  init() {
    // Prepare the SDK for delayed initialization
    Braze.prepareForDelayedInitialization()
  }

  var body: some Scene {
    WindowGroup {
      ContentView()
    }
  }
}
```

{% endtab %}
{% tab Objective-C %}

```objc
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  // Prepare the SDK for delayed initialization
  [Braze prepareForDelayedInitialization];
  
  // ... Additional non-Braze setup code

  return YES;
}

```

{% endtab %}
{% endtabs %}

> [Braze.prepareForDelayedInitialization(pushAutomation:)][2] takes an optional `pushAutomation` parameter that represents the automation configuration for push notifications. See [Braze.Configuration.Push.Automation][4] for more information. When this parameter is `nil`, all automation features are enabled except requesting authorization at launch.

## Step 2: Initializing the Braze SDK

Once the SDK is prepared for delayed initialization, you can initialize the SDK asynchronously at a later time. The SDK will process all queued push notifications events once it is initialized.

To do so, simply follow the standard initialization process described in the [Completing the integration][5] documentation page.

## Important considerations

By using `Braze.prepareForDelayedInitialization(pushAutomation:)`, the SDK will automatically be configured to use the push notification automation features. Any system delegate methods that handle push notifications will not be called for push notifications originating from Braze.

Actions resulting of the user clicking on the push notification will be processed by the SDK once it is initialized. For instance, if the user clicks on a push notification that opens a deeplink, the deeplink will be opened only after the `Braze` instance is initialized.

If you need to perform additional processing on Braze push notifications, please refer to the [Subscribing to push notifications updates][6]. You must implement the subscription handler right after initializing the SDK to receive updates for push notifications that were previously enqueued.

[1]: https://github.com/braze-inc/braze-swift-sdk/releases/tag/9.1.0
[2]: https://braze-inc.github.io/braze-swift-sdk/documentation/brazekit/braze/preparefordelayedinitialization(pushautomation:)
[3]: https://developer.apple.com/documentation/swiftui/uiapplicationdelegateadaptor
[4]: https://braze-inc.github.io/braze-swift-sdk/documentation/brazekit/braze/configuration-swift.class/push-swift.class/automation-swift.class
[5]: {{site.baseurl}}/developer_guide/platform_integration_guides/swift/initial_sdk_setup/completing_integration/
[6]: {{site.baseurl}}/developer_guide/platform_integration_guides/swift/push_notifications/integration/#subscribing-to-push-notifications-updates
