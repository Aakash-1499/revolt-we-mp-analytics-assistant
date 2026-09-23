# mp_ods_documentation

## 1_fact_operators_mp_events

mp_analytics_core.fact_operators_mp_events

**Owner:** Aakash / Mohit

**Grain:** Operator_code, event_date

**Short description:** This table captures daily activity summary of the operators from landing to trip. Eg. # of loads checked, # of bids placed / # of tokens paid / # of completed trips, plus lifetime cumulative metrics (life_time_trips, plc_till_date) and dimensions like fleet_size, fo_segment, fo_sub_type. Used for FO daily activation, engagement funnel, and supply-side cohort analysis.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization |
| --- | --- | --- | --- | --- |
| 1 | event_date | Calendar date of the event (or timestamp when the event occurred). | 2025-03-30T18:30:00.000Z | — |
| 2 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE3987982 | — |
| 3 | landed_on_mp | 1 if the FO landed on the our app ; 0 otherwise. | 1 | — |
| 4 | is_checked_loads | 1 if the FO checked at least one load on this day; 0 otherwise (operator-day grain). | 1 | — |
| 5 | is_checked_loads_matching | 1 if the FO checked at least one load in the matching flow on this day. | 0 | — |
| 6 | is_checked_loads_bid | 1 if the FO checked at least one load in the bidding flow on this day. | 0 | — |
| 7 | is_landed_on_bid | 1 if the FO landed on the bidding screen on this day. | 0 | — |
| 8 | is_landed_on_confirm | 1 if the FO landed on the booking confirmation screen on this day. | 0 | — |
| 9 | is_marked_veh_available | 1 if the FO marked their vehicle as 'available' on this day. | 0 | — |
| 10 | is_marked_veh_not_available | 1 if the FO marked their vehicle as 'NOT available' on this day. | 0 | — |
| 11 | is_loading_filter_used | 1 if the FO used the loading-location filter on this day. | 0 | — |
| 12 | is_unloading_filter_used | 1 if the FO used the unloading-location filter on this day. | 0 | — |
| 13 | is_matching_submit | 1 if the FO submitted a matching response on this day. | 0 | — |
| 14 | count_of_loads_checked | Number of distinct loads the FO checked on this day. | 0 | — |
| 15 | count_of_loads_bid_submit | Number of bids the FO submitted on this day. | 0 | — |
| 16 | count_of_loads_matching_submit | Do not use | 0 | — |
| 17 | is_matching_submit_loads | Mohit Kumar | 0 | — |
| 18 | is_token_paid | 1 if the FO paid the booking token on this day. | 0 | — |
| 19 | is_token_paid_loads | Count of token paid on that day | 0 | — |
| 20 | is_subscribed_at_event | 1 if the FO had an active subscription at the time of the event. | 1 | — |
| 21 | total_placed_loads | Total loads on which the FO was placed on this day. | 100 | — |
| 22 | total_placed_loads_cancelled_by_cx | Of the placements this day, how many were subsequently cancelled by the consigner. | 0 | — |
| 23 | total_trips_loads | Total trips completed by the FO on this day. | 78 | — |
| 24 | reverse_loads_trips | Count of reverse-load (return-leg) trips completed by the FO on this day. | 0 | — |
| 25 | life_time_trips | Cumulative trips completed by the FO across their entire history on the marketplace. | 84 | — |
| 26 | fleet_size | Fleet-size segment of the FO: SVO (Single Vehicle FO),SFO (Small FO), MFO (Multi-vehicle FO), LFO (Large FO),XLFO (Extra Large FO).<br>XLFO>=50<br>LFO-25-49,SFO 2-3,MFO 4-24 ,SVO 1 | SFO | — |
| 27 | fo_base_region | "(do not use this )" | NCR | — |
| 28 | first_trip_date | First Trip date of FO | 2022-10-03T12:04:04.649Z | ⚠ FIRST_TRIP_DATE — should be 'first_trip_date (NEEDS context prefix)' |
| 29 | trips_till_date | Cumulative trips up to and including this event date. | 78 | — |
| 30 | plc_till_date | Cumulative placements up to and including this event date. | 100 | — |
| 31 | token_till_date | Cumulative tokens paid up to and including this event date. | 103 | — |
| 32 | first_placement_date | Date the consigner where demand_status = 'FULFILLED' first time | 2022-10-02T18:30:00.000Z | — |
| 33 | life_time_placements | Cumulative placements the FO has received across their entire history. | 110 | — |
| 34 | trip_bucket | Bucketed FO lifetime trip count | 3+ | — |
| 35 | fo_segment | FO segment is the FO Trip segmentation , 0=0 trip, 1-2 = 1st trip or 2nd trip  and 2+ fo who have done more than 2+trip | 3+ | — |
| 36 | lifetime_loads_checked | Cumulative loads checked by the FO across their entire history. | 0 | — |
| 37 | fo_load_impressions | Bucketed count of load impressions or checking of load in lifetime for the FO (e.g., '0', '1-4', '5+'). | 0 | — |
| 38 | fo_sub_type | Subscription type / status: 'Subs' (subscribed)=1, 'Non-Subs',=0 | Subs | — |
| 39 | qualified_in_opsearch | 1 if the FO qualified in the opsearch (matching) algorithm for at least one demand on this day. | 0 | — |
| 40 | qualified_in_matching | 1 if the FO qualified in the matching engine for at least one demand on this day. | 0 | — |
| 41 | ready_fo | Marketplace readiness flag — 1 if the FO is MP Ready, 0 otherwise. | 0 | — |

## 2_fact_consigner_demands_lead_source

mp_analytics_core.fact_consigner_demands_lead_source

**Owner:** Ekta

**Grain:** login_date+consigner_user_code+app_platform

**Short description:** The MASTER FACT for Cx Growth: one row per (consigner_user_code × login_date × demand_id). For every demand a consigner created on a given login day, this captures consigner attributes (segment, region, sales team, potential, business category, lead source), demand attributes (route, vehicle type, origin/destination, pricing — base_price, ODVT, CODVT), funnel flags (dr_flag, plc_flag, trip_flag), pricing/supply confidence signals, and full sales attribution. Start here for almost any Cx Growth funnel analysis.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Descriptions | Sample value | ⚠ Standardization | col_6 |
| --- | --- | --- | --- | --- | --- |
| 1 | consigner_user_code | Unique identifier of a consigner (CX / customer). WheelsEye internal code, typically starts with 'WE'.<br>It depicts the Unique code assigned to the consigner | WE69409 | — |  |
| 2 | login_month | It defines the month when the consigner was active on the app | 2020-03-31T18:30:00.000Z | — |  |
| 4 | platform | App platform through whcih demand was created: App/Web | android | — |  |
| 5 | signup_date | Date the consigner signed up. | 2020-03-31T18:30:00.000Z | — |  |
| 6 | signup_week | It defines the week of the signup date | 2020-03-29T18:30:00.000Z | — |  |
| 7 | signup_month | It defines the month of the signup date | 2020-03-31T18:30:00.000Z | — |  |
| 8 | demand_time | Exact timestamp when the demand was created. | 2020-04-01T10:33:20.092Z | — |  |
| 9 | demand_date | Date the demand was created (day-truncated from demand_time). | 2020-03-31T18:30:00.000Z | — |  |
| 10 | demand_week | Week-start timestamp of the demand. | 2020-03-29T18:30:00.000Z | — |  |
| 11 | demand_month | It depicts the Month in which demand was created | 2020-03-31T18:30:00.000Z | — |  |
| 12 | sales_team | The sales team that was aligned with the consigner at a given point of time | NOT ASSIGNED | — |  |
| 13 | sales_sub_team | The sales sub team that was aligned with the consigner at a given point of time | NOT ASSIGNED | — |  |
| 17 | demand_id | Unique identifier of a demand created by a consigner. | 2006163 | — |  |
| 18 | dr_flag | Indicates if a Details Required (DR) was given by consigner <br>(1 = Yes, 0 = No) | 0 | — |  |
| 19 | plc_flag | Indicates if demand was placed with a vehicle (1 = Yes, 0 = No) | 0 | — |  |
| 20 | trip_flag | Indicates if the demand resulted in a trip (1 = Yes, 0 = No) | 0 | — |  |
| 21 | demand_restriction | This defines the status of the consigner at the time of demand creation<br>Restricted<br>Unrestricted | Unrestricted | — |  |
| 22 | dr_restriction | It depicts whether the consigner is allowed to give DR or not based upon its previous balance clearance <br>It can have the following values ( restricted / unrestricted ) | Unrestricted | — |  |
| 25 | trip_rank | Rank of this demand within the consigner's trip history (1 = first trip, etc.). | 1 | — | ? |
| 26 | active_cx_trip_rank | Rank of consigner's trip which resets if the consigner becomes dormant | 0 | — | ? |
| 27 | latest_acq_time | Timestamp of the latest 'acquisition' event for the consigner | 2020-03-18T15:21:39.918Z | — | It is 1st demand time where trip_flag =1 for that consignor |
| 29 | cx_segment | Consigner trip-bucket segment: 'New' (0 trips), '1-4' (1-4 lifetime trips), '4+' (4+ trips) | 1-4 | — |  |
| 31 | auto_plc | 'YES' / 'NO' — whether the placement was done automatically by the system (vs. manually by ops). | NO | — |  |
| 35 | app_version | App version at the time of the event. | (NULL) | — |  |
| 36 | demand_region | Demand origin region | OTHERS | — |  |
| 37 | demand_state | State of the demand's origin. | DELHI NCR | — |  |
| 38 | demand_city | City of the demand's origin. |  | — |  |
| 39 | demand_cluster | Demand origin cluster | NOT AVAILABLE | — |  |
| 42 | destination_id | District id of the demand's destination. Joined with id in mp_analytics_core.dim_mp_districts | (NULL) | — |  |
| 43 | destination_cluster_id | Cluster id of the demand's destination. Derived from mp_analytics_core.dim_mp_districts. | (NULL) | — |  |
| 44 | destination_region | Demand destination id | OTHERS | — |  |
| 46 | destination_city | City of the demand's destination. | (NULL) | — |  |
| 47 | destination_cluster | Cluster of the demand's destination. Derived from mp_analytics_core.dim_mp_districts. | OTHERS | — |  |
| 48 | vt_id | <missing in Glossary> | (NULL) | — |  |
| 49 | vt_pricing_id | <missing in Glossary> | (NULL) | — | ? |
| 50 | cod | Combination of Consigner_user_code,Demand_date,Origin_id,Destination_id | (NULL) | — |  |
| 51 | codvt | Combination of Consigner_user_code,Demand_date,Origin_id,Destination_id,vehicle_type_id | (NULL) | — |  |
| 52 | codvt_pricing | Do Not Use | (NULL) | — | ? |
| 55 | base_price | Supply fare with our margin ('Middle Share') which should have been shown to the consignor in case there is zero non-coupon discount applicable. | (NULL) | — | ? |
| 56 | base_rate1 | This is the lower end of the price range shown to the consigner before we start searching for the vehicle. It is derived by multiplying base_rate2 with a factor which might vary across ODVTs. | (NULL) | — | ? |
| 57 | base_rate2 | This is the predicted consigner freight fare for the given ODVT.<br>It is derived by multiplying supply_l2 (predicted supply_fare for the given ODVT by our pricing model) with a factor which might vary across ODVTs. | (NULL) | — | ? |
| 58 | base_rate3 | This is the upper end of the price range shown to the consigner before we start searching for the vehicle. It is derived by multiplying base_rate2 with a factor which might vary across ODVTs. | (NULL) | — | ? |
| 61 | consigner_freight_fare | Final freight fare quoted to the consigner (₹). | (NULL) | — | ? |
| 63 | cx_plc_cancel_time | Timestamp when placement was cancelled by consigner | (NULL) | — |  |
| 64 | ccvt_fo | <missing in Glossary> | (NULL) | — | ? |
| 74 | consigner_city | Do Not Use | NOT AVAILABLE | — | ? |
| 75 | consigner_state | It depicts the state of the consigner | NOT AVAILABLE | — | ? |
| 76 | consigner_region | Consigner's resolved region (sales geography region).<br>It depicts the region of the consigner and can have three values :<br>Not Available-when the consigner location is not available <br>NCR-when the consigner is from NCR region <br>ROI-when the consigner is from rest of india or not from NCR<br>New Serviceable | NEW SERVICEABLE | — |  |
| 77 | consigner_state_segment | Consigner's state-level segment classification (sales geography segmentation).<br>Consigner region is extracted from the very first source in this priority - FIELD SALES>SIGNUP>VT>DEMAND>WEB | NOT AVAILABLE | — | DNU |
| 83 | original_lead_source_detailed | This defines the first source of any given lead: <br>App (Organic)<br>App (Paid)<br>Cold Visit<br>Web (Organic)<br>Web (Paid)<br>Others | App (Organic) | — |  |
| 84 | utm_source | UTM parameter for campaign tracking (source) |  | — |  |
| 85 | latest_lead_source_detailed | This defines the latest source of any given lead: <br>App (Organic)<br>App (Paid)<br>Cold Visit<br>Web (Organic)<br>Web (Paid)<br>Others | App (Organic) | — | DNU |
| 87 | assigned_sales_team | The current sales team aligned with the consigner: <br>FIELD SALES<br>INSIDE SALES<br>NOT ASSIGNED | INSIDE SALES | — |  |
| 88 | assigned_sales_sub_team | The current sales sub team aligned with the consigner: <br>ONBOARDING<br>RETENTION<br>NOT ASSIGNED | RETENTION | — |  |
| 89 | relevant_sales_team | Do Not Use | NOT ASSIGNED | — | DNU |
| 90 | cx_potential | Consigner Potential as provided by Sales team | NOT AVAILABLE | — |  |
| 91 | cx_business_category | Business Category provided by user during signup like<br>MANUFACTURER, TRADER, INDIVIDUAL, SERVICE PROVIDER, etc. | NOT AVAILABLE | — |  |
| 97 | app_potential | Trip potential provided by user during signup | (NULL) | — |  |
| 98 | body_type | Body type of the vehicle (e.g., 'Open', 'Container', 'Trailer'). | UNKNOWN | — |  |
| 99 | login_date | Day-truncated login timestamp. Granularity of the (consigner_user_code × login_date × demand_id) primary key — i.e., one row per day the consigner was active.<br>Used to get Daily Active Users (DAU), Monthly Active Users (MAU), etc. |  | — | DNU |
|  | sales_state | DO NOT USE |  | ⚠ SALES_STATE — should be 'sales_state' | DNU |
|  | sales_city | DO NOT USE |  | ⚠ SALES_CITY — should be 'sales_city' | DNU |
|  | sales_cluster | DO NOT USE |  | — | DNU |
|  | placement_rn | DO NOT USE |  | — | DNU |
|  | placement_rank | Sequence of trips for a user (ONLY for fulfilled demands)<br> Counts successful trips only<br> Ignores non-trip demands (sets them to 0) |  | — |  |
|  | last_trip_time | Timestamp of the consigner's most recent completed trip prior to (or as of) this demand |  | — |  |
|  | dr_type | DO NOT USE |  | — |  |
|  | route_distance | Origin → destination route distance (km). Used as a filter (min_distance / max_distance) on the Placement and FO dashboards and to derive 'haul'. |  | — |  |
|  | tyre | Tyre count of the requested vehicle on the demand.  [Same data as 'tyre_count' in fact_vehicle_info — STANDARDIZE naming] |  | ⚠ TYRE_COUNT — should be 'tyre_count' |  |
|  | origin_id | District id of the demand's origin. Joined with id in mp_analytics_core.dim_mp_districts |  | — |  |
|  | origin_cluster_id | Cluster id of the demand's origin. Derived from mp_analytics_core.dim_mp_districts. |  | — | DNU |
|  | destination_state |  |  | — | DNU |
|  | odvt | Origin × Destination × Vehicle Type key (pricing dimension WITHOUT the consigner). Combination of origin_id, destination_id, vehicle_type_id. |  | — |  |
|  | odvt_pricing | DO NOT USE |  | — | DNU |
|  | pnl | Realised net P&L on the demand (₹). Net of cost components. Used as numerator for % Net Take Rate. |  | — |  |
|  | pnl_expected | Expected (pre-cost) P&L on the demand (₹). Used as numerator for % Gross Take Rate. |  | — |  |
|  | time_to_plc | Time in minutes between DR creation and the final placement on the demand. Used in '% DR to Plc (≤ L2 and ≤ 90 min)' metric. |  | — |  |
|  | opsearch_fo | Flag/count for FOs returned by the OpSearch (matching) algorithm for this demand. Used in North Star OpSearch-FO bucketing. |  | — | DNU |
|  | supply_confidence | Do Not Use |  | — | DNU |
|  | price_confidence | Do Not Use |  | — | DNU |
|  | plc_price_range | Bucket label for the consigner fare vs base rate 1,2,3 |  | — |  |
|  | haul | Haul type derived from route_distance (e.g., 'Short Haul', 'Long Haul','Medium Haul') |  | — |  |
|  | dr_time | Timestamp when the demand became a DR (Details Required) — i.e., entered the supply matching pipeline. |  | — |  |
|  | first_plc_time | Timestamp of the first placement event on the demand |  | — |  |
|  | last_plc_time | Timestamp of the most recent placement event on the demand |  | — |  |
|  | total_plc | DO NOT USE |  | — |  |
|  | prospectid | Prospect / lead ID linked to the consigner before they became a registered consigner_user_code (pre-signup identifier). |  | — |  |
|  | prospect_id_created_time | Timestamp when the prospect record was first created. |  | — |  |
|  | prospect_id_created_date | Date when the prospect record was first created. |  | — |  |
|  | prospect_id_created_week | Week-start of the prospect's creation date. |  | — |  |
|  | prospect_id_created_month | Month-start of the prospect's creation date. |  | — |  |
|  | latest_utm_source | <missing in Glossary> |  | — |  |
|  | first_sales_team | Sales team prospect was assigned to the first time: INSIDE SALES, FIELD SALES, etc. |  | — | DNU |
|  | first_sales_sub_team | Sales sub team prospect was assigned to the first time: RETENTION, ONBOARDING, etc. |  | — | DNU |
|  | first_sales_team_time | DO NOT USE |  | — | DNU |
|  | first_sales_team_date | DO NOT USE |  | — | DNU |
|  | last_updated_date | Timestamp of the most recent ETL refresh of this row. Operational column. |  | — |  |

