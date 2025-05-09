# Central Contract Repository for the Order API

## What is Central Contract Repository?

Please see **[Documentation](https://specmatic.io/documentation/central_contract_repository.html)**

### How it works:

1. When you push changes to a branch or create a pull request targeting the main branch, the CI workflow is triggered.
2. The workflow identifies changed API specification files (YAML, JSON, and GraphQL).
3. For changed OpenAPI specifications, it runs a backward compatibility check using the Specmatic.
4. For changed GraphQL schemas, it performs a similar check using the Specmatic GraphQL.

## Linting

Below are the instructions to run the linter on your local machine

* Install [spectral](https://github.com/stoplightio/spectral#-installation-and-usage)
* Run below command inside the repo
```
spectral lint **/*.yaml 
```
* Above command leverages .spectral.yaml

## Competing examples detection 

Running below command checks for competing examples in OpenAPI specifications located in the `io/specmatic/examples/store/openapi` directory.

```
docker run -v "$(pwd):/repo:rw" \
  --env-file env.list \
  znsio/specmatic-openapi examples validate --specs-dir=/repo/io/specmatic/examples/store/openapi
```