# Stakeholder Vocabulary → Canonical Mapping

Stakeholders at Wheelseye use a lot of internal shorthand and Hinglish phrasing. Map their words to the canonical tables/columns/metrics before doing anything else. The goal here is to remove ambiguity at the start so the rest of the workflow does not waste cycles asking the wrong question of the wrong table.

If the stakeholder uses a term not in this list, ask them to clarify — don't guess.

## Entities

| **Stakeholder says…** | **Canonical** | **Likely table** |
| --- | --- | --- |
| FO, operator, fleet operator, driver, supply, trucker | operator_code | fact_operators_mp_events, fact_operators_onb, fact_vehicle_info, dim_operator_base_district |
| Cx, customer, consigner, shipper, demand-side, payer | consigner_user_code | fact_consigner_demands_lead_source |
| Demand, indent, freight request, load | demand_id | fact_consigner_demands_lead_source |
| Vehicle, truck, tipper, container | vehicle_id | fact_vehicle_info |
| Opsearch, supply depth, FOs within 120km, notification pool | demand_id (summary) / demand_id+operator_code (per-FO) | fact_demand_opsearch_summary, fact_demand_opsearch_operator_summary |
| Bid, token, token paid, token refund/forfeit | demand_id+operator_code | fact_operator_tokens |
| Rating, service quality, delivery delay, GTL delay, damage | demand_id | fact_consigner_service_stats |

## Funnel stages (FO side)

| **Stakeholder says…** | **Canonical column / flag** | **Metric this enables** |
| --- | --- | --- |
| Visitor, landed FO, came to MP, opened marketplace | landed_on_mp = 1 | # Visitors |
| Browsed, opened a load, viewed LDP, checked load detail | is_checked_loads > 0 | # LDP FO |
| Ready FO, onboarded FO, validated vehicle and lane | ready_fo = 1 (events fact) or mp_status = 'MP Ready' AND ready_date IS NOT NULL (onb fact) | # Ready FO |
| Paid token, plc, placed, placement | is_token_paid > 0 (FO-side) or plc_flag = 1 (Cx-side) | # Token Paid FO / % Plc FO |
| Trip, tripped, completed trip | total_trips_loads > 0 (FO-side) or trip_flag = 1 (Cx-side) | # Trip FO / % Trip FO |
| Subscribed, Subs, paying, premium | is_subscribed_at_event = 1 or fo_sub_type = 'Subs' (events); has_sub = 1, sub_date IS NOT NULL (onb) | # Subscribed FOs |
| Bid, submitted bid, bidding | count_of_loads_bid_submit > 0 | % Bid Feature FO |
| Marked VA, vehicle available, available, "I'm free" | is_marked_veh_available = 1 | % Vehicle Available |
| Not available, blocked, busy | is_marked_veh_not_available = 1 | (denominator-side) |
| Used filter, ODVT filter, origin filter, destination filter | is_loading_filter_used = 1 OR is_unloading_filter_used = 1 | % ODVT Filter FO |
| Matching, found a match, qualified in matching | is_checked_loads_matching > 0 | % Matching Feature FO |
| Reverse trip, return leg | reverse_loads_trips = 1 | % Reverse Trip FO |
| Acquired, new FO with first trip, just-acquired | trips_till_date > 0 at the FO's first event_date with that condition | # Acquired FOs |
| Retained, 2nd trip, 3+ trips | trips_till_date > 1 (2nd trip) or > 3 / trip_bucket = '3+' (retained) | # Acquired FOs - 2nd Trip / Retained cohort |
| Churned, lapsed, stopped tripping | Trip FO with last trip > 1 month before today | Churned FOs |

### FO segment (fo_segment)

Stakeholders segment FOs by lifetime trip count using fo_segment (derived from trips_till_date). Per the ODS glossary the values are:

- **"0"** → 0 trips (new / not yet acquired)
- **"1-2"** → 1st or 2nd trip (early retention)
- **"2+"** → more than 2 trips (fully retained) Use as a split / cohort filter on FO-Growth and FO-Exp metrics. (Note: trip_bucket is a separate, similar column with values '0' / '1-2' / '3+'.)

## Funnel stages (Cx side / Placement)

| **Stakeholder says…** | **Canonical** | **Metric** |
| --- | --- | --- |
| Demand, request, indent | demand_id with no flag filter | # Demands |
| DR, Demand Record, routed demand, made-it-into-the-pipeline | dr_flag = 1 | # DRs / % Demand to DR |
| Placed, plc | plc_flag = 1 | # Plc / % DR to Plc |
| Trip, fulfilled, completed | trip_flag = 1 | # Trips / % Demand to Trip |
| Auto trip, system-placed, auto plc | auto_plc = 'YES' AND trip_flag = 1 | % Auto Trips |
| Right demand, valid demand, matchable | right_demand = 1 | (filter) |
| Cancel within 30 min, quick regret, cx_plc_cancel | plc_flag=1 AND trip_flag=0 AND datediff('minute', last_plc_time, cx_plc_cancel_time) <= 30 | % Cancellations (<30 mins) |
| GTL, accepted, going to load | WFMS state = 'GOING_TO_LOAD' | % GTL Cancellations, % Plc to Acceptance, % Acceptance to Trip |