## 3_dim_operator_base_district

mp_analytics_core.dim_operator_base_district

**Owner:** Gajinder

**Grain:** operator_code

**Short description:** This tabe contains fleet operator base location information at district level. Corresponding to district cluster is also mentioned.
District name and cluster name can be identified using table anaytics.dim_mp_districts

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization |
| --- | --- | --- | --- | --- |
| 1 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE1000021 | — |
| 5 | district_id | Integer ID of a district. Joinable via dim_mp_districts. | 21 | — |
| 6 | cluster_id | Integer ID of a geographic cluster .Joinable via dim_mp_districts. | 21 | — |

## 4_fact_vehicle_info

**mp_analytics_core.fact_vehicle_info:** Owner

**Gajinder:** Grain

**operator_code * vehicle_id:** Short description

Consider this GPS master data. This serves as base for marketplace as only GPS operators can be converted to Marketplace operators.
This table captures operator_code, the vehicle registration number, body type, tyre count, size, tonnage, vehicle category, and onboarding / deboarding dates, and vehicle category.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization |
| --- | --- | --- | --- | --- |
| 1 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE123741 | — |
| 2 | vehicle_id | Unique internal identifier of a specific vehicle in the WheelsEye system. | 3533241 | — |
| 3 | vehicle_number | Vehicle registration / number plate (RTO number). | HR35X3108 | — |
| 4 | live_date | Date a vehicle went live on the GPS | 2025-05-24T07:04:13.000Z | — |
| 5 | deboarding_date | Date a vehicle was deboarded from the GPS | (NULL) | — |
| 6 | body_type | Body type of the vehicle (e.g., 'Open', 'Container', 'Trailer'). | Not Known | — |
| 7 | tyre_count | Tyre count of the specific vehicle.  [Same data as 'tyre' in fact_consigner_demands_lead_source — STANDARDIZE naming] | 0 | ⚠ TYRE_COUNT — should be 'tyre_count' |
| 8 | size_in_ft | Vehicle size in feet (length of the cargo body). | 0 | — |
| 9 | tonnage | Vehicle tonnage capacity in metric tons. | 0 | — |
| 10 | pricing_vt_id | Unique identifier of VT description aling with pricing logics. Joined with mp_analytics_core.dim_pricing_vt | -1 | — |
| 11 | supply_vt_id | Vehicle type ID — canonical identifier combining body type, size, and tyre count. Joined with mp_analytics_core.fact_demand_vt | -1 | — |
| 12 | vehicle_category | Coarse vehicle category code (e.g., 'LMV', 'HMV'). | LMV | — |
| 13 | vehicle_category_desc | Detailed description of the vehicle category (e.g., 'Agricultural Tractor(LMV)'). | Agricultural Tractor(LMV) | — |
| 14 | vehicle_class | Vehicle class code (more specific than category, e.g., 'TRUCK'). | TRACTOR_AGRICULTURE | — |

## 5_fact_operators_onb

**mp_analytics_core.fact_operators_onb:** Owner

**Mohit:** Grain

**operator_code:** Short description

Operator onboarding / readiness fact. One row per operator capturing their subscription date, marketplace-ready date, current MP status (MP Ready / Not Ready), and flags indicating whether they have completed key readiness steps (has_sub, has_vt, has_preferred_state). Used to track the FO activation funnel from signup to marketplace-ready.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization |
| --- | --- | --- | --- | --- |
| 1 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE212659 | — |
| 2 | sub_date | Date the operator subscribed (took a paid plan). NULL if never subscribed. | (NULL) | — |
| 3 | ready_date | Date the operator became 'MP Ready' (all readiness criteria met). | 2020-07-05T18:30:00.000Z | — |
| 4 | mp_status | Marketplace status of the FO: 'MP Ready', 'MP Not Ready', etc. | MP Ready | — |
| 5 | has_sub | 1 if the operator has an active subscription. (String '0'/'1' in onboarding table.) | 1 | — |
| 6 | has_vt | 1 if the operator has at least one vehicle type registered. | 1 | — |
| 7 | has_preferred_state | 1 if the operator has set a preferred operating state. | 1 | — |
| 8 | readiness_source | Source of the operator readiness data — e.g., 'Self Input Attributes', 'Ops Verified'. | Self Input Attributes | — |

## 6_fact_demand_opsearch_summary

mp_analytics_core.fact_demand_opsearch_summary

**Owner:** Gajinder

**Grain:** demand_id

**Short description:** Aggregate table built on mp_analytics.fact_demand_fo_opsearch. For each demand, counts FOs from the opsearch output meeting various qualification thresholds (score, distance, subscription, availability, VT match, notification readiness). Used to evaluate supply depth and opsearch funnel quality per demand.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization |
| --- | --- | --- | --- | --- |
| 1 | demandid | Unique identifier of a demand (indent / freight request) created by a consigner.<br>Commonly refer as demand_id | 4039447 | — |
| 2 | demand_date | Date the demand was created (day-truncated from demand_time). | 2026-01-05 | — |
| 3 | total_operators | Total FOs returned by opsearch within 120km of demand origin. | 1230 | — |
| 4 | more_than_10l | Count of FOs with opsearch score > 10 lakh. | 111 | — |
| 5 | more_than_20l | Count of FOs with opsearch score > 20 lakh. | 81 | — |
| 6 | more_than_10l_and_60km | Count of FOs with score > 10L and within 60km of demand origin. | 90 | — |
| 7 | more_than_20l_and_60km | Count of FOs with score > 20L and within 60km of demand origin. | 62 | — |
| 8 | sub_operators | Count of subscribed FOs in the opsearch list. | 288 | — |
| 9 | nonsub_operators | Count of non-subscribed FOs in the opsearch list. | 942 | — |
| 10 | sub_more_than_10l | Count of subscribed FOs with opsearch score > 10L. | 82 | — |
| 11 | sub_more_than_20l | Count of subscribed FOs with opsearch score > 20L. | 68 | — |
| 12 | sub_more_than_10l_and_60km | Count of subscribed FOs with score > 10L and within 60km. | 62 | — |
| 13 | sub_more_than_20l_and_60km | Count of subscribed FOs with score > 20L and within 60km. | 49 | — |
| 14 | available_operators | Count of FOs with at least one vehicle marked available. | 30 | — |
| 15 | sub_available_operators | Count of subscribed FOs with vehicle available. | 30 | — |
| 16 | nonsub_available_operators | Count of non-subscribed FOs with vehicle available. | 0 | — |
| 17 | va_operators | Count of FOs with a matching vehicle type available. | 30 | — |
| 18 | sub_va_operators | Count of subscribed FOs with matching VT available. | 30 | — |
| 19 | nonsub_va_operators | Count of non-subscribed FOs with matching VT available. | 0 | — |
| 20 | ready_va_operators | Count of MP-ready FOs with matching VT available. | 24 | — |
| 21 | sub_ready_va_operators | Count of subscribed MP-ready FOs with matching VT available. | 24 | — |
| 22 | nonsub_ready_va_operators | Count of non-subscribed MP-ready FOs with matching VT available. | 0 | — |
| 23 | matching_qualified_operators | Count of FOs qualified for notification by the matching engine. | 0 | — |
| 24 | sub_matching_qualified_operators | Count of subscribed FOs qualified for notification. | 0 | — |
| 25 | nonsub_matching_qualified_operators | Count of non-subscribed FOs qualified for notification. | 0 | — |
| 26 | sub_available_matching_qualified_operators | Count of subscribed, available FOs qualified for notification. | 0 | — |
| 27 | sub_va_matching_qualified_operators | Count of subscribed FOs with matching VT that qualified for notification. | 0 | — |

