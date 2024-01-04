---
nav_title: Selections
article_title: Selections
page_order: 5
description: "This reference article covers how to create and use selections with your catalogs to reference data in your Braze campaigns."
---

# Selections

> Selections are groups of data that can be used to personalize a message for each user in your campaign. After creating a [catalog]({{site.baseurl}}/user_guide/personalization_and_dynamic_content/catalog/), you can further reference this data by incorporating selections in your Braze campaigns. Note that the free tier of catalogs allows one selection to be created per catalog. 

## Creating a selection

To create a selection, do the following.

1. Select your catalog and go to the **Selection** tab, then click **Create Selection**. 
2. Select the catalog column from the **Filter Field** dropdown. 
3. Select the operator and enter the attribute. 

{% alert note %}
You can create up to 30 selections per catalog.
{% endalert %}

{: start="4"}
4. In the **Sort type** section, specify the order in which results are returned. This includes an option to randomize the sort order. 
5. Enter the maximum number of results, up to 50, for the **Limit number** under the **Results limit** section.
6. Click **Create Selection** and the selection will display above the catalog data. 
7. Create a campaign, then click the plus sign in the **Message** composer.
8. In the **Add Personalization** modal, select:
- **Catalog Items** as the **Personalization Type**
- The catalog name
- The type of selection

{% alert important %}
String fields with more than 1,000 characters cannot be filtered.
{% endalert %}

![The Add Personalization modal with the following selections: "Catalog Items" for "Personalization Type", "Games" for "Catalog Name", "Selections" for "Selection Type", "game_selection" for "Selection", and "title" and "description_en" for "Information to Display".][6]{: style="max-width:70%;"}

### Liquid in selection results

Using any Liquid in catalogs, such as custom attributes and custom events, can result in different results returned for each user in your selection.

![The Selections section in an example catalog.][1]

## Use case

Let's say you own a meal delivery service and want to send a personalized message to your users who have specific meal preferences based on their most recently viewed food category. 

Using a catalog with your meal delivery service's information for the meal name, price, image, and category of the meal, you can create a selection to recommend three meals based on a user's most recently viewed category.

![An example of a selection for a meal delivery service with two filters: one that identifies a product type as a meal, and one that identifies the category as the most recently viewed. The selection is set to randomize the order in which the three results are returned.][2]{: style="max-width:90%;"}

To use this catalog and selection in a campaign, use the **Add Personalization** modal in the message composition section of building a campaign. In this example, we've selected the catalog with your meal delivery service's information, and the selection for meal recommendations based on the most recently viewed category. This allows us to display the meal name and price. To further build your message, you can use the selection to also add an image of the first recommended meal.

![A Content Card with the header "You will LOVE these highly rated meals!" with the selection "recommendations_be_recent_category" in message composition section.][3]{: style="max-width:90%;"}

For example, say you have a user whose most recently viewed category is "Chicken". Using the set personalization and a Content Card campaign, you can send three meal recommendations that include chicken for this user.

![A Content Card with an image of chargrilled lemon chicken, and a list of three meal recommendations that include chicken based on the user's most recently viewed category.][4]{: style="max-width:90%;"}

Using the same personalization, you can also send three meal recommendations for a user whose most recently viewed category is "Beef".

![A Content Card with an image of beef stroganoff, and a list of two meal recommendations that include beef based on the user's most recently viewed category.][5]{: style="max-width:90%;"}


[1]: {% image_buster /assets/img_archive/catalog_selections1.png %}
[2]: {% image_buster /assets/img_archive/catalog_selections2.png %}
[3]: {% image_buster /assets/img_archive/catalog_selections3.png %}
[4]: {% image_buster /assets/img_archive/catalog_selections4.png %}
[5]: {% image_buster /assets/img_archive/catalog_selections5.png %}
[6]: {% image_buster /assets/img_archive/catalog_selections6.png %}