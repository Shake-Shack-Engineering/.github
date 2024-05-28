# PR Code Review Checklist

## Merge into QA
* During the QA freeze period DO NOT MERGE any code into the QA branch of any project without getting explicit approval from Andrey Teplyakov.
* The ONLY person who can merge develop branch into QA is Steve Buonincontri
* QA Merge Status page: https://shakeshack.atlassian.net/wiki/spaces/DPM/pages/3145105420/QA+Freeze+status

## API
* All the API request/response **headers** must be lowercase.
    * It should be checked in **both** lambda’s code and resource’s definition
* All header **values** should be in UPPERCASE
    * All header **values** must be explicitly converted to UPPERCASE in the code.
* If any API Gateway resource is created/updated in the PR, **Swagger** must be updated accordingly (openapi-documentation
  project).

## Secrets/Credentials
* No tokens or credentials should be stored in the code.

## Errors handling
* Each line on the code must be covered by try/catch.
    * All errors must be logged using a **_console.error(error)_**
    * It’s acceptable to extend the standard error message:
      ``console.error(`Custom error message : ${error}`)``

## Logging
* It's required to use \`\` to inject any data into logs:
  ``console.log(`Data : ${JSON.stringify(data)}`)``
* PII data must be logged using `logSanitizedData` method from `@shake-shack/logging` package.

## Miscellaneous
* Any new feature must be behind the Feature Flag or its options.
    * If Feature Flags are added / updated the Feature Flag diagram must be updated.
* Do not add any extra functionality to the lambda beyond its intended purpose:
    * Example: lambda authorizer must not inject additional information into the lambda, which is integrated with the endpoint.

# Links
This document: (https://shakeshack.atlassian.net/wiki/spaces/DPM/pages/3128590337/Code+review+checklist)
Branching and Merging Requirements: (https://shakeshack.atlassian.net/wiki/spaces/DPM/pages/2930278401/Merging+and+Branching+strategy)