## 7_fact_demand_opsearch_operator_summary

mp_analytics_core.fact_demand_opsearch_operator_summary

**Owner:** Gajinder

**Grain:** demand_id, operator_code

**Short description:** Stores the output of the opsearch model at demand × operator grain. The model determines probability of each operator within 120km of demand origin fulfilling it. Only saves top operators (predetermined count). Used to evaluate per-operator supply probability and notification eligibility.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization |
| --- | --- | --- | --- | --- |
| 1 | demandid | Unique identifier of a demand (indent / freight request) created by a consigner.<br>Commonly refer as demand_id | 4508793 | — |
| 2 | demand_date | Date the demand was created (day-truncated from demand_time). | 2026-05-25 11:31:00 | — |
| 3 | opcode | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'.<br>Commonly refer as operator_code | WE3506795 | operator_code |
| 4 | totalscore | This is model score and refered as probability of operator to place vehicle. | 3394.1 | — |
| 5 | distance | Distance between operator and demand origin. | 23.81 | — |
| 6 | latest_opsearch_date | Datetime at which latest opsearch executed wrt demand_id.<br>Opsearchruns again in case of backout. | 2026-05-25 11:31:00 | — |
| 7 | opsearch_rnk | Rank of operator in opsearch on the basis of opsearch score. | 1331 | — |
| 8 | subscription_status | Operator subsction status.<br>1 = Subscribed<br>0 = Not Subscribed | 1 | — |
| 9 | fo_availability | Opeator's any vehicle is available for the day when opsearch executed<br>1 = Available<br>0 = Not Available | 0 | — |
| 10 | veh_availability | Opeator's any vehicle matching with requested VT is available for the day when opsearch executed<br>1 = Available<br>0 = Not Available | 0 | — |
| 11 | matching_qualified | Operator is qualified for notification<br>1 = Notification will be sent<br>0 = Notification will not be sent | 0 | — |

## 8_fact_operator_tokens

**mp_analytics_core.fact_operator_tokens:** Owner

**Gajinder:** Grain

**demand_id, operator_code:** Short description

Stores bids submitted by operators. Data is valid only if opfreight column is not empty.
Entry is created when operator enters bid amount. After the bid, next step is to pay token amount and give vehicle details.
After valid vehicle details are given, the bid is valid for placement.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization |
| --- | --- | --- | --- | --- |
| 1 | id | Unique identifier of a demand (indent / freight request) created by a consigner.<br>Commonly refer as demand_id | 785095465 | — |
| 2 | created | It is datetime when bid is submitted | 2026-06-20 07:11:00 | — |
| 3 | updated | DO NOT USE | 2026-06-20 07:20:00 | — |
| 4 | deleted | DO NOT USE | false | — |
| 5 | demand_id | Unique identifier of a demand created by a consigner. | 4605454 | — |
| 6 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE4629721 | — |
| 7 | status | This refers token status againt bid submitted.<br>INITIATED = Bid is submitted but token is not paid.<br>SUCCESS = Token is paid<br>REFUNDED = Token is paid and is refunded back after token is not converted to trip.<br>FORFEITED = Token is paid and win the bidding, but operator backout from trip.<br>EXPIRED = Bid is expired due to no token paid | REFUNDED | — |
| 8 | opfreight | Bid value submitted by operator | 16800 | — |
| 9 | amount_in_paisa | Token amount needed to submit. This amount stored in paisa denomination. | 19900 | — |
| 10 | refund_amount_in_paisa | Token amount refunded. This amount stored in paisa denomination and is valid for REFUNDED status only. | 19900 | — |
| 11 | trigger_source | This refers to mode the bid is given.<br>TESSERACT_SERVICE = Operator bid via visiting app directly or via notification.<br>MANUAL = Operator bid on notification sent manually by ops. | TESSERACT_SERVICE | — |
| 12 | transaction_code | It is payment transaction code for token paid | WEWLTTXN610E3B... | — |
| 13 | refund_transaction_code | It is payment transaction code for refunded token. | WEWLTTXN58F279... | — |
| 14 | bidding_type | <missing in Glossary Do not Use> | TEST_B0 | — |
| 15 | auction_type | <missing in Glossary, Do not Use> | 0 | — |
| 16 | flow | This refers to operator opting to pay at price shown or give his own price.<br>MATCHING = Opt for shown price<br>BIDDING = Opt to give his own bid | BIDDING | — |
| 17 | token_paid_time | it is datetime when taoken amount is paid | 2026-06-20 00:00:00 | — |
| 18 | vehicle_submitted_time | it is datetime when vehicle details given | 2026-06-20 00:00:00 | — |

## 9_fact_operators_demand_mp_events

mp_analytics_core.fact_operators_demand_mp_events

**Owner:** Aakash

**Grain:** operator_code, demand_id,event_date

**Short description:** FO engagement events aggregated at demand × operator level x event_date. Captures whether a specific FO checked, bid, matched, paid token, was placed, or completed a trip on each demand. Demand-level complement to fact_operators_mp_events (day-level). Used for per-demand FO funnel analysis.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization |
| --- | --- | --- | --- | --- |
| 1 | demand_id | Unique identifier of a demand created by a consigner. | 4605454 | — |
| 2 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE4629721 | — |
| 3 | event_date | Calendar date of the event (or timestamp when the event occurred). | 2025-09-01 | — |
| 4 | is_load_checked | 1 if the FO checked this specific demand load; 0 otherwise (demand-level, cf. is_checked_loads which is day-level). | 1 | — |
| 5 | is_bid_submitted | Do Not Use | 0 | — |
| 6 | is_matching_submit | Do Not Use | 1 | — |
| 7 | is_token_paid | Do Not Use | 0 | — |
| 8 | is_placed | Do Not Use | 0 | — |
| 9 | is_cancelled_by_cx | Do Not Use | 0 | — |
| 10 | is_trip | Do Not Use | 0 | — |
| 11 | landed_on_mp | Do Not Use | 1 | — |
| 12 | is_landed_on_bid | Do Not Use | 0 | — |
| 13 | is_landed_on_confirm | Do Not Use | 0 | — |
| 14 | is_marked_veh_available | Do Not Use | 0 | — |
| 15 | is_marked_veh_not_available | Do Not Use | 0 | — |
| 16 | is_loading_filter_used | Do Not Use | 0 | — |
| 17 | is_unloading_filter_used | Do Not Use | 0 | — |
| 18 | is_subscribed_at_event | Do Not Use | 1 | — |
| 19 | has_rate_card | Do Not Use | 1 | — |
| 20 | rate_card_collected_date | Do Not Use | 2025-08-01 | — |
| 21 | verified_vehicles | Do Not Use | 2 | — |
| 22 | life_time_trips | Do Not Use | 12 | — |
| 23 | trip_bucket | Do Not Use | 2+ | — |
| 24 | fleet_size | Do Not Use | SFO | — |
| 25 | fo_district | Do Not Use | GURUGRAM | — |
| 26 | district_id | Do Not Use | 21 | — |
| 27 | cluster_id | Do Not Use | 5 | — |
| 28 | fo_base_district | Do Not Use | GURUGRAM | — |
| 29 | fo_base_state | Do Not Use | HARYANA | — |
| 30 | fo_base_region | Do Not Use | NCR | — |
| 31 | ready_fo | Do Not Use | 1 | — |
| 32 | fo_segment | Do Not Use | 2+ | — |
| 33 | lifetime_loads_checked | Do Not Use | 45 | — |
| 34 | fo_load_impressions | Do Not Use | 5+ | — |
| 35 | fo_sub_type | Do Not Use | Subs | — |
| 36 | demand_cards_seen | Number of demand cards viewed by the FO for this demand. | 3 | — |

## 10_fact_consigner_service_stats

mp_analytics_core.fact_consigner_service_stats

**Owner:** Mohit

**Grain:** demand_id

**Short description:** Trip-level service quality metrics for consigners. Captures gate-to-loading delays, transit delays, vehicle offline time, consigner ratings and reasons, and ticket details linked to the trip. Used for service quality monitoring, delay analysis, and consigner satisfaction tracking.

**:** Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | col_6 | col_7 | col_8 | col_9 | col_10 | col_11 | col_12 | col_13 | col_14 | col_15 | col_16 | col_17 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | demand_id | Unique identifier of a demand created by a consigner. | 4605454 | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 2 | code | Consignment code of the trip — likely same data as consignment_code | WE-123456 | consignment_code |  |  |  |  |  |  |  |  |  |  |  |  |
| 3 | unloading_done_time | Timestamp when unloading at the destination was completed. | 2025-11-19 14:00:00 | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 4 | rating | Rating given by the consigner for the trip (1–5 scale). | 4 | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 5 | reasons | reasons associated with trip rating submitted by consigner | Driver Behaviour, | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 6 | gtl_delay | Pickup Delay - (Diffrence of Expected time to arrive at loading & Actual Loading Reaching time) | NO | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 7 | sys_trnst_dly | Delivery Delay (Diffrence of TAT given to Consigner for delivery and Actual Time taken for delivery<br>It Calculates transit delay status. Formula: Trip Journey – TAT = Delay Time.<br>Status categories: in_tat (ontime)<br>delay (up to 20% TaT) <br>critical (>20% TaT) | NO | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 8 | trip_journey | total time taken in transit by vehicle | 12 | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 9 | total_offline_time | Total time the vehicle was offline/untracked during the trip (minutes). | 2 | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 10 | type | Type Damage Occured in Trip | Major Broken | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 11 | reason | Specific reason for the recorded event (more granular than 'reasons'). | 1 | — |  |  |  |  |  |  |  |  |  |  |  |  |
| 12 | fo_trnst | (Time taken by FO - TAT given to FO) in transit to complete the delivery | 1 | — |  |  |  |  |  |  |  |  |  |  |  |  |

## 11_fact_cx_tickets

**mp_analytics_core.fact_cx_tickets:** Owner

**Mohit:** Grain

**ticket_code:** Short description

Support tickets raised by or for consigners. Captures ticket lifecycle (created → assigned → resolved), TAT metrics, issue categorization (right_cat, right_subject, sub_issue), and consigner feedback. Used for CX ops SLA tracking and issue root-cause analysis.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | col_6 |
| --- | --- | --- | --- | --- | --- |
| 1 | ticket_id | Internal numeric ID of the system ticket (surrogate key). | 1917184 | — | USE |
| 2 | ticket_code | Unique code for the support ticket. Also in ss_1_consignerservice_stats_table_pms and ss_1_mp_system_tickets. | TKT-20251119-001 | — | USE |
| 3 | ticket_created_time | Timestamp when the support ticket was created. | 2025-11-19 10:00:00 | — | USE |
| 4 | kam | Key Account Manager assigned to handle this ticket. | rahul.sharma@wheelseye.com | — | USE |
| 5 | assigned_to | Agent or team to whom the ticket is assigned. | cx_ops_team | — | USE |
| 6 | source | Channel through which the ticket was raised (e.g., App, Call, Email). Also in ss_1_mp_system_tickets. | App | — | USE |
| 7 | subject | Subject/title of the ticket — brief description of the issue. | PAYMENTS & CHARGES ISSUES | — | USE |
| 8 | description | Free-text complaint body, mostly Hinglish. | "As per driver dusra vehicle jaayega but gaadi maalik number update nahi kar raha hai..." | — | USE |
| 9 | context | Contextual metadata or notes associated with the ticket. | "Payment. Map" | — | USE |
| 10 | created_by | User who created the ticket. | neeraj.kumar@wheelseye.com / WE4687764 | — | USE |
| 11 | right_issue | Corrected sub-issue after QA audit; NULL 77%. | VEHICLE NUMBER DIFFERENT | — | USE |
| 12 | consignment_code | Unique code assigned to the consignment/trip. Also in ss_1_mp_system_tickets. | WE35392-2560793 | — | USE |
| 13 | right_cat | Correct/validated category of the ticket issue (post-ops review). | DELAY | — | USE |
| 14 | right_subject | Correct/validated subject of the ticket issue (post-ops review). | LOADING DELAY | — | USE |
| 15 | sub_issue | Sub-category of the ticket issue. Also in ss_1_consignerservice_stats_table_pms. | DELAY_AT_LOADING | — | USE |
| 16 | status | it shows the status of ticket (like - ACTIVE,HOLD,RESOLVED) | Resolved | — | USE |
| 17 | ticket_feedback | Feedback provided by consigner on ticket resolution. Also in ss_1_consignerservice_stats_table_pms. | SATISFIED | — | USE |
| 18 | tat | Turnaround time for ticket resolution (hours/days). | 2.5 | — | USE |
| 19 | duration | Total duration of ticket lifecycle from creation to resolution (seconds). | 9000 | — | USE |
| 20 | resolve_dif | Difference between target SLA and actual resolution time (positive = breached). | -0.5 | — | USE |
| 21 | tat_resolve_cat | Bucketed TAT resolution category (e.g., within SLA, 1-day breach). Also in ss_1_consignerservice_stats_table_pms. | 1 | — | USE |
| 22 | demand_id | Unique identifier of a demand created by a consigner. | 4605454 | — | USE |
| 23 | resolve_time | Timestamp when the ticket was resolved. Also in ss_1_mp_system_tickets. | 2025-11-19 12:30:00 | — | USE |
| 24 | workflow | MP_CONSIGNER_TICKET (114,125), PTL_CONSIGNER_USER_TICKET (7,167), PTL_CONSIGNER_TICKET (276). | MP_CONSIGNER_TICKET | — | USE |
| 25 | business_type | FTL (114,125) vs PTL (7,443); perfectly aligned with workflow. | FTL | — | USE |

## 12_fact_ptl_bookings

**mp_analytics_core.fact_ptl_bookings:** Owner

**Aniket:** Grain

**demand_id:** Short description

PTL funnel (demand → placement → trip), on-time performance, and repeat-behaviour analysis by cx segment.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | consigner_name | Business name of the consigner — variant of customer_name. | cosmos eco friends | — | USE |
| 2 | consigner_user_code | Unique identifier of a consigner (CX / customer). WheelsEye internal code, typically starts with 'WE'.<br>It depicts the Unique code assigned to the consigner | WE4634228 | — | USE |
| 3 | browsing_id | Unique request ID (245,248 distinct, range 1–245,280). | 178807 | — | USE |
| 4 | demand_time | Exact timestamp when the demand was created. | 2024-10-10 18:09:25.273 | — | USE |
| 5 | demand_id | Unique identifier of a demand created by a consigner. | 2674174 | — | USE |
| 6 | demand_status | Status of the demand (e.g.,PENDING<br>FULFILLED<br>EXPIRED). | FULFILLED | — | USE |
| 7 | consignment_code | Unique code assigned to the consignment/trip. Also in ss_1_mp_system_tickets. | WE35392-2197975 | — | USE |
| 8 | consignment_id | Unique identifier of the consignment/placement. | 2197975 | — | USE |
| 9 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE5475326 | — | USE |
| 10 | transporter_name | Name of the transporter / driver executing the trip. | DP WORLD | — | USE |
| 11 | lr_number | Lorry Receipt / docket number. 40,120 distinct — only once manifested, so NULL on expired demands. | 1301526501 | — | USE |
| 12 | in_transit_time | Timestamp when the shipment moved to In-Transit. | 2024-10-11 05:14:44 | — | USE |
| 13 | at_unloading_time | Timestamp when the vehicle arrived at the unloading point. | 2024-10-17 03:55:37 | — | USE |
| 14 | trip_end_time | Timestamp when the trip officially ended. | 2024-10-16 15:31:00 | — | USE |
| 15 | requested_pickup_eta | Pickup slot requested at demand creation. Clusters on 03:30 / 08:30 / 18:30 boundaries. | 2024-10-07 08:30:00 | — | USE |
| 16 | pd_remarks_time | When the pickup-done remark was logged; equals pickup_done_time. | 2024-10-08 19:12:38 | — | USE |
| 17 | pp_reason | Free-text ops remark on pickup status, tagged with #PD markers, often naming the carrier. Casing/spacing inconsistent. | WE35392-2196333 : #PD For DP by porter | — | USE |
| 18 | pickup_done_time | Actual pickup completion — drives the ETA-diff columns. | 2024-10-11 05:14:44 | — | USE |
| 19 | latest_pickup_eta | Most recent re-promised pickup ETA; equals requested when unrevised. | 2026-06-09 06:30:00 | — | USE |
| 20 | original_delivery_eta | Delivery ETA originally committed at booking. | 2024-10-07 03:00:00 | — | USE |
| 21 | latest_delivery_eta | Most recent revised delivery ETA. NULL if never progressed. | 2024-10-11 05:14:44 | — | USE |
| 22 | ptl_trip_rank | Sequence of this PTL trip for the consigner (0 = first). Range 0–2,952; steep decay. | 3 | — | USE |
| 23 | cx_segments_ptl | Tenure segment: 4+ (42,495), New (8,037), 1-4 (4,850). | 1-4 | — | USE |
| 24 | requested_pickup_eta_diff | Signed days late vs requested pickup ETA. Range −364 to 12,466 (dirty tail). | 3 | — | USE |
| 25 | latest_pickup_eta_diff | Same vs revised ETA. Identical distribution — pickup ETAs are rarely revised in practice. | 3 | — | USE |
| 26 | original_delivery_eta_diff | Signed days late vs original delivery promise. Range −357 to 402, mean 6. | 9 | — | USE |
| 27 | latest_delivery_eta_diff | Days late vs revised delivery ETA. Range −180 to 198, mean 4 — tighter, as expected after re-promising. | 5 | — | USE |
| 28 | topay_flag | 1 if the demand is To-Pay (consignee pays at delivery); 0 if pre-paid. | 1 | — | USE |
| 29 | selected_transporter_name | Carrier the consigner selected at booking, mixed case (vs upper-cased actual). NULL 33,628. Casing duplicates exist (DP World vs Dp World). | Lalji Mulji | — | USE |
| 30 | manifested | Boolean-as-string: false (15,340), true (2,969), NULL (37,073 older rows). | false | — | USE |
| 31 | loading_pincode | 6-digit origin PIN. Concentrated in Delhi-NCR (201009, 201301, 110041, 201306). | 122004 | — | USE |
| 32 | unloading_pincode | 6-digit destination PIN. Far more dispersed — consistent with hub-to-many PTL distribution. | 751010 | — | USE |
| 33 | source | Channel through which the ticket was raised (e.g., App, Call, Email). Also in ss_1_mp_system_tickets. | ODIN | — | USE |

## 13_dim_mp_districts

**mp_analytics_core.dim_mp_districts:** Owner

**Gajinder:** Grain

**District:** Short description

This table contains all possible districts where demand can be created.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | id | Unique identifier of district's. <br>This columns will be joined on origin_id, destination_id, district_id, ect. | 1 | — | USE |
| 2 | key | Natural join key in STATE_weye_DISTRICT format (literal _weye_ separator). 793 distinct, no nulls. | BIHAR_weye_JAMUI | — | USE |
| 3 | name | Name of district. | PATNA_BIHAR | — | USE |
| 4 | state | Name of district's state. | BIHAR | — | USE |
| 5 | cluster_id | Unique identifier of district's cluster. <br>This columns will be joined on origin_cluster_id, destination_cluster_id, ect. | 2 | — | USE |
| 6 | cluster | Name of the parent cluster = name of the district at cluster_id. 107 distinct. | PURNIA_BIHAR | — | USE |
| 7 | ncr_flag | NCR if the demand origin is in the NCR region; Non_NCR otherwise. | Non_NCR | — | USE |
| 8 | region | Coarse business region: OTHERS (708), ROI (61), NCR (24). | OTHERS | — | USE |
| 9 | tier | City tier: Tier4 (371), Tier3 (317), Tier2 (75), Tier1 (30). | Tier3 | — | USE |

## 14_dim_pricing_vt

**mp_analytics_core.dim_pricing_vt:** Owner

**Gajinder:** Grain

one pricing vehicle-type band (body_type × tyre × size-range × tonnage-range).

**Short description:** This table contains VT description aling with pricing logics.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | vt_pricing_id | <missing in Glossary> | 3 | — | USE |
| 2 | body_type | Body type of the vehicle (e.g., 'Open', 'Container', 'Trailer'). | container | — | USE |
| 3 | tyre | Tyre count of the requested vehicle on the demand.  [Same data as 'tyre_count' in fact_vehicle_info — STANDARDIZE naming] | 4 | — | USE |
| 4 | min_size | Lower bound (inclusive) of body length band, in feet. 1 acts as an open floor. | 1 | — | USE |
| 5 | max_size | Upper bound of body length band, in feet. 50 acts as an open ceiling. | 7 | — | USE |
| 6 | min_tonnage | Lower bound of payload band, in tonnes (0–40). Bands step by .1 so they don't overlap. | 0 | — | USE |
| 7 | max_tonnage | Upper bound of payload band, in tonnes (1.5–48). | 1.5 | — | USE |
| 8 | veh_tyre_type | Grouped vehicle class for pricing roll-ups: TRAILER (48), 4_6 (19), 10_12_14 (13), Other (6), LCV (5), SXL (2), MXL (2). | LCV | — | USE |

## 15_dim_supply_vt

**mp_analytics_core.dim_supply_vt:** Owner

**Gajinder:** Grain

one suply vehicle-type band (body_type × tyre × size).

**Short description:** This table contains VT description aling with supply onboarding.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | id | Unique identifier of VT description aling with supply onboarding | 18 | — | USE |
| 2 | body_type | Body type of the vehicle (e.g., 'Open', 'Container', 'Trailer'). | open | — | USE |
| 3 | tyre | Tyre count of the requested vehicle on the demand.  [Same data as 'tyre_count' in fact_vehicle_info — STANDARDIZE naming] | 6 | — | USE |
| 4 | size | Exact body length in feet (not a range as in dim_pricing_vt). Spans 7–40; 32/22/40 most frequent. | 19 | — | USE |

## 16_fact_cx_vt_browsing

**mp_analytics_core.fact_cx_vt_browsing:** Owner

**Ekta:** Grain

**price_browsing_id:** Short description

Stores vehicle-type (VT) price-browsing event data for consigners, including origin-to-destination lane details and tonnage quote lookups.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | id | Unique identifier of a demand (indent / freight request) created by a consigner.<br>Commonly refer as demand_id | 2943463 | — | USE |
| 2 | origin_district | DO NOT USE | NEW DELHI | — | USE |
| 3 | destination_district | DO NOT USE | Ambala | — | USE |
| 4 | origin_key | DO NOT USE | RAJASTHAN_weye_KHAIRTHAL-TIJARA | — | USE |
| 5 | destination_key | DO NOT USE | HARYANA_weye_AMBALA | — | USE |
| 6 | via_points | DO NOT USE | {"viaPoint": [{"unloadingDistrict": {"name": "Bangalore Urban", "placeId": "ChIJ..."}}]} | — | USE |
| 7 | weight | DO NOT USE | 4.5 | — | USE |
| 8 | date | DO NOT USE | 1787131793842000 | — | USE |
| 9 | consigner_code | Consigner user code | WE1002149 | — | USE |
| 10 | origin_address_id | DO NOT USE | 117719 | — | USE |
| 11 | origin_place_id | DO NOT USE | ChIJ9fKGzFLwDDkRpIRCk-KlO84 | — | USE |
| 12 | demand_address_id | DO NOT USE | 1001 | — | DNU |
| 13 | price_browsing_id | 32-char hex UUID of the pricing-browse request. 2,943,311 distinct — the join key to downstream pricing/conversion. | df190fae1289493c805c883c3f0ca3b7 | — | USE |
| 14 | deleted | DO NOT USE | false | — | USE |
| 15 | created | Epoch microseconds of source write. Basis of created_ts. | 1787131793844000 | — | USE |
| 16 | updated | DO NOT USE | 1784814204057000 | — | USE |
| 17 | created_by | User who created the ticket. | abhishek.patel@wheelseye.com | — | USE |
| 18 | updated_by | User who last updated the ticket. | NULL | — | DNU |
| 19 | destination_address_id | DO NOT USE | 163049 | — | USE |
| 20 | destination_place_id | DO NOT USE | ChIJEW8eQiq2DzkRFI0l9ymK0us | — | USE |
| 21 | ts_ms | DO NOT USE | 1787111993848 | — | USE |
| 22 | lsn | DO NOT USE | 48610904308088 | — | USE |
| 23 | _event_time | DO NOT USE | 2026-08-18 22:29:53 | — | USE |
| 24 | created_ts | DO NOT USE | 2026-07-23 08:12:59.643 | — | USE |
| 25 | dpyear | DO NOT USE(Use for Partition) | 2026 | — | USE |
| 26 | dpmonth | DO NOT USE(Use for Partition) | 7 | — | USE |
| 27 | dpday | DO NOT USE(Use for Partition) | 23 | — | USE |
| 28 | dphour | DO NOT USE(Use for Partition) | 13 | — | USE |
| 29 | dpymd | DO NOT USE(Use for Partition) | 20260723 | — | USE |
| 30 | body_type | Body type of the vehicle (e.g., 'Open', 'Container', 'Trailer'). | CONTAINER | — | USE |
| 31 | latlng_origin | DO NOT USE | {"lat": 28.7032552, "lng": 77.45342219999999} | — | USE |
| 32 | latlng_destination | DO NOT USE | {"lat": 30.900965, "lng": 75.8572758} | — | USE |
| 33 | price_source | DO NOT USE | DS_PRICING_V2 | — | USE |
| 34 | price_metadata | DO NOT USE | [{"id": "218", "priceShown": 32500.0}] | — | USE |
| 35 | distance | DO NOT USE | 389045.6 | — | USE |

## 17_fact_experiment_user_allocat

mp_analytics_core.fact_experiment_user_allocation

**Owner:** Ekta

**Grain:** flow_type_config_id

**Short description:** Tracks the experiment variant allocations assigned to consigners for each active experiment.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | id | Unique identifier of a demand (indent / freight request) created by a consigner.<br>Commonly refer as demand_id | 311681 | — | USE |
| 2 | created | Epoch microseconds of source write. Basis of created_ts. | 1774027274257000 | — | USE |
| 3 | updated | DO NOT USE | 1774088180961936 | — | USE |
| 4 | deleted | DO NOT USE | false | — | USE |
| 5 | created_by | User who created the ticket. | bhim.singh@wheelseye.com | — | DNU |
| 6 | updated_by | User who last updated the ticket. | ptl@wheelseye.com | — | DNU |
| 7 | user_code | Consigner user code | WE8414272 | — | USE |
| 8 | flow_type_config_id | Variant identifier per experiment. Used to tag Test and Control consigners in each experiment | 18 | — | USE |
| 9 | ts_ms | DO NOT USE | 1775736600873 | — | USE |
| 10 | lsn | DO NOT USE | 0 | — | USE |
| 11 | _event_time | DO NOT USE | 2026-04-09 06:40:00 | — | USE |
| 12 | created_ts | DO NOT USE | 2026-03-20 11:51:14.257 | — | USE |
| 13 | dpyear | DO NOT USE(Use for Partition) | 2026 | — | USE |
| 14 | dpmonth | DO NOT USE(Use for Partition) | 3 | — | USE |
| 15 | dpday | DO NOT USE(Use for Partition) | 13 | — | USE |
| 16 | dphour | DO NOT USE(Use for Partition) | 20 | — | USE |
| 17 | dpymd | DO NOT USE(Use for Partition) | 20260320 | — | USE |
| 18 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | NULL | — | DNU |

## 18_fact_ptl_browsing

**mp_analytics_core.fact_ptl_browsing:** Owner

**Aniket:** Grain

**browsing_id:** Short description

that table carries browsing_id as varchar, so cast. Also lane demand heatmaps, weight/service-type mix, and channel-wise funnel drop-off.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | browsing_time | Timestamp of the PTL enquiry — primary date filter. | 2025-04-03 05:59:43 | — | USE |
| 2 | browsing_id | Unique request ID (245,248 distinct, range 1–245,280). | 163 | — | USE |
| 3 | consigner_user_code | Unique identifier of a consigner (CX / customer). WheelsEye internal code, typically starts with 'WE'.<br>It depicts the Unique code assigned to the consigner | WE7562357 | — | USE |
| 4 | uom | Unit for width/height/length. INCH (130,717) or CM (114,511). Dimensions are meaningless without this. | CM | — | USE |
| 5 | width | Package width in uom units, stored as decimal string. 0.0 common (dimensions skipped). | 15.0 | — | USE |
| 6 | height | Package height in uom units. Often equal to width/length (cubic cartons). | 12.0 | — | USE |
| 7 | length | Package length in uom units. | 20.0 | — | USE |
| 8 | service_type | Leg configuration: DOOR_TO_DOOR (75%), WAREHOUSE_TO_WAREHOUSE, WAREHOUSE_TO_DOOR, DOOR_TO_WAREHOUSE. | DOOR_TO_DOOR | — | USE |
| 9 | pickup_pincode | 6-digit pickup PIN, text to preserve leading zeros. | 201306 | — | USE |
| 10 | drop_pincode | 6-digit delivery PIN. | 570016 | — | USE |
| 11 | requested_weight | Total weight in kg. Severely dirty — range −5 to 5e+27. Must be range-capped before aggregation. | 352 | — | USE |
| 12 | request_quantity | Constant 1 on every row — no information. Real counts live in materiallist. | 1 | — | DNU |
| 13 | appointmentrequired | Appointment-slot needed. String boolean: false (196,016) / true (24,564); NULL on older rows. | false | — | USE |
| 14 | topay | Freight billed to consignee on delivery. String boolean: false (166,113) / true (32,964). | true | — | USE |
| 15 | insurance | Cargo insurance opted. String boolean; only 0.9% attach rate. | false | — | USE |
| 16 | materiallist | JSON array of package types with the real quantities: [{"length":..,"width":..,"height":..,"quantity":..}]. | [{"length":15.0,"width":15.0,"height":15.0,"quantity":16}] | — | USE |
| 17 | source | Channel through which the ticket was raised (e.g., App, Call, Email). Also in ss_1_mp_system_tickets. | WEB PORTAL | — | USE |

## 19_fact_leads

**mp_analytics_core.fact_leads:** Owner

**Ekta:** Grain

**prospectid:** Short description

Contains lead-level tracking for consigners, including prospect creation details, acquisition sources, assigned sales teams, and CRM outreach/engagement activities.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | prospectid | Prospect / lead ID linked to the consigner before they became a registered consigner_user_code (pre-signup identifier). | 599cb94a-f812-4e20-a799-cab2c0fc3187 | — | USE |
| 2 | prospect_id_created_time | Timestamp when the prospect record was first created. | 2026-08-05 11:22:25 | — | USE |
| 3 | prospect_id_created_date | Date when the prospect record was first created. | 2025-03-01 | — | USE |
| 4 | prospect_id_created_week | Week-start of the prospect's creation date. | 2025-02-23 | — | USE |
| 5 | prospect_id_created_month | Month-start of the prospect's creation date. | 2025-02-28 | — | USE |
| 6 | lead_source_detailed | Channel bucket, 8 values: App (Organic) 358,679; Field Sales 300,641; App (Paid) 104,556; Web (Paid) 77,489; Web (Organic) 69,501; Others; SEO; Paid. | App (Paid) | — | USE |
| 7 | source | Channel through which the ticket was raised (e.g., App, Call, Email). Also in ss_1_mp_system_tickets. | UAC | — | USE |
| 8 | utm_source | UTM parameter for campaign tracking (source) | PRO_App_InAppAction_DemandCreation_Mumbai_100326 | — | USE |
| 9 | consigner_user_code | Unique identifier of a consigner (CX / customer). WheelsEye internal code, typically starts with 'WE'.<br>It depicts the Unique code assigned to the consigner | WE5156752 | — | USE |
| 10 | signup_time | Signup timestamp stored as text — needs casting. Can precede lead creation. | 2026-05-07 20:12:01.585 | — | USE |
| 11 | signup_date | Date the consigner signed up. | 2026-05-07 | — | USE |
| 12 | signup_week | It defines the week of the signup date | 2026-05-04 | — | USE |
| 13 | signup_month | It defines the month of the signup date | 2026-04-30 | — | USE |
| 14 | assigned_sales_team | The current sales team aligned with the consigner: <br>FIELD SALES<br>INSIDE SALES<br>NOT ASSIGNED | INSIDE SALES | — | USE |
| 15 | assigned_sales_sub_team | The current sales sub team aligned with the consigner: <br>ONBOARDING<br>RETENTION<br>NOT ASSIGNED | ONBOARDING | — | USE |
| 16 | first_sales_team | Sales team prospect was assigned to the first time: INSIDE SALES, FIELD SALES, etc. | INSIDE SALES | — | USE |
| 17 | first_sales_sub_team | Sales sub team prospect was assigned to the first time: RETENTION, ONBOARDING, etc. | ONBOARDING | — | USE |
| 18 | first_sales_team_time | DO NOT USE | 2026-05-07 20:27:13.948 | — | USE |
| 19 | first_sales_team_date | DO NOT USE | 2026-08-12 (= 13 Aug IST) | — | USE |
| 20 | consigner_city | Do Not Use | NEW DELHI | — | USE |
| 21 | consigner_state | It depicts the state of the consigner | NCR | — | USE |
| 22 | consigner_region | Consigner's resolved region (sales geography region).<br>It depicts the region of the consigner and can have three values :<br>Not Available-when the consigner location is not available <br>NCR-when the consigner is from NCR region <br>ROI-when the consigner is from rest of india or not from NCR<br>New Serviceable | ROI | — | USE |
| 23 | consigner_state_segment | Consigner's state-level segment classification (sales geography segmentation).<br>Consigner region is extracted from the very first source in this priority - FIELD SALES>SIGNUP>VT>DEMAND>WEB | SIGNUP | — | USE |
| 24 | cx_potential | Consigner Potential as provided by Sales team | LP | — | USE |
| 25 | cx_business_category | Business Category provided by user during signup like<br>MANUFACTURER, TRADER, INDIVIDUAL, SERVICE PROVIDER, etc. | TRANSPORTER | — | USE |
| 26 | app_potential | Trip potential provided by user during signup | 20 | — | USE |
| 27 | cx_called_up_flag | 0/1 — dialled at least once | 1 | — | USE |
| 28 | cx_called_in_7_days_flag | 0/1 — first attempt within 7 days (SLA) | 1 | — | USE |
| 29 | cx_call_connected_flag | 0/1 — a call actually connected | 1 | — | USE |
| 30 | cx_meeting_flag | 0/1 — meeting logged. Can be 1 without a dial (field sales). | 1 | — | USE |
| 31 | cx_signup_post_meeting_flag | 0/1 — signed up after a meeting. 5.0% of all leads. | 0 | — | USE |

## 20_fact_cx_events_l3m

**mp_analytics_core.fact_cx_events_l3m:** Owner

**Gajinder:** Grain

pre-aggregated daily rollup per event_date × user/device × event_name × action/category × screen × demand × payload × platform/version/UTM context

**Short description:** This table contains consigner app events data for last 3 months.
Use below tables for olders events analysis,
mp_analytics_core.fact_cx_events_l12m
mp_analytics_core.fact_cx_events_l24m

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | event_date | Calendar date of the event (or timestamp when the event occurred). | 2026-08-17 | — | USE |
| 2 | user_code | Consigner user code | WE2477229 | — | USE |
| 3 | demand_id | Unique identifier of a demand created by a consigner. | 4826862 | — | USE |
| 4 | event_name | Tracked event key. v1_ = current app, bt_ = book-truck notifications. Top: v1_to_api, v1_from_api, v1_home_page, v1_pin_drag, v1_select_add, v1_start_ab_testing_flow. | v1_add_lr | — | USE |
| 5 | event_action | Interaction type, 3 values: view, click, api. | click | — | USE |
| 6 | event_category | UI grouping; blank for the plurality. Top populated: add_input, bottom_nav, map_view, top_nav, trip_details, ab_testing, sent. | trip_details | — | USE |
| 7 | screen_name | Screen where the event fired — maps the demand-creation funnel: home_page → loading/unloading_add_selection → tonnage_req → demand_price_range. | at_loading | — | USE |
| 8 | entity | Free-form payload, blank ~96%. Either JSON attribution {"ph","us","uc","um"} or key:value.<br>Commonly, it contains demand_id | {"ph":"","us":"google","uc":"Generic","um":"transport service"} | — | USE |
| 9 | miscellaneous | Second payload, key:value pairs delimited by ::. Mostly blank. | up_src:man::up_idx:0 | — | USE |
| 10 | target_product | Constant book_truck across all rows. | book_truck | — | DNU |
| 11 | app_info_id | Bundle ID: com.wheelseye.consigner or '' (web). Confirms this is the consigner app. | com.wheelseye.consigner | — | USE |
| 12 | event_platform | android (~71%), ios, mweb, '', web. | android | — | USE |
| 13 | city | Geo-IP city, title-cased. Top: Delhi, Mumbai, Bengaluru, Ahmedabad, Pune. | Ghaziabad | — | USE |
| 14 | region | Geo-IP state, title-cased. Top: Delhi, Mumbai, Bengaluru, Ahmedabad, Pune. | Karnataka | — | USE |
| 15 | app_version | App version at the time of the event. | 17.5.0 | — | USE |
| 16 | device_id | 16-char hex device ID. 63,697 distinct vs 55,060 users — the only handle for logged-out sessions. | 34dc7ef278efe177 | — | USE |
| 17 | source_utm | Install/visit attribution: google-play, whatsapp, organic, google, (not%20set) (URL-encoded). | google-play | — | USE |
| 18 | campaign_utm | Campaign name; blank ~89%. Top: mp_eventBangMSME, sup_to_acq, Generic, Brand, retention_baseline. | Generic_Mumbai | — | USE |
| 19 | medium_utm | UTM medium — for paid search this holds the keyword, not a medium. | organic | — | USE |
| 20 | unique_session | Count of distinct sessions for the context that day (not a 0/1 flag). Range 0–135. | 1 | — | USE |
| 21 | total_counts | Raw event fires collapsed into the row (1–3,459). SUM this, never COUNT(*), for true event volume. | 32 | — | USE |
| 22 | min_timestamp | Epoch microseconds of earliest raw event in the group. | 1786961546350021 | — | USE |
| 23 | max_timestamp | Epoch microseconds of latest raw event; equals min when total_counts=1. (max−min)/1e6 = dwell seconds. | 1786961659179048 | — | USE |

## 21_fact_operator_tickets

**mp_analytics_core.fact_operator_tickets:** Owner

**Mohit:** Grain

**ticket_code:** Short description

it consist all support tickets created for operators through App / Manual

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | ticket_code | Unique code for the support ticket. Also in ss_1_consignerservice_stats_table_pms and ss_1_mp_system_tickets. | T1636426 | — | USE |
| 2 | trip_id | Unique identifier of the trip associated with the demand. | WE35392-2410953 | — | USE |
| 3 | description | Free-text complaint body, mostly Hinglish. | "Message : Do p o d Mili hai" | — | USE |
| 4 | issue_identified | Agent-assigned root cause — the analytically useful classification. Top: No Response from Customer, Balance Payment, Refund Amount in bank Account, Unloading Detention, Delay in Unloading, Extra Distance. | Balance Payment | — | USE |
| 5 | subject | Subject/title of the ticket — brief description of the issue. | MP_TRIP_END | — | USE |
| 6 | status | it shows the status of ticket (like - ACTIVE,HOLD,RESOLVED) | RESOLVED | — | USE |
| 7 | a_created | Creation timestamp stored as a string — must be cast. | 2026-01-08 09:49:57.713 | — | USE |
| 8 | hold_time | String timestamp of hold/pending-third-party. Usually NULL. | 2026-05-23 00:44:09.667 | — | USE |
| 9 | resolved_time | String timestamp of resolution; NULL while ACTIVE. | 2026-01-08 12:33:47.666 | — | USE |
| 10 | resolved_dur | Resolution duration in hours (floored). 0 for sub-hour. Range 0–8,232. | 2 | — | USE |
| 11 | created_by | User who created the ticket. | WE45945 | — | USE |
| 12 | assigned_to | Agent or team to whom the ticket is assigned. | sumit.y@wheelseye.com | — | USE |
| 13 | reporting_to | Escalation owner — usually a functional mailbox (aftertrip@, fo_kyc@, finance@, resolution_mp@). Good department proxy. | aftertrip@wheelseye.com | — | USE |
| 14 | updated_by | User who last updated the ticket. | mohd.arsh@wheelseye.com | — | USE |
| 15 | consigner_type | Classification of the consigner at time of demand (New / Repeat). | SME_HP | — | USE |
| 16 | a_hour | Hour-of-day 0–23 of creation — for shift/staffing analysis. | 9 | — | USE |
| 17 | a_date | Creation date, stored as IST calendar date at UTC-midnight offset. Compare on date parts. | 2026-01-07 (= 8 Jan IST) | — | USE |
| 18 | a_month | Month number 1–12. Peak Jul/Aug, trough Jan. | 1 | — | USE |
| 19 | a_week | ISO-style week number 1–52. | 2 | — | USE |
| 20 | r_date | Resolution date, same shifted convention. NULL if unresolved. | 2026-01-07 | — | USE |
| 21 | cmnt_first | String timestamp of the first agent comment — the first-response marker. | 2026-01-08 11:43:04.336 | — | USE |
| 22 | open_from | Days open, populated only for the small live backlog (NULL 99.5%). Contains negatives — treat with caution. | 12 | — | DNU |
| 23 | created_day | Day-of-month 1–31. | 8 | — | USE |
| 24 | day_chck | Creation-vs-reporting-day flag. Near-constant "previous" (111,728) vs "same_day" (70) — little value. | previous | — | DNU |
| 25 | rank_tkt | Dedupe rank. Filter rank_tkt = 1 to guarantee one row per ticket. | 1 | — | DNU |
| 26 | cmnt_diff | First-response time in minutes (a_created → cmnt_first). Mean ~401. | 7 | — | USE |
| 27 | cmnt_res_diff | Gap from first comment to resolution — unreliable: inconsistent units and negative values. Derive from timestamps instead. | 21 | — | USE |
| 28 | ticket_feedback | Feedback provided by consigner on ticket resolution. Also in ss_1_consignerservice_stats_table_pms. | SATISFIED | — | USE |
| 29 | ticket_feedback_reason | Reason for the rating. Can be comma-separated multi-value — split before grouping. | NO_UPDATES | — | USE |
| 30 | resolved_by | Agent who actually resolved. Use this, not assigned_to, for productivity metrics. | mohd.arsh@wheelseye.com | — | USE |
| 31 | ticket_id | Internal numeric ID of the system ticket (surrogate key). | 1676122 | — | USE |

## 22_fact_system_alerts

**mp_analytics_core.fact_system_alerts:** Owner

**Mohit:** Grain

**Ticket code:** Short description

it consist all internal tickets/alerts created by system for trip management / flags

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | ticket_id | Internal numeric ID of the system ticket (surrogate key). | 1962141 | — | USE |
| 2 | ticket_code | Unique code for the support ticket. Also in ss_1_consignerservice_stats_table_pms and ss_1_mp_system_tickets. | T1922445 | — | USE |
| 3 | subject | Subject/title of the ticket — brief description of the issue. | POD_DAMAGE | — | USE |
| 4 | context | Contextual metadata or notes associated with the ticket. | "The operator has a outstanding recovery of Rs.-50.01" | — | USE |
| 5 | description | Free-text complaint body, mostly Hinglish. | "The operator has a outstanding recovery of Rs.-890.51" | — | USE |
| 6 | status | it shows the status of ticket (like - ACTIVE,HOLD,RESOLVED) | ACTIVE | — | USE |
| 7 | created | Epoch microseconds of source write. Basis of created_ts. | 2026-07-05 15:34:35.618 | — | USE |
| 8 | updated | DO NOT USE | 2026-08-12 12:33:47.310 | — | USE |
| 9 | created_by | User who created the ticket. | SYSTEM | — | USE |
| 10 | updated_by | User who last updated the ticket. | ashish.kr@wheelseye.com | — | USE |
| 11 | source | Channel through which the ticket was raised (e.g., App, Call, Email). Also in ss_1_mp_system_tickets. | SYSTEM | — | USE |
| 12 | demand_id | Unique identifier of a demand created by a consigner. | 0 | — | USE |
| 13 | consignment_code | Unique code assigned to the consignment/trip. Also in ss_1_mp_system_tickets. | WE35392-2588877 | — | USE |
| 14 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE7117273 | — | USE |
| 15 | resolve_time | Timestamp when the ticket was resolved. Also in ss_1_mp_system_tickets. | 2026-08-12 12:33:47 | — | USE |
| 16 | assigned_to | Agent or team to whom the ticket is assigned. | damage@wheelseye.com | — | USE |

## 23_fact_cx_trip_expenses

**mp_analytics_core.fact_cx_trip_expenses:** Owner

**Aniket:** Grain

one demand x expense_name row (366,161 rows / 321,146 distinct demand_id; unique_flag numbers the rows within a demand, so unique_flag=1 gives one row per demand). Span 2019-05-03 -> 2026-09-06

**Short description:** Consigner-side trip billing and expense ledger. One row per demand per expense head, carrying the freight build-up (freight, discount, GST, insurance, receivable freight) alongside the expenses charged on that trip (CANCELLATION, DELAY_CHARGE etc. - 17 heads), how much of each was reversed and by whom (Cx / system / manual), and the amount actually collected at D0 / D7 / D15 / D30 relative to the due date. Filter unique_flag=1 before aggregating the freight columns, otherwise freight values repeat across expense rows of the same demand.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | consigner_user_code | Unique identifier of a consigner (CX / customer). WheelsEye internal code, typically starts with 'WE'.<br>It depicts the Unique code assigned to the consigner | WE4846141 | — | USE |
| 2 | demand_id | Unique identifier of a demand created by a consigner. | 4913081 | — | USE |
| 3 | demand_time | Exact timestamp when the demand was created. | 2026-09-06 12:55:11 | — | USE |
| 4 | trip_end_time | Timestamp when the trip officially ended. | 2026-09-07 09:08:59 | — | USE |
| 5 | due_date | Due date by which the consigner must pay the billed amount. | 2026-09-06 18:30:00 | — | USE |
| 6 | demand_payment_mode | Payment mode / credit term code agreed for the demand (29 distinct values, e.g. A4, W1). | A4 | — | USE |
| 7 | discount | Discount given on the freight, stored as a negative amount. | -200 | — | USE |
| 8 | gst | GST charged on the freight for this demand. | 0 | — | USE |
| 9 | insurance | Cargo insurance opted. String boolean; only 0.9% attach rate. | 0 | — | USE |
| 10 | freight | Base freight amount for the demand (₹). | 4120 | — | USE |
| 11 | freight_diff | Difference between the originally quoted freight and the finally agreed / revised freight. | 0 | — | USE |
| 12 | freight_settled | Freight amount settled via adjustment or write-off rather than actual collection. | 0 | — | USE |
| 13 | receivable_freight | Net freight receivable from the consigner = freight + discount + gst + insurance. | 3920 | — | USE |
| 14 | total_pay | Total net payable / receivable position on the demand after freight and expenses are netted off. | -4116 | — | USE |
| 15 | freight_paid_d0 | Freight collected on or before the due date (D0). | -3920 | — | USE |
| 16 | freight_paid_d7 | Freight collected up to 7 days after the due date (cumulative). | -3920 | — | USE |
| 17 | freight_paid_d15 | Freight collected up to 15 days after the due date (cumulative). | -3920 | — | USE |
| 18 | freight_paid_d30 | Freight collected up to 30 days after the due date (cumulative). | -3920 | — | USE |
| 19 | freight_paid | Total freight collected against the demand till date, across all ageing buckets. | -3920 | — | USE |
| 20 | expense_name | Type of expense head charged on the trip (17 distinct, e.g. CANCELLATION, DELAY_CHARGE). | CANCELLATION | — | USE |
| 21 | added_expense | Expense amount charged to the consigner under this expense head. | 1000 | — | USE |
| 22 | reveres_expense | Total expense amount reversed / waived under this head, stored negative. (Column name is misspelt in the table - it means "reverse".) | -1000 | — | USE |
| 23 | settled_expense | Expense amount settled via adjustment rather than actual collection. | 0 | — | USE |
| 24 | reveres_expense_by_cx | Portion of the expense reversal done on the consigner request. | -1000 | — | USE |
| 25 | reveres_expense_by_system | Portion of the expense reversal done automatically by the system. | -38 | — | USE |
| 26 | reveres_expense_by_manual | Portion of the expense reversal done manually by an ops / finance user. | 0 | — | USE |
| 27 | expense_paid_d0 | Expense amount collected on or before the due date (D0). | 0 | — | USE |
| 28 | expense_paid_d7 | Expense amount collected up to 7 days after the due date (cumulative). | 0 | — | USE |
| 29 | expense_paid_d15 | Expense amount collected up to 15 days after the due date (cumulative). | 0 | — | USE |
| 30 | expense_paid_d30 | Expense amount collected up to 30 days after the due date (cumulative). | 0 | — | USE |
| 31 | expense_paid | Total expense amount collected against this expense head till date. | 0 | — | USE |
| 32 | addressed_expense | 1 if the expense has been addressed; 0 otherwise. | 1 | — | USE |
| 33 | unique_flag | <TO VERIFY — internal flag in fact_payment_summary, possibly to dedupe demand_id rows during multi-trip scenarios> | 1 | — | USE |

## 24_fact_trip_payments

**mp_analytics_core.fact_trip_payments:** Owner

**Aniket:** Grain

one demand (364,763 rows, demand_id fully unique; 43,675 distinct consigners). Span 2019-05-03 -> 2026-09-07

**Short description:** Demand-level receivables and collection table for the consigner business. One row per demand carrying the trip milestone timestamps (GTL, loading, in-transit, unloading, trip end, POD, invoice), the billing terms (payment mode, payment plan, billing date, due date), the receivable build-up (freight fare, GST, payment mode fee, discount, delay amount, TDS, settlements) and the full recovery curve - how much was recovered within due date and then within 3/5/7/15/30/45/60/90/120/150/180/240 days. Also carries the NPA position (gross and net), DSO, credit cost, and the cost of recovery effort split across sales, central and legal teams. This is the table to use for DSO, NPA, ageing and collection-efficiency reporting.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | consigner_user_code | Unique identifier of a consigner (CX / customer). WheelsEye internal code, typically starts with 'WE'.<br>It depicts the Unique code assigned to the consigner | WE7554019 | — | USE |
| 2 | customer_type | Type of consigner: SME_HP / BROKER / TRANSPORTER / ENTERPRISE / SME. Consider all values by default. | SME | — | USE |
| 3 | demand_time | Exact timestamp when the demand was created. | 2025-09-17 10:07:16 | — | USE |
| 4 | demand_id | Unique identifier of a demand created by a consigner. | 3702392 | — | USE |
| 5 | ptl_flag | Flag (0/1) marking whether the demand is a PTL (Part-Truck-Load) demand. | 1 | — | USE |
| 6 | consigner_freight_fare | Final freight fare quoted to the consigner (₹). | 1040.4 | — | USE |
| 7 | topay_flag | 1 if the demand is To-Pay (consignee pays at delivery); 0 if pre-paid. | 0 | — | USE |
| 8 | consignee_payment_mode | Payment mode used by the consignee (e.g., 'PAY_AT_LOADING', 'PAY_AT_UNLOADING'). | (blank) | — | USE |
| 9 | trip_rank | Rank of this demand within the consigner's trip history (1 = first trip, etc.). | 16 | — | USE |
| 10 | demand_payment_mode | Payment mode / credit term code agreed for the demand (29 distinct values, e.g. A4, W1). | W1 | — | USE |
| 11 | demand_payment_plan | Human-readable credit plan attached to the demand (20 distinct). | Trip End Invoicing With 7 days credit | — | USE |
| 12 | invoice_creation_time | Timestamp when the invoice for the demand was generated. | 2025-10-06 22:32:56 | — | USE |
| 13 | pod_received_time | Timestamp when the Proof of Delivery was received. | 2025-09-29 12:48:07 | — | USE |
| 14 | gtl_time | Timestamp when the vehicle started moving towards the loading point. | 2025-09-17 10:07:17 | — | USE |
| 15 | at_loading_time | Timestamp when the vehicle arrived at the loading point. | 2025-09-18 07:31:30 | — | USE |
| 16 | in_transit_time | Timestamp when the shipment moved to In-Transit. | 2025-09-18 07:31:31 | — | USE |
| 17 | at_unloading_time | Timestamp when the vehicle arrived at the unloading point. | 2025-09-27 13:30:18 | — | USE |
| 18 | trip_end_time | Timestamp when the trip officially ended. | 2025-09-27 13:30:19 | — | USE |
| 19 | billing_date | Date when billing was raised against the consigner. | 2025-10-03 18:30:00 | — | USE |
| 20 | due_date | Due date by which the consigner must pay the billed amount. | 2025-10-10 18:30:00 | — | USE |
| 21 | final_receivable_amount | Net amount actually receivable from the consigner after all adjustments (₹). | 0 | — | USE |
| 22 | net_freight_settled | Net freight amount settled through adjustment / write-off rather than collection. | 0 | — | USE |
| 23 | net_operational_settled | Net operational charges settled through adjustment / write-off. | -1273.24 | — | USE |
| 24 | receivable_before_settlement | Receivable amount before any settlements/discounts (₹). | 1273.24 | — | USE |
| 25 | gst_amount | GST amount levied on this demand (₹). | 0 | — | USE |
| 26 | payment_mode_fee | Fee charged based on the payment mode chosen (₹) ) against this demand. | 0 | — | USE |
| 27 | payment_discount | Discount based on the payment mode chosen (₹) against this demand. | -67.01 | — | USE |
| 28 | delay_amount | Late-payment fee accrued on this demand (₹). | 0 | — | USE |
| 29 | tds_amount | Tax Deducted at Source amount (₹). | 0 | — | USE |
| 30 | first_payment_time | Timestamp of the first payment received against the demand. | 2025-09-20 05:21:55 | — | USE |
| 31 | last_payment_time | Timestamp of the most recent payment received against the demand. | 2025-10-14 12:51:56 | — | USE |
| 32 | overall_received_amount | Total amount received from the consigner against this demand (₹). | 0 | — | USE |
| 33 | demand_pending_balance | Outstanding balance still pending on this demand (₹). | 0 | — | USE |
| 34 | recovered_within_due_date | Amount recovered on or before due date (₹) at this demand. | -1502.42 | — | USE |
| 35 | recovered_within_3_days | Cumulative amount recovered up to 3 days after the due date. | 0 | — | USE |
| 36 | recovered_within_5_days | Cumulative amount recovered up to 5 days after the due date. | 0 | — | USE |
| 37 | recovered_within_7_days | Amount recovered within 7 days of due date (₹) at this demand. | 0 | — | USE |
| 38 | recovered_within_15_days | Amount recovered within 15 days of due date (₹) at this demand. | 0 | — | USE |
| 39 | recovered_within_30_days | Amount recovered within 30 days of due date (₹) at this demand. | 0 | — | USE |
| 40 | recovered_within_45_days | Amount recovered within 45 days of due date (₹) at this demand. | 0 | — | USE |
| 41 | recovered_within_60_days | Amount recovered within 60 days of due date (₹) at this demand. | 0 | — | USE |
| 42 | recovered_within_90_days | Amount recovered within 90 days of due date (₹) at this demand. | 0 | — | USE |
| 43 | recovered_within_120_days | Amount recovered within 120 days of due date (₹) at this demand. | 0 | — | USE |
| 44 | recovered_within_150_days | Amount recovered within 150 days of due date (₹) at this demand. | 0 | — | USE |
| 45 | recovered_within_180_days | Amount recovered within 180 days of due date (₹) at this demand. | 0 | — | USE |
| 46 | recovered_within_240_days | Amount recovered within 240 days of due date (₹) at this demand. | 0 | — | USE |
| 47 | demand_gross_npa | Gross NPA (Non-Performing Asset) amount on this demand (₹) amount which is not received till due+90 days. | 1273.24 | — | USE |
| 48 | demand_net_npa | Net NPA amount which is not received till date | 1273.24 | — | USE |
| 49 | dso | Days Sales Outstanding for the demand - days taken to collect against the billed amount. | 2 | — | USE |
| 50 | credit_cost | Cost of the credit extended on the demand (interest / cost of capital for the outstanding period). | 0.662782 | — | USE |
| 51 | total_days_taken_for_payment | Total number of days between billing and the final payment on the demand. | -21 | — | USE |
| 52 | sales_days | Number of days the recovery of this demand sat with the sales team. | 0 | — | USE |
| 53 | sales_team_cost | Cost allocated to the sales team for this demand (₹). | 0 | — | USE |
| 54 | allocated_balance | Outstanding balance allocated to the recovery teams for follow-up. | 1273.24 | — | USE |
| 55 | central_days | Number of days the recovery of this demand sat with the central collections team. | 0 | — | USE |
| 56 | central_cost | Central / overhead cost allocated to this demand (₹). | 0 | — | USE |
| 57 | allocated_balance_legal | Outstanding balance allocated to the legal recovery track. | 1273.24 | — | USE |
| 58 | legal_days | Number of days the recovery of this demand sat with the legal team. | 0 | — | USE |
| 59 | legal_cost | Legal cost incurred on this demand (₹). | 0 | — | USE |
| 60 | days_since_due | Number of days the demand is past its due date (positive = overdue). | 331 | — | USE |

