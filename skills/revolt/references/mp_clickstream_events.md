# mp_clickstream_events

Event dictionary for the app clickstream. Maps every tracked user action to the
exact `event_name` / `event_action` / `event_category` / `screen_name` written
to the event tables, and says which rows carry a `demand_id`.

**Use this before writing any query against clickstream data.** The raw event
tables (`de_analytics.operator_app_events_current_etl`,
`operator_app_click_events_etl`, `operator_app_view_events_etl`, and
`mp_analytics_core.fact_operator_events_l3m`) store these names verbatim.
Names change when the app is redesigned, so a filter written from memory will
silently return zero rather than error — resolve the literal here first.

**Demand id is not on every screen.** The `Entity id` column says which event
carries it and under which key (`demand_id`, `demandId`, `nid`). An event with
a blank `Entity id` cannot be counted per demand, only as an event.

Source: `mp_clickstream_events` (Google Sheet, owner ekta.1@wheelseye.com).
Three tabs: **Glossary**, **Consigner App**, **Operator App**.

## Glossary

Empty in the source sheet as of 2026-09-23 — no field definitions have been
written yet. Read it first once it is populated.

## Consigner App

Grain: one row per (flow, screen, user action). 24 events, all Signup Flow.

| Flow / Feature Name | Describe Screen | Describe User Action | Event name | Event action | Event Category | Screen name | Demand_id | Entity id | Miscellaneous | user_code |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Signup Flow | Login/Signup | Impression | v1_offer_signup_screen | view |  | offer_screen | FALSE |  |  | FALSE |
| Signup Flow | Basic Details | Impression | v1_basic_details | view |  | sign_up_basic_details | FALSE |  |  | FALSE |
| Signup Flow | Basic Details | Clicks 'Name' field | v1_enter_name | click |  | sign_up_basic_details | FALSE |  |  | FALSE |
| Signup Flow | Basic Details | Clicks 'Sales Representative' field | v1_enter_salesrep | click |  | sign_up_basic_details | FALSE |  |  | FALSE |
| Signup Flow | Basic Details |  | v1_sales_contact | click |  | sign_up_basic_details | FALSE |  |  | FALSE |
| Signup Flow | Basic Details |  | v1_next | click |  | sign_up_basic_details | FALSE |  |  | FALSE |
| Signup Flow | Basic Details |  | v1_back | click |  | sign_up_basic_details | FALSE |  |  | FALSE |
| Signup Flow | Business Category |  | v1_business_category | view |  | sign_up_business_category | FALSE |  |  | FALSE |
| Signup Flow | Business Category |  | v1_next | click |  | sign_up_business_category | FALSE |  | business_category - id | FALSE |
| Signup Flow | Business Category |  | v1_previous | click |  | sign_up_business_category | FALSE |  |  | FALSE |
| Signup Flow | Business Category |  | v1_back | click |  | sign_up_business_category | FALSE |  |  | FALSE |
| Signup Flow | Trip Potential |  | v1_expected_trip_count | view |  | sign_up_expected_trip_count | FALSE |  |  | FALSE |
| Signup Flow | Trip Potential |  | v1_submit | click |  | sign_up_expected_trip_count | FALSE |  | expected_trip_count - id | FALSE |
| Signup Flow | Trip Potential |  | v1_previous | click |  | sign_up_expected_trip_count | FALSE |  |  | FALSE |
| Signup Flow | Trip Potential |  | v1_back | click |  | sign_up_expected_trip_count | FALSE |  |  | FALSE |
| Signup Flow | Trip Potential |  | v1_success_bottomsheet | view |  | sign_up_expected_trip_count | FALSE |  |  | FALSE |
| Signup Flow |  |  | v1_pricing_type | click | insurance_pricing | insurance | TRUE |  | type:fragile/non-fragile | FALSE |
| Signup Flow |  |  | v1_update_pricing | click | Insurance | `<dynamic_screen>` | TRUE |  |  | FALSE |
| Signup Flow |  |  | v1_view_pricing | click | Insurance | `<dynamic_screen>` | TRUE |  |  | FALSE |
| Signup Flow |  |  | v1_confim | click | update_ins_pricing | `<dynamic_screen>` | TRUE |  |  | FALSE |
| Signup Flow |  |  | v1_view_fragile | click | update_ins_pricing | `<dynamic_screen>` | TRUE |  |  | FALSE |
| Signup Flow |  |  | V1_close | click | update_ins_pricing | `<dynamic_screen>` | TRUE |  |  | FALSE |
| Signup Flow |  |  | v1_ok | click | update_ins_pricing | `<dynamic_screen>` | TRUE |  |  | FALSE |
| Signup Flow |  |  | v1_ok | click | fragile_items_list | `<dynamic_screen>` | TRUE |  |  | FALSE |

Note: `v1_confim` is spelt that way in the app — it is not a typo in this file.
`<dynamic_screen>` means the screen name varies at runtime.

## Operator App