## Geography

| **Stakeholder says…** | **Canonical** |
| --- | --- |
| NCR, Delhi NCR | demand_region = 'NCR' (FO side: use the "FO State, cluster, district, region" metric — fo_base_region is Do Not Use) |
| ROI, rest of India | demand_region = 'ROI' |
| Others, OTHERS region | demand_region NOT IN ('NCR','ROI') |
| State (Maharashtra / Gujarat / Karnataka etc) | demand_state or consigner_state; FO side → FO geography metric (via dim_operator_base_district → dim_mp_districts) |
| Cluster | demand_cluster / cluster_id (⛔ sales_cluster is Do Not Use) |
| Origin, source, "from city" | origin_id / demand_city |
| Destination, "to city", drop | destination_id / destination_city |
| Lane | concat of origin → destination — use demand_origin + demand_destination separately (⛔ demand_lane is Do Not Use) |

## Sales hierarchy

| **Stakeholder says…** | **Canonical** |
| --- | --- |
| Sales team, IS / FS | assigned_sales_team (canonical) = INSIDE SALES / FIELD SALES / NOT ASSIGNED |
| Sub-team, onboarding team, retention team | assigned_sales_sub_team = ONBOARDING / RETENTION / NOT ASSIGNED |
| Manager | assigned_manager |
| ASM, SM | ⛔ assigned_manager_designation is Do Not Use — no canonical replacement |
| ZSM | ⛔ assigned_zsm / assigned_zsm_email are Do Not Use — no canonical replacement |
| RH, Regional Head | ⛔ assigned_rh is Do Not Use — no canonical replacement |
| First sales team (original assignment) | ⛔ first_sales_team is Do Not Use — use assigned_sales_team |
| Should-be sales team | ⛔ relevant_sales_team is Do Not Use — use assigned_sales_team |

## Pricing & money

| **Stakeholder says…** | **Canonical** |
| --- | --- |
| Base price, fare to FO | base_price |
| L1 / L2 / L3 fare, base rate | base_rate1 / base_rate2 / base_rate3 |
| Consigner fare, Cx freight, freight quoted | consigner_freight_fare |
| P&L, net P&L | pnl (realised) / pnl_expected (pre-cost) |
| Net Take Rate, Net TR | % Net Take Rate metric |
| Gross Take Rate, Gross TR | % Gross Take Rate metric |
| Plc price range, price bucket | plc_price_range |
| Receivable | receivable_before_settlement (gross) / final_receivable_amount (net) |
| Pending, outstanding | demand_pending_balance (per demand), customer_overall_pending (per customer) |
| Overdue | customer_overdue_pending, days_since_due > 0 |
| Bid amount, opfreight | opfreight (fact_operator_tokens) |
| Token amount / refund | amount_in_paisa / refund_amount_in_paisa (fact_operator_tokens, in paisa) |

## Payments / Credit / NPA

| **Stakeholder says…** | **Canonical** |
| --- | --- |
| Recovery, collected | recovered_within_X_days columns |
| Recovered on time, before due | recovered_within_due_date |
| Recovered within 7 / 15 / 30 / 60 / 90 / 180 days | recovered_within_7_days etc. |
| DSO | demand_dso |
| Days since due, overdue days | days_since_due |
| NPA | demand_gross_npa (≥90d cohort) and demand_net_npa (≥180d cohort) |
| Bad loan, write-off, settlement | npa_settlement_amount, npa_operational_amount |
| Credit cost | demand_credit_cost |
| Discount given to consigner | payment_discount |
| Payment mode fee, our fee revenue | payment_mode_fee |
| Delay fee, late fee, delay charger | delay_amount (% Delay Charges metric — note: dashboard typo says "Chargers") |
| KYC for credit, credit KYC | credit_kyc_flag, credit_kyc_status, kyc_completed_time |
| Cream Cx, top-tier | cream_flag = 1 |
| Restricted, blocked Cx | account_restriction_status = 'RESTRICTED' |
| Billing mode, payment plan, advance, postpaid 15, postpaid 30 | billing_submode (raw code) → maps to human-readable via CASE WHEN. See Payment Plan Usage metric for the full mapping. |
| Bank credit | billing_submode ILIKE '%F%' (= 'Bank' in human-readable) |
| Pay at Loading (PAL), Pay at Unloading (PAU / Paul) | billing_submode ILIKE '%A%' (PAL) / '%C%' (PAU) |
| 60-day credit / 30-day credit / 15-day credit | billing_submode value-set; W4/W8/WT30/WW30 → '30-37 Days Credit', W9/WT60/WW60 → '60-67 Days Credit', etc. |
| To-Pay, consignee pays | topay_flag = 1 |
| GST, FCM, RCM | gst_type, gst_number, gst_amount |
| Wallet | wallet_balance, last_wallet_entry |