## 25_fact_operator_events_l3m

mp_analytics_core.fact_operator_events_l3m

**Owner:** Aakash

**Grain:** event_date, 
event_name,
event_action,
screen_name

**Short description:** This table contains Operator clickstream data for the last 3 months

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | event_date | Calendar date of the event (or timestamp when the event occurred). | 2026-08-17 | — | USE |
| 2 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. | WE723012 | — | USE |
| 3 | demand_id | Unique identifier of a demand created by a consigner. | 4826862 | — | USE |
| 4 | event_name | Tracked event key. v1_ = current app, bt_ = book-truck notifications. Top: v1_to_api, v1_from_api, v1_home_page, v1_pin_drag, v1_select_add, v1_start_ab_testing_flow. | v1_back_btn | — | USE |
| 5 | event_action | Interaction type, 3 values: view, click, api. | click | — | USE |
| 6 | event_category | UI grouping; blank for the plurality. Top populated: add_input, bottom_nav, map_view, top_nav, trip_details, ab_testing, sent. | top_nav | — | USE |
| 7 | screen_name | Screen where the event fired — maps the demand-creation funnel: home_page → loading/unloading_add_selection → tonnage_req → demand_price_range. | choose_plan | — | USE |
| 8 | entity | Free-form payload, blank ~96%. Either JSON attribution {"ph","us","uc","um"} or key:value.<br>Commonly, it contains demand_id | {"ph":"","us":"google","uc":"Generic","um":"transport service"} | — | USE |
| 9 | miscellaneous | Second payload, key:value pairs delimited by ::. Mostly blank. | up_src:man::up_idx:0 | — | USE |
| 10 | target_product | Constant book_truck across all rows. | book_truck | — | DNU |
| 11 | app_info_id | Bundle ID: com.wheelseye.consigner or '' (web). Confirms this is the consigner app. | com.wheelseye.driver | — | USE |
| 12 | app_version | App version at the time of the event. | 24.4.0 | — | USE |
| 13 | device_id | 16-char hex device ID. 63,697 distinct vs 55,060 users — the only handle for logged-out sessions. | B014538B-903D-452F-8511-A23812351EE | — | USE |
| 14 | vehicle_id | Unique internal identifier of a specific vehicle in the WheelsEye system. | VD{vehicleNo: DL1LAQ1703, vId: 3557500, isExpiring: false} | — | USE |
| 15 | city | Geo-IP city, title-cased. Top: Delhi, Mumbai, Bengaluru, Ahmedabad, Pune. | New Delhi | — | USE |
| 16 | region | Coarse business region: OTHERS (708), ROI (61), NCR (24). | Delhi Division | — | USE |
| 17 | source_utm | Install/visit attribution: google-play, whatsapp, organic, google, (not%20set) (URL-encoded). | google-play | — | USE |
| 18 | campaign_utm | Campaign name; blank ~89%. Top: mp_eventBangMSME, sup_to_acq, Generic, Brand, retention_baseline. | Generic_Mumbai | — | USE |
| 19 | medium_utm | UTM medium — for paid search this holds the keyword, not a medium. | organic | — | USE |
| 20 | unique_session | Count of distinct sessions for the context that day (not a 0/1 flag). Range 0–135. | 1 | — | USE |
| 21 | total_counts | Raw event fires collapsed into the row (1–3,459). SUM this, never COUNT(*), for true event volume. | 43 | — | USE |
| 22 | min_timestamp | Epoch microseconds of earliest raw event in the group. | 1787432768248005 | — | USE |
| 23 | max_timestamp | Epoch microseconds of latest raw event; equals min when total_counts=1. (max−min)/1e6 = dwell seconds. | 1787432948204071 | — | USE |

