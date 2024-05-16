---
nav_title: Dynamic SMS Link Preview
article_title: Dynamic SMS Link Preview
description: "This reference article outlines how to turn on and use Moveable Ink's SMS link preview feature."
page_type: partner
search_tag: Partner
---

# Dynamic SMS link preview

> With Moveable Ink’s dynamic SMS link preview, you can leverage the immersiveness of MMS at the same cost of SMS. This allows you to use Braze and Moveable Ink to deliver cost-effective, personalized rich messaging experiences.

## Prerequisites

| Requirement | Description |
| --- | --- |
| Moveable Ink account | A Movable Ink account is required to take advantage of this partnership. |
| Data source | You need to connect a data source to Movable Ink. This can be done through CSV, website import, or API. |
| MMS sending capabilities | Confirm that you're set up for MMS through Braze.
| [Link shortening]({{site.baseurl}}/user_guide/message_building_by_channel/sms/campaign/link_shortening/) | Confirm that link shortening is turned on. | 
| Contact Card | Your brand (the sender) must be saved as a contact on the user's phone for link preview to work with iOS. This can be done with a contact card or another method. |
{: .reset-td-br-1 .reset-td-br-2}

## Integration

Follow the respective steps below to send dynamic SMS links for iOS and Android operating systems.

### iOS

{% alert important %}
To allow link preview images for iOS, users must add your brand (the sender) as a contact.
{% endalert %}

#### Step 1: Create a Contact Card campaign

After users use your Braze [content card]({{site.baseurl}}/user_guide/message_building_by_channel/sms/mms/contact_card/) to save your brand as a contact, they will be able to view **Tap to Load Preview** prompts and Moveable Ink links.

![1]{: style="max-width:30%;"}

#### Step 2: Send Moveable Ink links

1. Create an SMS campaign in Moveable Ink and generate your click-through URL.
2. In the Braze dashboard, go to **Campaigns** and set up a new SMS/MMS campaign from the **Create Campaign** dropdown.
3. In the SMS campaign composer:
    - Set your subscription group.
    - Enter your message.
    - Add your Moveable Ink link **last**, after all other text in the message body. <br><br>![2]{: style="max-width:50%;"}

{% alert tip %}
Check out [Liquid]({{site.baseurl}}/user_guide/personalization_and_dynamic_content/liquid/using_liquid/) for a refresher on Liquid personalization.  
{% endalert %}

{: start="4"}
4. You’re all set to test and launch your dynamic SMS link preview campaign.

![3]{: style="max-width:70%;"}

After users load the link preview, a personalized image will render with the ability to link out to your website, app, or landing page.

![4]{: style="max-width:30%;"}

### Android (Google & Samsung devices)

Andriod users aren't required to save your brand as a contact to receive dynamic SMS link previews. However, users who have done so and have turned on automatic previews for their device can automatically view images for preview links.

![5]{: style="max-width:30%;"}

Users who haven't saved your brand as a contact and have turned on automatic previews will have to select **Tap to load preview** to load the image. <br>![6]{: style="max-width:30%;"}

## Considerations

- Only include one preview link in your message. Content will not be generated with multiple links in your SMS body. 
- Don't include any characters after your preview link or the experience might break.


[1]: {% image_buster /assets/img/movable_ink/ios_link.png %}
[2]: {% image_buster /assets/img/movable_ink/ios_message.png %}
[3]: {% image_buster /assets/img/movable_ink/ios_test_launch.png %}
[4]: {% image_buster /assets/img/movable_ink/ios_example.png %}
[5]: {% image_buster /assets/img/movable_ink/android_automatic.png %}
[6]: {% image_buster /assets/img/movable_ink/android_tap.png %}
