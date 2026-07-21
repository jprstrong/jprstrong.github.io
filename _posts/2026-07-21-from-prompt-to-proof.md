---
layout: post
title: "From Prompt to Proof"
subtitle: "A practical workflow for building reliable data dashboards with AI-assisted coding"
date: 2026-07-21 09:00:00 +0800
author: Jingpu Chen
tags: [data analytics, dashboards, AI-assisted development, vibe coding]
comments: false
social-share: true
readtime: true
---

*By Jingpu Chen*

Between March and July 2026, while between roles, I set myself a practical learning goal: become much better at turning an ambiguous question into a useful, working data product. I studied AI fundamentals, prompt engineering, data-analysis workflows, and modern application development, then applied them through a series of hands-on dashboard and analytical prototypes.

Much of that work involved private data or problem contexts. This field note therefore contains no client names, project descriptions, datasets, screenshots, or proprietary results. Instead, it distils the reusable production method I developed: how I move from a prompt to a dashboard whose numbers, interactions, and conclusions can be checked.

## A dashboard is a decision interface

My first lesson was to stop treating a dashboard as a collection of charts. A useful dashboard connects evidence to a decision. Before choosing a visual, I now write down four things:

1. **Decision:** What should a user be able to understand or decide?
2. **Audience:** What does that user already know, and what could be misread?
3. **Metric:** What exactly is being counted, compared, or classified?
4. **Action:** What should happen when a change, exception, or threshold appears?

This small discipline changes the build. It prevents attractive but irrelevant charts, exposes vague requests early, and makes acceptance criteria much clearer. It also gives an AI coding assistant the context it needs to produce something coherent instead of merely plausible.

## Start with a data contract, not a UI prompt

The fastest route to an unreliable dashboard is to ask an AI tool to “make a dashboard” before defining the data. I now begin with a lightweight data contract: source, grain, time period, field meaning, units, allowable values, missing-value treatment, refresh expectations, and known limitations.

I then define each KPI as if another analyst will have to reproduce it without asking me a question. That includes the numerator and denominator, inclusion and exclusion rules, aggregation logic, time window, and rounding. Where a label such as “active,” “completed,” or “at risk” depends on a rule, the rule belongs in the definition rather than only in the interface.

This is especially important when combining spreadsheets, CSV files, databases, APIs, or text-derived signals. The sources may look compatible while using different identifiers, date conventions, category names, or levels of detail. Schema checks and explicit joins make those assumptions visible.

## Build a thin, source-backed slice first

Vibe coding is most productive when the feedback loop is short. I do not try to generate a complete analytical product in one prompt. I build a thin vertical slice:

- one representative source;
- one validated transformation;
- one well-defined KPI;
- one chart or table;
- one filter or drill-down; and
- one trace back to the supporting records.

Once that slice is correct, the pattern can be extended. This approach makes errors cheaper to find and prompts easier to improve. It also separates problems in the data from problems in the interface.

Depending on the task, my working toolkit has included Python, SQL, R, Excel, Power BI, Tableau, and web stacks using TypeScript, React, Next.js, and charting libraries. The specific tool matters less than the contract between stages: raw evidence, transformed data, metric logic, visual encoding, and user interpretation.

## Prompt for constraints and evidence

The quality of AI-assisted development depends heavily on the structure of the request. My prompts increasingly resemble short product specifications. They include:

- the user and decision context;
- the data schema and sample edge cases;
- exact metric definitions;
- required interactions and responsive behaviour;
- privacy and accessibility constraints;
- states for loading, empty data, and errors; and
- tests or observable conditions that define “done.”

I also ask the assistant to state assumptions, identify ambiguous fields, and propose validation checks before implementing. This turns prompting into requirements discovery. The AI is useful for scaffolding transformations, components, tests, and documentation, while I remain responsible for the meaning of the metric and the validity of the conclusion.

## Validation has four layers

A dashboard can render perfectly and still be wrong. I therefore use four layers of validation.

### 1. Data validation

I check types, required fields, uniqueness, ranges, missingness, duplicate records, date coverage, and referential integrity. I compare row counts and totals before and after transformations and make exceptions visible instead of silently dropping them.

### 2. Metric validation

For critical KPIs, I calculate small examples independently and reconcile them with the application output. I test boundary cases such as zero denominators, partial periods, category changes, and records that qualify for more than one group.

### 3. Product validation

Automated tests protect transformation logic and important interface behaviour. Build and lint checks catch integration problems. I test filters in combination, verify that displayed totals remain consistent, and ensure the empty and error states explain what happened.

### 4. Visual and interpretive validation

I review the product at different screen sizes and inspect labels, contrast, units, ordering, legends, and tooltips. Then I ask a more important question: could a reasonable user draw the wrong conclusion from this view? If so, the dashboard needs clearer context, a different comparison, or a visible caveat.

## Keep a human in the analytical loop

AI can accelerate code generation and help surface patterns, but it does not own the analytical judgment. I use it to suggest alternatives, challenge assumptions, draft tests, and explain technical logic in plain language. I do not treat an AI-generated formula, classification, or narrative as evidence by itself.

The final review remains human: Does the metric answer the decision question? Is the source appropriate? Is uncertainty represented honestly? Can someone reproduce the result? Are privacy-sensitive fields excluded? Does the wording distinguish observation from inference?

This is also why documentation is part of the product rather than a task saved for the end. A concise data dictionary, metric catalogue, source note, validation log, and change record make a dashboard easier to maintain and safer to use.

## The production loop I now use

My current workflow is simple enough to repeat:

1. Frame the user, decision, and intended action.
2. Inspect the sources and write the data contract.
3. Define KPIs and acceptance criteria.
4. Build one source-backed vertical slice.
5. Expand through short prompt–implement–review cycles.
6. Validate data, metrics, product behaviour, and interpretation.
7. Document assumptions, provenance, and limitations.
8. Package the result so another person can run, review, and maintain it.

The central idea is that speed and rigour are not opposites. AI-assisted coding makes iteration faster; disciplined context, validation, and documentation make that speed useful. The goal is not to produce more charts. It is to shorten the distance between a real question and trustworthy evidence—without losing the reasoning in between.
