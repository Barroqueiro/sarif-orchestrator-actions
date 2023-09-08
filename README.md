# Sarif Orchestrator Actions

GitHub actions that used the sarif-orchestrator found at [this repository](https://github.com/Barroqueiro/sarif-orchestrator) for automatic analysis on web projects.

## Inputs

- `config_dir` :  Configuration directory that can be used to pass files and information to the orchestrator
- `config_file` : File that described the scan that will be executed by the orchestrator
- `type_reporting` : Type of reporting to be produced along with the SARIF results (Markdown (MD), HTML (HTML) and PDF (PDF) are available)

## Execution

The execution occurs with a predefined directory structure and the reports are always produced inside the GitHub worker on the directory `/tmp/output`. Along side this, the input directory is the current working directory which is the root of the repository the orchestrator is analysing if a checkout is preformed using the standard checkout actions.

## Example

This example executes the action and uploads the results as an artifact.

```
- uses: barroqueiro/sarif-orchestrator-actions@main
  with:
    config-dir: ".github/workflows/config"
    type-reporting: "MD"
    config-file: "run.toml"
- uses: actions/upload-artifact@v3
  with:
    name: outputs
    path: /tmp/output
```
