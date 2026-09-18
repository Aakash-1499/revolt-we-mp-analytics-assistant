# mp_ab_experiments

## Glossary

| Field | Description | Mandatory |
| --- | --- | --- |
| POD | Defines the POD who designed the experiment like Cx Growth, Cx Payments, FO Growth, etc. | Yes |
| Experiment Type | Defines whether experiment is live at user level or not (Non user level = demand level) | Yes |
| Experiment Name | Defines the common name of the experiment by which it is mostly referred. | Yes |
| Start Date | The date experiment went live on product | Yes |
| Current Status | This is self explanatory (Live/ 100% Scaled/ Rolled Back) | Yes |
| 100% Scaled Up Date<br>or<br>Rolled Back Date |  | No |
| Config iD | Unique id attached to a variant of the experiment. It might repeat across experiments. | Yes |
| Variant Name | Test /Control/ <User defined> | Yes |
| Data Filters | Defines any hard filter that has to be used while calculating any metric for comparing variant performance eg. 'Demands where VT is Trailers' means we only have to consider demands where vehicle type is trailers | No |
| Top of the Funnel | Defines the traffic metric for the experiment | Yes |
| Success Metric | Self explanatory | No |
| Guardrail Metric | Self explanatory | No |
| Leading Metric | Self explanatory | No |
| Other Metrics | Self explanatory | No |
| Android App Version<br>(In case of Forced Release) | Self explanatory | No |
| iOS App Version<br>(In case of Forced Release) | Self explanatory | No |

## Experiment Variants



| POD | Experiment Type | Experiment Name | Start Date | Current Status | 100% Scaled Up Date<br>or<br>Rolled Back Date<br>(Optional) | Config iD | Variant Name | Data Filters<br>(Optional) | Top of the Funnel | Success Metric<br>(Optional) | Guardrail Metric<br>(Optional) | Leading Metric<br>(Optional) | Other Metrics<br>(Optional) | Android App Version<br>(In case of Forced Release)<br>(Optional) | iOS App Version<br>(In case of Forced Release)<br>(Optional) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Cx Growth | User Level | Booking revamp | 46246 | Live |  | 32 | Test |  | Demands | Demand to Trip | Gross Take Rate | Plc to Trip |  |  |  |
| Cx Growth | User Level | Booking revamp | 46246 | Live |  | 33 | Control |  | Demands | Demand to Trip | Gross Take Rate | Plc to Trip |  |  |  |
| Cx Growth | User Level | Trailer | 46200 | Live |  | 28 | Test | Demands where VT is Trailers | Demands | Demand to Plc | Demand to DR |  |  |  |  |
| Cx Growth | User Level | Trailer | 46200 | Live |  | 29 | Control | Demands where VT is Trailers | Demands | Demand to Plc | Demand to DR |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 19 | Super Test A |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 20 | Super Test B |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 21 | Super Control |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 22 | One time Test A |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 23 | One time Test B |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 24 | One time Control |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 25 | Normal Test A |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 26 | Normal Test B |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | User Level | Segmented discounting | 46200 | Live |  | 27 | Normal Control |  |  | Onboarding | Discount per trip |  |  |  |  |
| Cx Growth | Non-User Level | Variable take rate | 46228 | Live |  | 23 | TAKE_RATE_EXP_V1 |  | Demands |  |  |  |  |  |  |
| Cx Growth | Non-User Level | Variable take rate | 46228 | Live |  | 24 | TAKE_RATE_EXP_V2 |  | Demands |  |  |  |  |  |  |
| Cx Growth | Non-User Level | Variable take rate | 46228 | Live |  | 25 | TAKE_RATE_EXP_V3 |  | Demands |  |  |  |  |  |  |
| Cx Growth | Non-User Level | Variable take rate | 46228 | Live |  | 26 | TAKE_RATE_EXP_V4 |  | Demands |  |  |  |  |  |  |
| Cx Growth | Non-User Level | Variable take rate | 46228 | Live |  | 27 | TAKE_RATE_EXP_V5 |  | Demands |  |  |  |  |  |  |
| Cx Growth | Non-User Level | Variable take rate | 46228 | Live |  | 28 | TAKE_RATE_EXP_V6 |  | Demands |  |  |  |  |  |  |

Cx Growth
