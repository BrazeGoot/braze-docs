---
nav_title: Catalogs
article_title: Catalogs Endpoints
page_order: 0
layout: dev_guide

search_tag: Endpoint
description: "This landing page lists the Braze catalogs endpoints."
page_type: landing

guide_top_header: "Catalogs Endpoints"
guide_top_text: "Use the Braze Catalogs Endpoints to add, edit, and manage your catalogs and catalog item details. For bulk changes to your catalog, use the asynchronous catalog endpoints. <br><br> Looking for guidance on creating a catalog? Check out our article for <a href='/docs/user_guide/personalization_and_dynamic_content/catalog/'>creating and using catalogs</a>."

guide_featured_title: "Catalog management endpoints<br><br>"
guide_featured_list:
  - name: "DELETE: Delete Catalog"
    link: /docs/api/endpoints/catalogs/catalog_management/synchronous/delete_catalog/
    fa_icon: fas fa-pen-square
  - name: "GET: List Catalogs"
    link: /docs/api/endpoints/catalogs/catalog_management/synchronous/get_list_catalogs/
    fa_icon: fas fa-list-ul
  - name: "POST: Create Catalog"
    link: /docs/api/endpoints/catalogs/catalog_management/synchronous/post_create_catalog/
    fa_icon: fas fa-check

optional_guide_menu_title: "Catalog items endpoints"
guide_menu_title: "<h3>Asynchronous</h3>"
guide_menu_list:
  - name: "DELETE: Delete Multiple Catalog Items Endpoints"
    link: /docs/api/endpoints/catalogs/catalog_items/asynchronous/delete_catalog_items_bulk/
    fa_icon: fas fa-pen-square
  - name: "PATCH: Edit Multiple Catalog Items"
    link: /docs/api/endpoints/catalogs/catalog_items/asynchronous/patch_catalog_items_bulk/
    fa_icon: fas fa-user-edit
  - name: "POST: Create Multiple Catalog Items"
    link: /docs/api/endpoints/catalogs/catalog_items/asynchronous/post_create_catalog_items_bulk/
    fa_icon: fas fa-check
  - name: "PUT: Update Multiple Catalog Items"
    link: /docs/api/endpoints/catalogs/catalog_items/asynchronous/put_update_catalog_items/
    fa_icon: fas fa-user-circle

guide_menu_title2: "<h3>Synchronous</h3>"
guide_menu_list2:  
  - name: "DELETE: Delete Catalog Item"
    link: /docs/api/endpoints/catalogs/catalog_items/synchronous/delete_catalog_item/
    fa_icon: fas fa-pen-square
  - name: "GET: List Catalog Item Details"
    link: /docs/api/endpoints/catalogs/catalog_items/synchronous/get_catalog_item_details/
    fa_icon: fas fa-list-ul
  - name: "GET: List Multiple Catalog Item Details"
    link: /docs/api/endpoints/catalogs/catalog_items/synchronous/get_catalog_items_details_bulk/
    fa_icon: fas fa-list-alt
  - name: "PATCH: Edit Catalog Item"
    link: /docs/api/endpoints/catalogs/catalog_items/synchronous/patch_catalog_item/
    fa_icon: fas fa-user-edit
  - name: "POST: Create Catalog Item"
    link: /docs/api/endpoints/catalogs/catalog_items/synchronous/post_create_catalog_item/
    fa_icon: fas fa-check
  - name: "PUT: Update Catalog Item"
    link: /docs/api/endpoints/catalogs/catalog_items/synchronous/put_update_catalog_item/
    fa_icon: fas fa-user-circle

optional_guide_menu_title_2: "Catalog fields endpoints"
guide_menu_title_2_1: "<h3>Asynchronous</h3>"
guide_menu_list_2_1:
  - name: "POST: Create Catalog Fields"
    link: /docs/api/endpoints/catalogs/catalog_fields/asynchronous/post_create_catalog_fields/
    image: /assets/img/braze_icons/check-square-broken.svg
  - name: "DELETE: Delete Catalog Field"
    link: /docs/api/endpoints/catalogs/catalog_fields/asynchronous/delete_catalog_field/
    image: /assets/img/braze_icons/edit-05.svg

optional_guide_menu_title_3: "Catalog selections endpoints"
guide_menu_title_3_1: "<h3>Asynchronous</h3>"
guide_menu_list_3_1:
  - name: "POST: Create Catalog Selection"
    link: /docs/api/endpoints/catalogs/catalog_selections/asynchronous/post_create_catalog_selection/
    image: /assets/img/braze_icons/check-square-broken.svg
  - name: "DELETE: Delete Catalog Selection"
    link: /docs/api/endpoints/catalogs/catalog_selections/asynchronous/delete_catalog_selection/
    image: /assets/img/braze_icons/edit-05.svg

---