## 26_fact_demands

**mp_analytics_core.fact_demands:** Owner

**Gajinder:** Grain

**demand_id:** Short description

A demand-level fact table capturing the full lifecycle of a consigner's demand — creation, DR, placement, and trip outcome — across lane, consigner, vehicle-type, special-request, and pricing dimensions. It is serving as the master base for placement, fulfilment, and pricing dashboards.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | demand_id | Unique identifier of a demand created by a consigner. |  | — | USE |
| 2 | demand_time | Exact timestamp when the demand was created. |  | — | USE |
| 3 | app_version | App version at the time of the event. |  | — | USE |
| 4 | app_platform | Type of platform used to create a demand.<br>[Same data as 'platform' in fact_consigner_demands_lead_source — standardize naming] |  | — | USE |
| 5 | experiment_ids | Variant details of the A/B experiment if live at demand level. |  |  | USE |
| 6 | dr_type | Classification of the DR  eg BEST PRICE, QUICK CONFIRMATION, SCHEDULED, etc |  | — | USE |
| 7 | dr_flag | Indicates if a Details Required (DR) was given by consigner <br>(1 = Yes, 0 = No) |  | — | USE |
| 8 | dr_time | Timestamp when the demand became a DR (Details Required) — i.e., entered the supply matching pipeline. |  | — | USE |
| 9 | demand_cancel_by_cx_time | Timestamp when the demand was cancelled by consigner. |  | — | USE |
| 10 | demand_cancel_by_sys_time | Timestamp when the demand was cancelled by system. |  |  | USE |
| 11 | plc_flag | Indicates if demand was placed with a vehicle (1 = Yes, 0 = No) |  | — | USE |
| 12 | acceptance_flag | Consigner accepted the placement (1 = Yes, 0 = No). |  | — | USE |
| 13 | auto_cancel_flag | After placement, consigner need to fill address details for demand. Acceptance is considered incomplete without this step. If consigner fails to update address within x minutes, then demand is cancel automatically (1 = Yes, 0 = No). |  | — | USE |
| 14 | trip_flag | Indicates if the demand resulted in a trip (1 = Yes, 0 = No) |  | — | USE |
| 15 | status | Demand status: EXPIRED (closed without a trip), FULFILLED (trip started), PENDING (active, searching vehicle). Consider all values by default. |  | — | USE |
| 16 | plc_demand_type | Placement demand-type classification. |  | — | USE |
| 17 | replacement_flag | Placed vehicle is replaced once for the demand (1 = Yes, 0 = No). |  | — | USE |
| 18 | operator_induced_backout | Consignment cancelled due to FO reasons (1 = Yes, 0 = No). |  | — | USE |
| 19 | operator_triggered_backout | Consignment cancelled by FO via the operator app (1 = Yes, 0 = No). |  | — | USE |
| 20 | consigner_induced_backout | Consignment cancelled due to consigner reasons (1 = Yes, 0 = No). |  | — | USE |
| 21 | consigner_triggered_backout | Consignment cancelled by consigner via the app (1 = Yes, 0 = No). |  | — | USE |
| 22 | non_plc_reason | Reason a demand was not placed. |  | — | USE |
| 23 | drop_points | Drop/destination points associated with the ticket's trip. |  | — | USE |
| 24 | special_req | 1 = demand had a special request; 0 = no special request. Consider all values by default. |  | — | USE |
| 25 | special_type | Type of special request: overheight / overweight / expressdeliverytat / opendala / extrawidth / extraperson / dieselvehicle. Consider all values by default. |  | — | USE |
| 26 | pricing_special_req | 1/0 flag for special request per pricing VT definitions (overheight & overweight defined per pricing rules). |  | — | USE |
| 27 | pricing_special_type | Type of special request per pricing definitions (overheight, overweight, expressdeliverytat, opendala, extrawidth, extraperson, dieselvehicle). |  | — | USE |
| 28 | load_type | Load type: PTL (Part Truck Load) / FTL (Full Truck Load). |  | — | USE |
| 29 | from_lat | Latitude of pickup location. |  | — | USE |
| 30 | from_long | Longitude of pickup location. |  | — | USE |
| 31 | to_lat | Latitude of drop location. |  | — | USE |
| 32 | to_long | Longitude of drop location. |  | — | USE |
| 33 | route_distance | Origin → destination route distance (km). Used as a filter (min_distance / max_distance) on the Placement and FO dashboards and to derive 'haul'. |  | — | USE |
| 34 | shortest_route_distance | Straight-line distance between origin and destination. |  | — | USE |
| 35 | consigner_user_code | Unique identifier of a consigner (CX / customer). WheelsEye internal code, typically starts with 'WE'.<br>It depicts the Unique code assigned to the consigner |  | — | USE |
| 36 | consigner_payment_status | Consigner's ability to complete DR based on outstanding payment: RESTRICTED / UNRESTRICTED. Consider all values by default. |  | — | USE |
| 37 | consigner_payment_status_at_dr | Consigner payment status (RESTRICTED/UNRESTRICTED) captured at the DR stage. |  | — | USE |
| 38 | consigner_type | Classification of the consigner at time of demand (New / Repeat). |  | — | USE |
| 39 | body_type | Body type of the vehicle (e.g., 'Open', 'Container', 'Trailer'). |  | — | USE |
| 40 | tyre_count | Tyre count of the specific vehicle.  [Same data as 'tyre' in fact_consigner_demands_lead_source — STANDARDIZE naming] |  | — | USE |
| 41 | size_in_ft | Vehicle size in feet (length of the cargo body). |  | — | USE |
| 42 | tonnage | Vehicle tonnage capacity in metric tons. |  | — | USE |
| 43 | pricing_vt_id | Unique identifier of VT description aling with pricing logics. Joined with mp_analytics_core.dim_pricing_vt |  | — | USE |
| 44 | supply_vt_id | Vehicle type ID — canonical identifier combining body type, size, and tyre count. Joined with mp_analytics_core.fact_demand_vt |  | — | USE |
| 45 | latest_consignment_id | Unique identifier of the latest consignment/placement wrt demand |  | — | USE |
| 46 | total_consignments | Number of unique vehicles found for the demand. Count is >1 in case of operator backout. |  | — | USE |
| 47 | origin_id | District id of the demand's origin. Joined with id in mp_analytics_core.dim_mp_districts |  | — | USE |
| 48 | destination_id | District id of the demand's destination. Joined with id in mp_analytics_core.dim_mp_districts |  | — | USE |
| 49 | predicted_rate_flag | Indicates if predicted price exists (1 = Yes, 0 = No). |  | — | USE |
| 50 | l1 | Lower end of the price range shown to the consigner before vehicle search starts. Derived by multiplying l2 by a factor that may vary across ODVTs. |  | — | USE |
| 51 | l2 | Predicted consigner freight fare for the given ODVT. Derived by multiplying supply_l2 (predicted supply_fare from the pricing model) by a factor that may vary across ODVTs. |  | — | USE |
| 52 | l3 | Upper end of the price range shown to the consigner before vehicle search starts. Derived by multiplying l2 by a factor that may vary across ODVTs. |  | — | USE |
| 53 | price_browsing_id | 32-char hex UUID of the pricing-browse request. 2,943,311 distinct — the join key to downstream pricing/conversion. |  | — | USE |

