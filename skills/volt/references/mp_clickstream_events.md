# mp_clickstream_events

## Glossary

**Overview:** This sheet lists the clickstream event details for Markeplace related journeys on the consigner and operator apps/website

**How to read 'Consigner App' tab:** The below table lists all the fields, their meanings and the equivalent mapping names (can be used to join with similar fields in the 'mp_analytics_core.fact_cx_events_l3m' table)
The fields 'Flow/ Feature Name', 'Describe Screen', 'Describe Action','Critical Step' are defined in this sheet to describe and classify the events and not present in any database table. The stakeholder's query should be mapped to these fields to find the right Flow/Feature name, Stages, Actions that the stakeholder is talking about.
The rest of the fields are present in the 'mp_analytics_core.fact_cx_events_l3m'  table

| Field | Description | Mapping Name |
| --- | --- | --- |
| Flow/ Feature Name | Defines the flow name or the feature name by which it is commonly addressed eg. Signup flow, Demand flow, VIP Pass feature |  |
| Describe Stage | Defines the stage within the flow where the event gets triggerred |  |
| Describe Action | Defines the user/system actions within a stage that causes the event to trigger |  |
| Critical Step | Defines whether the 'Describe Action' is a critical step or not |  |
| Event name | Defines the name of the event. | eventname |
| Event action | Defines the action type:  Click or View | event_action |
| Event Category | Defines the event category | event_category |
| Screen name | Defines the screen name. This is not same as 'Describe Screen' field. | screen_name |
| Demand ID | Defines whether demand_id is populated on the given event or not | demand_id |
| Entity id | Defines the entity | entity_id |
| Miscellaneous | Defines the extra field which can contain additional metadata related to the event | miscellaneous |
| user_code | Defines whether user_code is populated on the given event or not | user_code |

## Consigner

