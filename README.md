# Volt — WE MP Analytics Assistant

Volt is a read-only analytics assistant for the Wheelseye MP business.
Ask it a question in plain English; it resolves the wording, writes the SQL,
runs it against Redshift, and hands back the answer.

## Install

    /plugin marketplace add Aakash-1499/volt-we-mp-analytics-assistant
    /plugin install volt@volt-marketplace

Requires the Redshift MCP server configured in your Claude setup.

### Already had `revolt` installed?

It will not update itself into `volt`. The plugin, the marketplace and the
repo were all renamed, so its auto-update points at a catalog entry that no
longer exists and quietly finds nothing. Swap it once:

    /plugin uninstall revolt@revolt-marketplace
    /plugin marketplace remove revolt-marketplace
    /plugin marketplace add Aakash-1499/volt-we-mp-analytics-assistant
    /plugin install volt@volt-marketplace

Until you do, you stay on the last `revolt` build and get no new references.

## Using it

Volt only activates when your message contains the word **volt**.
It will not trigger on its own, however analytics-sounding your question is.

    volt what were placements last week by region?
    volt show me results for the price modulator experiment

## What it knows

| File | What it holds |
|---|---|
| mp_business_context.csv | the business, both market sides, the journeys |
| mp_ods_documentation.md | 25 tables: columns, meanings, sample values |
| mp_vocabulary.md | stakeholder shorthand → canonical names |
| mp_metrics_documentation.csv | metric dictionary with pre-written SQL |
| mp_ab_experiments.md | live experiments, variants, config IDs |
| mp_clickstream_events.md | Consigner App , Operator App Click Events |
| mp_analytics_guardrails.md | hard limits on what Volt may do |

## Staying current

These files are generated from source documents and published here
automatically. When a new version ships you'll see an **Update** prompt on
the plugin — click it to pick up the latest.

## Read-only

Volt never writes. SELECT queries only: no inserts, updates, schema
changes, or dashboard edits. See mp_analytics_guardrails.md.
