# Coupling Contribution Action

A Github Action for submitting repository contributions to [Coupling](https://coupling.zegreatrob.com).


## Requirements

In order to use this Action, you must have:

- A Coupling Secret
- A Coupling Party ID (for the same party as the secret)
- A JSON containing contribution data

### JSON Contribution Data Specification

The contribution file is in a JSON formatted to a spec defined in the "digger" project.

[Digger Contribution Specification](https://github.com/robertfmurdock/ze-great-tools/blob/main/tools/digger-json/src/commonMain/kotlin/com/zegreatrob/tools/digger/json/ContributionDataJson.kt)

Any "Instant" in the specification is an ISO 8601 date-time. Any Duration is an ISO 8601 duration.

If you'd like to use the Digger Gradle Plugin to generate the JSON, see [Digger Plugin](https://github.com/robertfmurdock/ze-great-tools/tree/main/tools/digger-plugin).

## Usage

```yaml
      - uses: robertfmurdock/coupling-contribution-action@v2
        with:
          coupling-secret: YOUR_COUPLING_SECRET
          party-id: YOUR_PARTY_ID
          save-contribution: ${{ github.ref == 'refs/heads/master' }}
          contribution-file: ./contribution.json
```

## Inputs

| Name                         | Description                                                                                                                                  | Default | Data Type                |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|---------|--------------------------|
| coupling-secret              | A coupling secret for a party is required in order to update contributions.                                                                  | none    | string                   |
| party-id                     | A coupling secret for a party is required in order to update contributions.                                                                  | none    | string                   |
| contribution-file            | A JSON containing the contribution information                                                                                               | none    | path string              | 
| cli-type                     | CLI runtime type to use. Accepts "js" or "jvm"                                                                                               | js      | js / jvm                 |
| link                         | Optional link to include to relate to the contribution. If omitted, will link to commit in github.                                           | none    | hyperlink                |
| save-contribution            | Boolean flag that can disable saving the contribution. Useful for confirming the action works on branches that should not save contributions | true    | boolean                  |
| cycle-time                   | Optionally provided value for cycle time property.                                                                                           | none    | ISO-8601 duration string |
| cycle-time-from-first-commit | Should calculate cycle time by subtracting the current time from the first commit time                                                       | false   | boolean                  |