## Token / bid status (fact_operator_tokens)

| **Stakeholder says…** | **Canonical** |
| --- | --- |
| Bid submitted, entered price | row with opfreight non-empty (status = 'INITIATED' before token) |
| Token paid | status = 'SUCCESS' |
| Token refunded (didn't convert) | status = 'REFUNDED' |
| Forfeited (won bid but backed out) | status = 'FORFEITED' |
| Bid expired (no token) | status = 'EXPIRED' |
| Matching flow (took shown price) vs Bidding flow (own price) | flow = 'MATCHING' / flow = 'BIDDING' |

## Service quality (fact_consigner_service_stats)

| **Stakeholder says…** | **Canonical** |
| --- | --- |
| Rating, stars | rating (1–5) |
| Rating reasons | reasons |
| Pickup delay, gate-to-loading delay | gtl_delay |
| Delivery / transit delay, in_tat / delay / critical | sys_trnst_dly |
| Vehicle offline / untracked time | total_offline_time |
| Damage | type (damage type) |

## Cohorts & segments

| **Stakeholder says…** | **Canonical** |
| --- | --- |
| Onboarding cohort, new Cx, 0-trip Cx | cx_segment = 'New' OR trip_rank <= 4 (depending on which dashboard); also see cx_segment Signup/Repeat/Unactivated/Dormant classification |
| Retention cohort, repeat Cx | cx_segment = '4+' OR trip_rank > 4 (Payment POD uses trip_rank > 4) |
| Dormant Cx, lapsed, 90-day inactive | cx_segment = 'Dormant' (monthly classification — last trip > 90 days before given month) |
| FS, FS Cx | Sales team = 'FIELD SALES' |
| IS, IS Cx | Sales team = 'INSIDE SALES' |

## Time terminology

| **Stakeholder says…** | **Canonical** |
| --- | --- |
| DoD, day-on-day | timeframe_type / Interval = 'Day' |
| WoW, week-on-week | 'Week' |
| MoM, month-on-month | 'Month' |
| Cumulative, lifetime | View_Type = 'Cumulative' (or use _till_date / life_time_ columns) |
| Period, in-period | View_Type = 'Normal' |
| Hourly, today's pacing, intra-day | Hourly tab on Placement Overview (mp_demand_details source, not the canonical fact) |

## Common shorthand / typos / Hinglish

| **You'll see…** | **Read as** |
| --- | --- |
| "plc" | placement |
| "Cx" | consigner / customer |
| "FO" | fleet operator (supply side) |
| "OB" | Onboarding |
| "RT" | Retention |
| "Plc Cx" / "placed Cx" | consigner whose demand was placed |
| "Trip Cx" / "Tripping Cx" | consigner whose demand became a trip |
| "DR drop" / "DR cancel" | DR cancelled before placement |
| "kyc nahi hua" / "no kyc" | credit_kyc_status != 'Approved' |
| "limit khatam" / "credit limit exhausted" | account_restriction_status = 'RESTRICTED' AND account_restriction_substatus = 'OVERDUE_LIMIT' |
| "VA mark", "marked VA" | Vehicle Available marked |
| "GTL", "GTL ho gaya" | Going-to-Load state in WFMS (= driver accepted) |
| "Token paid", "token kar diya" | is_token_paid > 0 |
| "Acquired" | first trip done |
| "Drop off", "leakage" | conversion gap between funnel stages |
| "Chargers" | dashboard typo for Charges — read as "delay charges" |
| "Paul" | Pay At Unloading (PAU). Sometimes a typo, sometimes deliberate shorthand. |
| "L2 fare" / "L2 price" | base_rate2 |

## Region rollouts (cohort start dates to remember)

| **Region** | **Start date** | **Notes** |
| --- | --- | --- |
| NCR | 2025-12-01 | North Star base |
| ROI | 2025-12-01 | covers most of India |
| ROI:2 | 2025-12-09 | Mumbai / Pune / Bengaluru / Gujarat etc. expansion |
| ROI:3 | 2025-12-18 | Jaipur / Hyderabad expansion |
| OTHERS | (default) | everything else |

If a stakeholder asks about a region for a period before its rollout date, that's zero by construction — not a real zero. Always call this out.
