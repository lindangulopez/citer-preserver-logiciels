# Hands-on Exercise 2 — Mapping metadata to CodeMeta

**Duration:** 40 minutes

## Main goal

The goal is to make and justify **mapping decisions**.

This is **not** a CodeMeta-generation exercise, and you are not expected to map an entire metadata schema in 40 minutes.

Instead, select a representative set of approximately **8–12 properties** from a source schema and determine how they correspond to CodeMeta.

## Central question

> How do I systematically map metadata from my schema into CodeMeta, and how do I deal with cases where the correspondence is not straightforward?

## General workflow

```text
Select source schema
        ↓
Select representative properties
        ↓
Understand source semantics
        ↓
Find potential CodeMeta correspondences
        ↓
Compare definitions
        ↓
Classify the mapping
        ↓
Identify transformations / information loss
        ↓
Document and justify the decision
```

## Important rule

**Do not map based only on property names.**

Before deciding on a correspondence, inspect:

- the property definition,
- expected values,
- datatype,
- cardinality,
- examples,
- scope and intended meaning.

## Suggested timing

### 0–5 min — Choose schema and properties

Form a group and choose a source metadata schema.

If you did not bring one, use one of the fallback schemas supplied by the organisers.

Select roughly 8–12 representative properties.

### 5–10 min — Understand the properties

For each selected property, examine its semantics.

Record:

- definition,
- value/type,
- cardinality,
- example,
- relevant notes.

### 10–25 min — Map to CodeMeta

Search the CodeMeta vocabulary for possible correspondences.

For each source property, decide whether the mapping is:

- exact or near-exact,
- partial,
- broader,
- narrower,
- transformation required,
- ambiguous,
- no satisfactory mapping.

Document the justification for each decision.

### 25–32 min — Investigate difficult cases

Select **2–3 uncertain mappings**.

You may use the common LLM prompt supplied with the workshop to request a mapping recommendation.

Compare the LLM recommendation with your own decision.

Ask:

- Does the proposed mapping preserve the meaning?
- Is important information lost?
- Is a transformation needed?
- Is the LLM recommendation sufficiently justified?

### 32–40 min — Compare and discuss

Each group should present **one interesting or problematic mapping**, rather than the entire crosswalk.

Discussion should focus on:

- why the mapping was difficult,
- alternative mapping options,
- transformations,
- possible information loss.

## Expected output

By the end of the exercise, each group should have:

- selected a source metadata schema,
- examined approximately 8–12 properties,
- identified possible CodeMeta correspondences,
- justified the mapping decisions,
- identified mappings requiring transformations,
- identified ambiguous or uncertain mappings,
- identified properties without a satisfactory CodeMeta mapping,
- considered possible information loss,
- documented the results as a CodeMeta crosswalk.

## Template

Use:

`../resources/mapping-template.csv`

The template can be opened in a spreadsheet editor or imported into Google Sheets.
