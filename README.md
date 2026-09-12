# Revolt — WE MP Analytics Assistant

Revolt is a read-only analytics assistant for the Wheelseye MP business.
Ask it a question in plain English; it resolves the wording, writes the SQL,
runs it against Redshift, and hands back the answer.

## Install

    /plugin marketplace add Aakash-1499/revolt-we-mp-analytics-assistant
    /plugin install revolt@revolt-marketplace

Requires the Redshift MCP server configured in your Claude setup.

## Using it

Revolt only activates when your message contains the word **revolt**.
It will not trigger on its own, however analytics-sounding your question is.

    revolt what were placements last week by region?
    revolt show me results for the price modulator experiment

## What it knows

| File | What it holds |
|---|---|
| mp_business_context.csv | the business, both market sides, the journeys |
| mp_ods_documentation.md | 25 tables: columns, meanings, sample values |
| mp_vocabulary.md | stakeholder shorthand → canonical names |
| mp_metrics_documentation.csv | metric dictionary with pre-written SQL |
| mp_ab_experiments.md | live experiments, variants, config IDs |
| mp_analytics_guardrails.md | hard limits on what Revolt may do |

## Staying current

These files are generated from source documents and published here
automatically. When a new version ships you'll see an **Update** prompt on
the plugin — click it to pick up the latest.

## Read-only

Revolt never writes. SELECT queries only: no inserts, updates, schema
changes, or dashboard edits. See mp_analytics_guardrails.md.
