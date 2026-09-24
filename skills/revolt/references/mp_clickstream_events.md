# mp_clickstream_events

## Glossary

**Overview:** This sheet lists the clickstream event details for Markeplace related journeys on the consigner and operator apps/website

**How to read 'Consigner App' tab:** The below table lists all the fields, their meanings and the equivalent mapping names that can be used to join with similar fields in the 'mp_analytics_core.fact_cx_events_l3m' table.
The fields 'Flow/ Feature Name', 'Describe Screen', 'Describe User Action' are defined in this sheet to describe and classify the events and not present in any database table. The stakeholder's query should be mapped to these fields to find the right Flow/Feature name > Screen > User Action that the stakeholder is talking about.
The rest of the fields are present in the mentioned table

| Field | Description | Mapping_name |
| --- | --- | --- |
| Flow/ Feature Name | Defines the flow name or the feature name by which it is commonly addressed eg. Signup flow, Demand flow, VIP Pass feature |  |
| Describe Screen | Defines the name of the screen where the event gets triggerred |  |
| Describe User Action | Defines the user action or system action that causes the event to trigger |  |
| Event name | Defines the name of the event | eventname |
| Event action | Defines the action type:  Click or View | event_action |
| Event Category | Defines the event category | event_category |
| Screen name | Defines the screen name. This is not same as 'Describe Screen' field. | screen_name |
| Demand ID | Defines whether demand_id is populated on the given event or not | demand_id |
| Entity id | Defines the entity | entity_id |
| Miscellaneous | Defines the extra field which can contain additional metadata related to the event | miscellaneous |
| user_code | Defines whether user_code is populated on the given event or not | user_code |

## Consigner App

| Flow/ Feature Name | Describe Screen | Describe User Action | Event Name | Event Action | Event Category | Screen Name | Demand ID | Entity id | Miscellaneous | user_code |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Signup Flow | Login/Signup | Impression | v1_offer_signup_screen | view |  | offer_screen | False |  |  | False |
| Signup Flow | Basic Details Input | Impression | v1_basic_details | view |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details Input | Clicks 'Name' field | v1_enter_name | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details Input | Clicks 'Sales Representative' field | v1_enter_salesrep | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details Input |  | v1_sales_contact | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details Input |  | v1_next | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details Input |  | v1_back | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Business Category Input |  | v1_business_category | view |  | sign_up_business_category | False |  |  | False |
| Signup Flow | Business Category Input |  | v1_next | click |  | sign_up_business_category | False |  | business_category - id | False |
| Signup Flow | Business Category Input |  | v1_previous | click |  | sign_up_business_category | False |  |  | False |
| Signup Flow | Business Category Input |  | v1_back | click |  | sign_up_business_category | False |  |  | False |
| Signup Flow | Trip Potential Input |  | v1_expected_trip_count | view |  | sign_up_expected_trip_count | False |  |  | False |
| Signup Flow | Trip Potential Input |  | v1_submit | click |  | sign_up_expected_trip_count | False |  | expected_trip_count- id | False |
| Signup Flow | Trip Potential Input |  | v1_previous | click |  | sign_up_expected_trip_count | False |  |  | False |
| Signup Flow | Trip Potential Input |  | v1_back | click |  | sign_up_expected_trip_count | False |  |  | False |
| Signup Flow | Trip Potential Input |  | v1_success_bottomsheet | view |  | sign_up_expected_trip_count | False |  |  | False |
| Signup Flow | Insurance Opt in |  | v1_pricing_type | click | insurance_pricing | insurance | True |  | type:fragile/non-fragile | False |
| Signup Flow | Insurance Opt in |  | v1_update_pricing | click | Insurance | <dynamic_screen> | True |  |  | False |
| Signup Flow | Insurance Opt in |  | v1_view_pricing | click | Insurance | <dynamic_screen> | True |  |  | False |
| Signup Flow | Insurance Opt in |  | v1_confim | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |
| Signup Flow | Insurance Opt in |  | v1_view_fragile | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |
| Signup Flow | Insurance Opt in |  | V1_close | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |
| Signup Flow | Insurance Opt in |  | v1_ok | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |
| Signup Flow | Insurance Opt in |  | v1_ok | click | fragile_items_list | <dynamic_screen> | True |  |  | False |
|  |  |  |  |  |  |  | False |  |  | False |
|  |  |  |  |  |  |  | False |  |  | False |
|  |  |  |  |  |  |  | False |  |  | False |
|  |  |  |  |  |  |  | False |  |  | False |
|  |  |  |  |  |  |  | False |  |  | False |
|  |  |  |  |  |  |  | False |  |  | False |

