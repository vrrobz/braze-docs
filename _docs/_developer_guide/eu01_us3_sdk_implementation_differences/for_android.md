---
nav_title: For Android
page_order: 0

page_type: reference
description: "This article describes extra Android implementation steps customers on the EU-01 instance will need to take."
platform: Android
---

# For Android
To update the default endpoint in your integration of the Braze SDKs please add the following code to your `braze.xml`, where `sdk.fra-01.braze.eu` is your secure endpoint:

``<string translatable="false" name="com_appboy_custom_endpoint">sdk.fra-01.braze.eu</string>``

SDK Endpoint configuration via `braze.xml` is available starting with Braze Android SDK v2.1.1.
