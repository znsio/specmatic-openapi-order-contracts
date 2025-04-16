# Central Contract Repository for the Order API

## Overview

This repository serves as the Central Contract Repository for API Specifications / Contracts, primarily focusing on OpenAPI specifications. It includes functionality to validate and identify duplicate examples in the OpenAPI contracts.

## Key Features

- **Duplicate Example Detection**: Automatically checks for duplicate examples in OpenAPI specifications located in the `io/specmatic/examples/store/openapi` directory.
- **CI Integration**: Warnings for duplicate examples are displayed during merge commits via the GitHub Actions workflow defined in `.github/workflows/pull_request_merge_checks.yaml`.

## How It Works

1. **Validation Process**:
    - The workflow runs on every `push` or `pull_request` to the `main` branch.
    - It validates OpenAPI examples using the `znsio/specmatic-openapi` Docker image.
    - Duplicate examples in the OpenAPI specifications are identified, and warnings are displayed in the CI logs.

2. **Specifications Directory**:
    - All OpenAPI specifications are located in the `io/specmatic/examples/store/openapi` directory.

3. **Documentation**:
    - For more details on identifying duplicate examples, refer to the [Specmatic Documentation](https://docs.specmatic.io/documentation/external_examples.html#identifying-duplicate-examples).

## Running Locally

To validate OpenAPI examples locally, you can use the following command:

```bash
docker run -v "$(pwd):/repo:rw" znsio/specmatic-openapi examples validate --specs-dir=/repo/io/specmatic/examples/store/openapi