| Flow/ Feature Name | Describe Screen | Describe Action | Critical Step | Event Name | Event Action | Event Category | Screen Name | Demand ID | Entity id | Miscellaneous | user_code | android_version | ios_version | web_version |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Signup | Promotions |  | False | v1_offer_signup_screen | view |  | offer_screen | False |  |  | True |  |  |  |
| Signup | Basic Details |  | True | v1_basic_details | view |  | sign_up_basic_details | False |  |  | True |  |  |  |
| Signup | Basic Details | Clicks 'Name' field | False | v1_enter_name | click |  | sign_up_basic_details | False |  |  | True |  |  |  |
| Signup | Basic Details | Clicks 'Sales Representative' field | False | v1_enter_salesrep | click |  | sign_up_basic_details | False |  |  | True |  |  |  |
| Signup | Basic Details | Clicks 'Sales Representative' field | False | v1_sales_contact | click |  | sign_up_basic_details | False |  |  | True |  |  |  |
| Signup | Basic Details | Clicks 'Next' button | False | v1_next | click |  | sign_up_basic_details | False |  |  | True |  |  |  |
| Signup | Basic Details | Clicks 'Back' arrow | False | v1_back | click |  | sign_up_basic_details | False |  |  | True |  |  |  |
| Signup | Business Category |  | True | v1_business_category | view |  | sign_up_business_category | False |  |  | True |  |  |  |
| Signup | Business Category | Clicks 'Next' button | False | v1_next | click |  | sign_up_business_category | False |  | business_category - id | True |  |  |  |
| Signup | Business Category | Clicks 'Previous' button | False | v1_previous | click |  | sign_up_business_category | False |  |  | True |  |  |  |
| Signup | Business Category | Clicks 'Back' arrow | False | v1_back | click |  | sign_up_business_category | False |  |  | True |  |  |  |
| Signup | Trip Potential |  | True | v1_expected_trip_count | view |  | sign_up_expected_trip_count | False |  |  | True |  |  |  |
| Signup | Trip Potential | Clicks 'Submit' button | False | v1_submit | click |  | sign_up_expected_trip_count | False |  | expected_trip_count- id | True |  |  |  |
| Signup | Trip Potential | Clicks 'Previous' button | False | v1_previous | click |  | sign_up_expected_trip_count | False |  |  | True |  |  |  |
| Signup | Trip Potential | Clicks 'Back' arrow | False | v1_back | click |  | sign_up_expected_trip_count | False |  |  | True |  |  |  |
| Signup | Success |  | True | v1_success_bottomsheet | view |  | sign_up_expected_trip_count | False |  |  | True |  |  |  |
| Signup | Insurance Opt in |  | False | v1_pricing_type | click | insurance_pricing | insurance | True |  | type:fragile/non-fragile | False |  |  |  |
| Signup | Insurance Opt in |  | False | v1_update_pricing | click | Insurance | <dynamic_screen> | True |  |  | False |  |  |  |
| Signup | Insurance Opt in |  | False | v1_view_pricing | click | Insurance | <dynamic_screen> | True |  |  | False |  |  |  |
| Signup | Insurance Opt in |  | False | v1_confim | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |  |  |  |
| Signup | Insurance Opt in |  | False | v1_view_fragile | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |  |  |  |
| Signup | Insurance Opt in |  | False | V1_close | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |  |  |  |
| Signup | Insurance Opt in |  | False | v1_ok | click | update_ins_pricing | <dynamic_screen> | True |  |  | False |  |  |  |
| Signup | Insurance Opt in |  | False | v1_ok | click | fragile_items_list | <dynamic_screen> | True |  |  | False |  |  |  |
| Browsing | Enter Tonnage |  | False | v1_tonnage | view |  | tonnage_req_v1 | False |  |  | False |  |  |  |
| Browsing | Enter Tonnage | Enters tonnage | False | v1_input_wt | click |  | tonnage_req_v1 | False |  |  | False |  |  |  |
| Browsing | Enter Tonnage | Chooses tonnage option | False | v1_choose_wt | click |  | tonnage_req_v1 | False |  |  | False |  |  |  |
| Browsing | Enter Tonnage | Clicks 'I don't know my material weight' | False | v1_dont_know_wt | click |  | tonnage_req_v1 | False |  |  | False |  |  |  |
| Browsing | Enter Tonnage | Clicks 'Submit' | False | v1_submit | click |  | tonnage_req_v1 | False |  | wt | False |  |  |  |
| Browsing | Enter Tonnage | Clicks 'Back' arrow | False | v1_back | click | top_nav | tonnage_req_v1 | False |  |  | False |  |  |  |
| Browsing | Enter Tonnage | Clicks 'Edit' button | False | v1_edit_add | click | top_nav | tonnage_req_v1 | False |  |  | False |  |  |  |
| Browsing | Enter Tonnage | Clicks 'Add loading' button | False | v1_add_loading | click | top_nav | tonnage_req_v1 | False |  |  | False |  |  |  |
| Browsing | Enter Tonnage | Clicks 'Add unloading' button | False | v1_add_unloading | click | top_nav | tonnage_req_v1 | False |  |  | False |  |  |  |
| Browsing | VT Browsing |  | False | v1_veh_options | view |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks 'Enter weight' button | False | v1_enter_wt | click |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks 'Open/Container/Trailer' options | False | v1_body_type | click |  | tonnage_req | False |  | 0 : Open; <br>1 : Container, <br>2 : Trailer | False |  |  |  |
| Browsing | VT Browsing | Clicks any VT card | False | v1_veh_opted | click |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks 'height' option | False | v1_height | click |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks  any special request choice | False | v1_spcl_req | click |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks 'Confirm <VT>' | False | v1_cnf_veh | click |  | tonnage_req | False |  | chosen option index | False |  |  |  |
| Browsing | VT Browsing |  | False | v1_spcl_req_bottomsheet | view |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks 'Okay, Got it' button | False | v1_continue | click | special_req_bottomsheet | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing |  | False | v1_scroll | view |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing |  | False | v1_veh_unavailable | view |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks 'Change Tonnage' | False | v1_change_tonnage | click |  | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing |  | False | v1_wt_bottomsheet | view | enter_wt_bottomsheet | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks tonnage in 'Select weight of your goods' | False | v1_enter_wt | click | enter_wt_bottomsheet | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks tonnage option | False | v1_choose_wt | click | enter_wt_bottomsheet | tonnage_req | False |  |  | False |  |  |  |
| Browsing | VT Browsing | Clicks 'Submit' | False | v1_cnf_wt | click | enter_wt_bottomsheet | tonnage_req | False |  | weight | False |  |  |  |
| Browsing | VT Browsing | Clicks 'Close' button | False | v1_close | click | enter_wt_bottomsheet | tonnage_req | False |  |  | False |  |  |  |
| Demand |  | Demand Created | False | v1_demand_price_range(view)(misc : demandid) | view |  | demand_price_range | False |  |  | False |  |  |  |
| Demand |  | Demand Confirmed (DR) | False | v1_back_btn | click |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False | v1_cancel | click |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False | v1_edit_add | click |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False | v1_edit_veh | click |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False | v1_price_range | view |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False | v1_mode | click |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False | v1_confirm_btn(click)(misc: mode:quick_confirmation/best_price) | click |  | demand_price_range | True |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  | demand_price_range | False |  |  | False |  |  |  |
| Price Confirmation |  | Final Price Given | False |  |  |  |  | False |  |  | False |  |  |  |
| Price Confirmation |  | Price Accepted | False |  |  |  |  | False |  |  | False |  |  |  |
| Fulfilment |  | At Loading | False |  |  |  |  | False |  |  | False |  |  |  |
| Fulfilment |  | Trip Started | False |  |  |  |  | False |  |  | False |  |  |  |
| Fulfilment |  | At Unloading | False |  |  |  |  | False |  |  | False |  |  |  |
| Fulfilment |  | Trip Completed | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |
|  |  |  | False |  |  |  |  | False |  |  | False |  |  |  |

## Operator

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
