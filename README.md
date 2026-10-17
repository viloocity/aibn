AIBN — AI Bibliographic Name
Persistent, location-independent identifiers (URN namespace aibn) for workscreated in whole or in part with generative AI assistance.

Status: pre-registration. The aibn formal NID is not yet registered withIANA; identifiers are not yet assignable. The reg-segment example ispermanently reserved for documentation and examples.

docs/ — namespace registration template (the specification)
schema/ — machine-readable metadata schema, JSON-LD context, examples
License: docs CC-BY 4.0; schema and examples CC0 1.0.Contact: aibn-admin@viloocity.press

And the workflow which doubles as the verification of my draft schema, since Actions will tell you immediately whether the examples actually validate:

name: validate
on: [push, pull_request]
jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 20 }
      - run: npm install -g ajv-cli
      - run: ajv compile -s schema/aibn-record.schema.json --spec=draft2020
      - run: ajv validate -s schema/aibn-record.schema.json -d "schema/examples/record-example.json" --spec=draft2020
      - run: ajv validate -s schema/aibn-submission.schema.json -r schema/aibn-record.schema.json -d "schema/examples/submission-example.json" --spec=draft2020