## Operator App

| Journey | Feature Description | Page Description | Event Description | Important Details | Event name | Event action | Event Category | Screen name | Miscellaneous | Entity id |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| - | - | - | - | - | add exact value | add exact value | add exact value | add exact value | add only key values and their defination if needed | add only key values and their defination if needed |
| Demand Confirmation Flow | After DR, notification for rate confirmation are being sent to eligible FO. And  demand card in shown on Confirm Load page.<br>This flow covers journey from Notification/Demand Card to Token payment | Overlay notification | Notification delivered | To identify exact event,  notification id to be matched with fact_notification_history_s3 with filter notification_type="Booking Automation" | NotificationStatus | view |  |  | nid |  |
|  |  |  | Action taken on the notification | Following action are defined as,<br>CONFIRM_BOOKING - Click on Confirm<br>NEED_PROGRAM - Click anywhere on notification<br>DISMISS - Click on back button | NotificationAction | click |  |  | nid<br>action |  |
|  |  | Demand Card | Demand card viewed |  | v1_load_card | view | load_card | web_confirm_load | amount : Rate shown to FO<br>demand_index : Rank of card starting from 0 | demand_id |
|  |  |  | Clicked on Demand Card |  | v1_load_confirm | click | load_card | web_confirm_load | entity : demand_id<br>freight : Rate shown to FO<br>demand_index : Rank of card starting from 0 |  |
|  |  | Token Page | Toke Page viewed |  | v1_load_confirmation | view |  | web_load_confirmation | conf_freight : Rate shown to FO | demandId |
|  |  |  | Token Paid clicked |  | v1_submit_btn | click | bottom_nav | web_load_confirmation | conf_freight : Rate shown to FO | demandId |
|  |  |  |  | This is scroll button | v1_submit_btn | click | we_wallet_bottom_sheet | web_load_confirmation | conf_freight : Rate shown to FO | demandId |
| Bidding Flow | FO asked to quote their rate for demands.<br>This flow covers journey from Notification/Demand Card to Token payment | Overlay notification | Notification delivered | To identify exact event,  notification id to be matched with fact_notification_history_s3 with filter notification_type="Bidding" | NotificationStatus | view |  |  | nid |  |
|  |  |  | Action taken on the notification | Following action are defined as,<br>CONFIRM_BOOKING - Click on Confirm<br>NEED_PROGRAM - Click anywhere on notification<br>DISMISS - Click on back button | NotificationAction | click |  |  | nid<br>action |  |
|  |  | Demand Card | Demand card viewed |  | v1_load_card | view | load_card | web_confirm_load | amount : Always null value<br>demand_index : Rank of card starting from 0 | demand_id |
|  |  |  | Clicked on Demand Card |  | v1_rate_and_confirm | click | load_cards | web_confirm_load | entity : demand_id<br>demand_index : Rank of card starting from 0 |  |
|  |  | Bidding | Bidding Page viewed |  | v1_rate_and_confirm | view | rate_and_confirm | web_rate_and_confirm | conf_freight : Always null value | demandId |
|  |  |  | Rate edited |  | v1_plus | click | bottom_nav | web_rate_and_confirm |  | demand_id |
|  |  |  |  |  | v1_minus | click | bottom_nav | web_rate_and_confirm |  | demand_id |
|  |  |  | Token Paid clicked |  | v1_submit | click | bottom_nav | web_rate_and_confirm | conf_freight : Rate selected by FO<br>get_prob : % probability value shown to FO | demand_id |
|  |  |  |  | This is scroll button | v1_submit_btn | click | we_wallet_bottom_sheet | web_load_confirmation | token_amt : Rate selected by FO | demandId |
