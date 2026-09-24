# mp_clickstream_events

## Glossary

**Overview:** This sheet lists the clickstream event details for Markeplace related journeys on the consigner and operator apps/website

How to read 'Consigner App' tab

| Field | Description | Mandatory |
| --- | --- | --- |
| Flow/ Feature Name | Defines the flow name or the feature name by which it is commonly addressed eg. Signup flow, Demand flow, VIP Pass feature | Yes |
| Describe Screen | Defines the name of the screen where the event gets triggerred | Yes |
| Describe User Action | Defines the user action or system action that causes the event to trigger | Yes |
| Event name | Defines the name of the event | Yes |
| Event action | This is self explanatory (Live/ 100% Scaled/ Rolled Back) | Yes |
| Event Category |  | No |
| Screen name | Unique id attached to a variant of the experiment. It might repeat across experiments. | Yes |
| Demand_id | Test /Control/ <User defined> | Yes |
| Entity id | Defines any hard filter that has to be used while calculating any metric for comparing variant performance eg. 'Demands where VT is Trailers' means we only have to consider demands where vehicle type is trailers | No |
| Miscellaneous | Defines the traffic metric for the experiment | Yes |
| user_code | Self explanatory | No |

## Consigner App

| Flow/ Feature Name | Describe Screen | Describe User Action | Event Name | Event Action | Event Category | Screen Name | Demand ID | Entity id | Miscellaneous | user_code |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Signup Flow | Login/Signup | Impression | v1_offer_signup_screen | view |  | offer_screen | False |  |  | False |
| Signup Flow | Basic Details | Impression | v1_basic_details | view |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details | Clicks 'Name' field | v1_enter_name | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details | Clicks 'Sales Representative' field | v1_enter_salesrep | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details |  | v1_sales_contact | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details |  | v1_next | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Basic Details |  | v1_back | click |  | sign_up_basic_details | False |  |  | False |
| Signup Flow | Business Category |  | v1_business_category | view |  | sign_up_business_category | False |  |  | False |
| Signup Flow | Business Category |  | v1_next | click |  | sign_up_business_category | False |  | business_category - id | False |
| Signup Flow | Business Category |  | v1_previous | click |  | sign_up_business_category | False |  |  | False |
| Signup Flow | Business Category |  | v1_back | click |  | sign_up_business_category | False |  |  | False |
| Signup Flow | Trip Potential |  | v1_expected_trip_count | view |  | sign_up_expected_trip_count | False |  |  | False |
| Signup Flow | Trip Potential |  | v1_submit | click |  | sign_up_expected_trip_count | False |  | expected_trip_count- id | False |
| Signup Flow | Trip Potential |  | v1_previous | click |  | sign_up_expected_trip_count | False |  |  | False |
| Signup Flow | Trip Potential |  | v1_back | click |  | sign_up_expected_trip_count | False |  |  | False |
| Signup Flow | Trip Potential |  | v1_success_bottomsheet | view |  | sign_up_expected_trip_count | False |  |  | False |
| Signup Flow |  |  | v1_pricing_type | click | insurance_pricing | insurance | True |  | type:fragile/non-fragile | False |
| Signup Flow |  |  | v1_update_pricing | click | Insurance | <dynamic_screen> | True |  |  | False |
| Signup Flow |  |  | v1_view_pricing | click | Insurance | <dynamic_screen> | True |  |  | False |
| Signup Flow |  |  | v1_confim | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |
| Signup Flow |  |  | v1_view_fragile | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |
| Signup Flow |  |  | V1_close | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |
| Signup Flow |  |  | v1_ok | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |
| Signup Flow |  |  | v1_ok | click | fragile_items_list | <dynamic_screen> | True |  |  | False |
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