## 27_fact_consignments

**mp_analytics_core.fact_consignments:** Owner

**Gajinder:** Grain

**consignment_id:** Short description

A consignment-level fact table tracking the full placement-to-trip lifecycle — state transitions with timestamps, placement type/stage, backouts, and replacements. It carries the complete demand economics: consigner and operator fares, commissions, bonuses, discounts, ancillary charges (damage, penalty, detention, etc.), realised/expected P&L, and predicted price ranges — serving as the master base for placement, fulfilment, and pricing/P&L dashboards.

Columns (Description pulled from Glossary via VLOOKUP)

| # | Column | Description (from Glossary) | Sample value | ⚠ Standardization | use_flag |
| --- | --- | --- | --- | --- | --- |
| 1 | consignment_id | Unique identifier of the consignment/placement. |  | — | USE |
| 2 | consignment_code | Unique code assigned to the consignment/trip. Also in ss_1_mp_system_tickets. |  | — | USE |
| 3 | consignment_time | Timestamp when consignment was created. |  | — | USE |
| 4 | operator_code | Unique identifier of a fleet operator (FO). WheelsEye internal code, typically starts with 'WE'. |  | — | USE |
| 5 | vehicle_id | Unique internal identifier of a specific vehicle in the WheelsEye system. |  | — | USE |
| 6 | consignment_state | Status/state of the consignment. |  | — | USE |
| 7 | consignment_rank | In case of multiple consignments for a single demand, represents order of consignment creation. |  | — | USE |
| 8 | scheduled_time | Timestamp when vehicle is placed and waiting for consigner acceptance. |  | — | USE |
| 9 | gtl_time | Timestamp when the vehicle started moving towards the loading point. |  | — | USE |
| 10 | at_loading_time | Timestamp when the vehicle arrived at the loading point. |  | — | USE |
| 11 | in_transit_time | Timestamp when the shipment moved to In-Transit. |  | — | USE |
| 12 | at_unloading_time | Timestamp when the vehicle arrived at the unloading point. |  | — | USE |
| 13 | trip_end_time | Timestamp when the trip officially ended. |  | — | USE |
| 14 | backout_time | Timestamp when the consignment was cancelled. |  | — | USE |
| 15 | demand_cancel_time | Timestamp when the demand was cancelled. |  | — | USE |
| 16 | placement_type | Mode of placement: Manual or Automation. |  | — | USE |
| 17 | operator_induced_backout | Consignment cancelled due to FO reasons (1 = Yes, 0 = No). |  | — | USE |
| 18 | operator_triggered_backout | Consignment cancelled by FO via the operator app (1 = Yes, 0 = No). |  | — | USE |
| 19 | consigner_induced_backout | Consignment cancelled due to consigner reasons (1 = Yes, 0 = No). |  | — | USE |
| 20 | consigner_triggered_backout | Consignment cancelled by consigner via the app (1 = Yes, 0 = No). |  | — | USE |
| 21 | replacement_consignment_id | Unique identifier of the consignment/placement that replaced the current consignment. |  | — | USE |
| 22 | replacement_supplyfare | Supply fare of the consignment/placement that replaced the current consignment. |  | — | USE |
| 23 | replacement_time | Timestamp when replacement consignment was created. |  | — | USE |
| 24 | revenue | It is gross GMV. It is sum of all base prices plus service charge amount (base price*service charge rate) of the trips |  | — | USE |
| 25 | payable_to_operator | Final price payable to operator post deducting fo commission |  | — | USE |
| 26 | supplyfare | Final fare at which we got the vehicle |  | — | USE |
| 27 | base_price | Supply fare with our margin ('Middle Share') which should have been shown to the consignor in case there is zero non-coupon discount applicable. |  | — | USE |
| 29 | base_price_shown | Price shown to the consignor post non-coupons discounts. |  | — | USE |
| 28 | final_price | This is the price shown to the consignor post non-coupon and coupon discounts. |  | — | USE |
| 30 | payable_by_consigner | Final price owed by the consignor post the service charge. |  | — | USE |
| 31 | freight_difference | Manual consigner price change. |  | — | USE |
| 32 | service_charge | Commission charged to consigner over wfms_consigner_freight_fare. It is a % of base_price. |  | — | USE |
| 33 | coupon_discount | These are discount given to consigner for damages, delays, service issues, new user discount, etc. These are visible to consigners. |  | — | USE |
| 34 | noncoupon_discount | These are discount given to consigner to change their payble amount. These are not visible to consigners and could be a negative discount. |  |  |  |
| 35 | fo_commission | Commission charged to operator. Flat amount based on vehicle type (vt_category) or fare amount. |  | — | USE |
| 36 | token_forfeit | Penalty amount charged to the operator in case of backout. |  | — | USE |
| 37 | net_take_rate | Realised net P&L on the demand (₹) wrt final freight fare. |  | — | USE |
| 38 | gross_take_rate | Expected (pre-cost) P&L on the demand (₹) wrt final freight fare. |  | — | USE |
| 39 | predicted_rate_flag | Indicates if predicted price exists (1 = Yes, 0 = No). |  | — | USE |
| 40 | supply_l1 | Lower end of the supply fare range. |  | — | USE |
| 41 | supply_l2 | Predicted supply fare for the given ODVT. |  | — | USE |
| 42 | supply_l3 | Upper end of the supply fare range. |  | — | USE |
| 43 | l1 | Lower end of the price range shown to the consigner before vehicle search starts. Derived by multiplying l2 by a factor that may vary across ODVTs. |  | — | USE |
| 44 | l2 | Predicted consigner freight fare for the given ODVT. Derived by multiplying supply_l2 (predicted supply_fare from the pricing model) by a factor that may vary across ODVTs. |  | — | USE |
| 45 | l3 | Upper end of the price range shown to the consigner before vehicle search starts. Derived by multiplying l2 by a factor that may vary across ODVTs. |  | — | USE |
| 46 | reference_id | This is not relevent columns. DNU |  | — | DNU |
| 47 | tds_metadata | Consignment TDS details information exist here. Only relevent for finance use |  | — | DNU |
