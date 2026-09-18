# Common LLM prompt for metadata mapping

Use this prompt only for **difficult or uncertain mappings** after you have first analysed the property yourself.

```text
You are helping to create a metadata crosswalk from a source metadata schema to CodeMeta.

Source schema:
[SCHEMA NAME AND URL]

Source property:
[PROPERTY NAME]

Definition:
[PROPERTY DEFINITION]

Expected value / datatype:
[TYPE]

Cardinality:
[CARDINALITY, IF KNOWN]

Example:
[EXAMPLE VALUE, IF AVAILABLE]

Identify the most appropriate CodeMeta property or properties.

For your recommendation:

1. Provide the proposed CodeMeta property.
2. Explain the semantic correspondence.
3. Classify the mapping as one of:
   - exact or near-exact
   - partial
   - broader
   - narrower
   - transformation required
   - ambiguous
   - no satisfactory mapping
4. Explain any transformation required.
5. Identify any information that would be lost.
6. If there are multiple plausible CodeMeta properties, explain the alternatives.
7. Do not infer a mapping only from similarity between property names.

Return a concise, justified recommendation.
```

## Critical evaluation

Do not accept the model output automatically.

Compare it with:

- the source schema definition,
- the CodeMeta definition,
- value types,
- cardinality,
- examples,
- the intended meaning of both properties.

Record your final human decision in the mapping template.
