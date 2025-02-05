---
nav_title: "GET: App Sessions by Time"
page_order: 4

layout: api_page

page_type: reference
platform: API
tool: Segments
description: "This article outlines details about the App Sessions by Time endpoint."
---
{% api %}
# Session Analytics Endpoint
{% apimethod get %}
/sessions/data_series
{% endapimethod %}

This endpoint allows you to retrieve a series of the number of sessions for your app over a designated time period.

{% apiref postman %}https://documenter.getpostman.com/view/4689407/SVYrsdsG?version=latest#79efb6a9-62ec-4b8a-bf4a-e96313aa4be1 {% endapiref %}

## Request Parameters

| Parameter| Required | Data Type | Description |
| -------- | -------- | --------- | ----------- |
| `length` | Yes | Integer | Max number of units (days or hours) before `ending_at` to include in the returned series - must be between 1 and 100 inclusive. |
| `unit` | No | String | Unit of time between data points - can be "day" or "hour" (defaults to "day"). |
| `ending_at` | No | DateTime (ISO 8601 string) | Point in time when the data series should end - defaults to time of the request. |
| `app_id` | No | String | App API identifier retrieved from the Developer Console to limit analytics to a specific app. |
| `segment_id` | No | String | Segment API identifier indicating the analytics enabled segment for which sessions should be returned. |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3  .reset-td-br-4}

### Request Components
- [Segment Identifier]({{site.baseurl}}/api/identifier_types/)

## Example Request
{% raw %}
```
curl --location -g --request GET 'https://rest.iad-01.braze.com/sessions/data_series?length=14&unit=day&ending_at=2018-06-28T23:59:59-5:00&app_id={{app_identifier}}&segment_id={{segment_identifier}}' \
--header 'Authorization: Bearer YOUR-REST-API-KEY'
```
{% endraw %}

## Response

```json
Content-Type: application/json
Authorization: Bearer YOUR-REST-API-KEY
{
    "message": (required, string) the status of the export, returns 'success' when completed without errors,
    "data" : [
        {
            "time" : (string) point in time - as ISO 8601 extended when unit is "hour" and as ISO 8601 date when unit is "day",
            "sessions" : (int)
        },
        ...
    ]
}
```

{% alert tip %}
For help with CSV and API exports, visit our troubleshooting article [here]({{site.baseurl}}/user_guide/data_and_analytics/export_braze_data/export_troubleshooting/).
{% endalert %}

{% endapi %}
