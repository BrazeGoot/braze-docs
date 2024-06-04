---
nav_title: tvOS
article_title: Content Cards for tvOS
platform: tvOS
page_type: reference
description: "Learn how to customize your Content Cards for Apple's tvOS platform."
page_order: 1
---

# Customizing Content Cards for tvOS

> Learn how to customize your Content Cards for Apple's tvOS platform.

## Setting up your tvOS app

### Step 1: Create a new iOS app

In Braze, select **Settings** > **App Settings**, then select **Add App**. Enter a name for your tvOS app, select **iOS**&#8212;_not tvOS_&#8212;then select **Add App**.

![ALT_TEXT.]({% image_buster /assets/img/tvos.png %}){: style="width:70%"}

{% alert warning %}
If you select the **tvOS** checkbox, you will not be able to customize Content Cards for tvOS.
{% endalert %}

### Step 2: Get your app's API key

In your app settings, select your new tvOS app then take note of your app's API key. You'll use this key to configure your app in Xcode.

![ALT_TEXT]({% image_buster /assets/img/tvos1.png %}){: style="width:70%"}

### Step 3: Integrate the Braze Swift SDK

Use your app's API key to integrate the [Braze Swift SDK](https://github.com/braze-inc/braze-swift-sdk) into your tvOS project in Xcode. When you're finished, you can [customize your Content Cards for tvOS](#customizing-your-in-app-messages).

## Customizing your content cards

Because Braze doesn't provide a default UI for Content Cards on tvOS, you'll need to customize them yourself. For a full walkthrough, see our step-by-step tutorial: [Customizing Content Cards for tvOS](https://braze-inc.github.io/braze-swift-sdk/documentation/braze/content-cards-customization/). For a sample project, see [Braze Swift SDK samples](https://github.com/braze-inc/braze-swift-sdk/tree/main/Examples).