Grain: one row per (journey, page, event). Covers the Demand Confirmation
and Bidding journeys. Rows tagged `[merged]` are shared
across the two journeys below.

Sheet convention: `Event name`, `Event action`, `Event Category` and
`Screen name` hold exact values as written by the app. `Miscellaneous` and
`Entity id` list only the key names and their meaning.

| Journey | Feature Description | Page Description | Event Description | Important Details | Event name | Event action | Event Category | Screen name | Miscellaneous | Entity id |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| [merged] Demand Confirmation Flow | [merged] After DR, notification for rate confirmation are being sent to eligible FO. And demand card is shown on Confirm Load page. This flow covers journey from Notification/Demand Card to Token payment | [merged] Overlay notification | Notification delivered | To identify exact event, notification id to be matched with fact_notification_history_s3 with filter notification_type="Booking Automation" | NotificationStatus | view |  |  | nid |  |
| [merged] Demand Confirmation Flow | [merged] As above | [merged] Overlay notification | Action taken on the notification | CONFIRM_BOOKING = click on Confirm; NEED_PROGRAM = click anywhere on notification; DISMISS = click on back button | NotificationAction | click |  |  | nid action |  |
| [merged] Demand Confirmation Flow | [merged] As above | [merged] Demand Card | Demand card viewed |  | v1_load_card | view | load_card | web_confirm_load | amount : Rate shown to FO; demand_index : Rank of card starting from 0 | demand_id |
| [merged] Demand Confirmation Flow | [merged] As above | [merged] Demand Card | Clicked on Demand Card |  | v1_load_confirm | click | load_card | web_confirm_load | entity : demand_id; freight : Rate shown to FO; demand_index : Rank of card starting from 0 |  |
| [merged] Demand Confirmation Flow | [merged] As above | [merged] Token Page | Token Page viewed |  | v1_load_confirmation | view |  | web_load_confirmation | conf_freight : Rate shown to FO | demandId |
| [merged] Demand Confirmation Flow | [merged] As above | [merged] Token Page | [merged] Token Paid clicked |  | v1_submit_btn | click | bottom_nav | web_load_confirmation | conf_freight : Rate shown to FO | demandId |
| [merged] Demand Confirmation Flow | [merged] As above | [merged] Token Page | [merged] Token Paid clicked | This is scroll button | v1_submit_btn | click | we_wallet_bottom_sheet | web_load_confirmation | conf_freight : Rate shown to FO | demandId |
| [merged] Bidding Flow | [merged] FO asked to quote their rate for demands. This flow covers journey from Notification/Demand Card to Token payment | [merged] Overlay notification | Notification delivered | To identify exact event, notification id to be matched with fact_notification_history_s3 with filter notification_type="Bidding" | NotificationStatus | view |  |  | nid |  |
| [merged] Bidding Flow | [merged] As above | [merged] Overlay notification | Action taken on the notification | CONFIRM_BOOKING = click on Confirm; NEED_PROGRAM = click anywhere on notification; DISMISS = click on back button | NotificationAction | click |  |  | nid action |  |
| [merged] Bidding Flow | [merged] As above | [merged] Demand Card | Demand card viewed |  | v1_load_card | view | load_card | web_confirm_load | amount : Always null value; demand_index : Rank of card starting from 0 | demand_id |
| [merged] Bidding Flow | [merged] As above | [merged] Demand Card | Clicked on Demand Card |  | v1_rate_and_confirm | click | load_cards | web_confirm_load | entity : demand_id; demand_index : Rank of card starting from 0 |  |
| [merged] Bidding Flow | [merged] As above | [merged] Bidding | Bidding Page viewed |  | v1_rate_and_confirm | view | rate_and_confirm | web_rate_and_confirm | conf_freight : Always null value | demandId |
| [merged] Bidding Flow | [merged] As above | [merged] Bidding | [merged] Rate edited |  | v1_plus | click | bottom_nav | web_rate_and_confirm |  | demand_id |
| [merged] Bidding Flow | [merged] As above | [merged] Bidding | [merged] Rate edited |  | v1_minus | click | bottom_nav | web_rate_and_confirm |  | demand_id |
| [merged] Bidding Flow | [merged] As above | [merged] Bidding | [merged] Token Paid clicked |  | v1_submit | click | bottom_nav | web_rate_and_confirm | conf_freight : Rate selected by FO; get_prob : % probability value shown to FO | demand_id |
| [merged] Bidding Flow | [merged] As above | [merged] Bidding | [merged] Token Paid clicked | This is scroll button | v1_submit_btn | click | we_wallet_bottom_sheet | web_load_confirmation | token_amt : Rate selected by FO | demandId |

Note: `v1_rate_and_confirm` appears twice with different meanings — as a
`click` on `web_confirm_load` (opening the bidding page) and as a `view` on
`web_rate_and_confirm` (the page itself). Always pair `event_name` with
`screen_name` and `event_action`; `event_name` alone is ambiguous.
