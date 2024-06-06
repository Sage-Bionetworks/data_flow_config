# Project configurations for the [Data Flow App](https://github.com/Sage-Bionetworks/data_flow)

## Overview of steps to set up Data Flow App Configuration

1. Create directory that will contain DCC's configuration file.
2. Add DCC information to `tenants.json`.
3. Fill in `dfa_config.json`.
4. Run the manifest generation Github Action.

### Adding a DCC to `tenants.json`

The tenants.json file determines which DCCs show up in the "Select a DCC" dropdown that is displayed when DFA loads.

Each DCC should have it's own JSON object within tenants.json containing the following:

- name: The name of the DCC to appear in the DCC selection menu
- synapse_asset_view: The synapse ID of the DCCs fileview. Must include "syn".
- config_location: Filepath to the DCC's `dfa_config.json` file.

### Configuring `dfa_config.json`

Each DCC has it's own directory, that at a minimum will contain the `dfa_config.json` file. Other files such as schemas can optionally be kept here too. This configuration file contains two top-level JSON objects: `dcc` and `dfa`.

#### `dcc` contains configuration parameters related to the DCC and data model

| Configuration Parameter | Required | Description                                                           |
| ----------------------- | -------- | --------------------------------------------------------------------- |
| `project_name`          | TRUE     | Name of DCC contribution project (shows up in select a DCC drop down) |
| `synapse_asset_view`    | TRUE     | File view Synapse SynId                                               |
| `manifest_dataset_id`   | TRUE     | Dataset folder SynId of Data Flow manifest                            |
| `data_model_url`        | TRUE     | URL to jsonld schema (ex. RAW github file)                            |

#### `dfa` contains configuration parameters related to the Data Flow App

| Configuration Parameter | Required | Description                                                                                                         |
| ----------------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| `icon`                  | TRUE     | Convert TRUE / FALSE to checkmark / x icons                                                                         |
| `display_name`          | FALSE    | Dashboard display names for schema attributes. If no display name is specified, attribute is hidden from dashboard. |

### Generating a Data Flow manifest using GitHub Actions

The Manifest Generation Action generates a Data Flow manifest and submits it to Synapse. Run the workflow by navigating to the Action's page, clicking `Run workflow`, and filling in the required inputs. This action will use `dfa_config.json` to source `synapse_asset_view`, `manifest_dataset_id`, and `data_model_url`.

Manifest generation action can be found [here](https://github.com/Sage-Bionetworks/data_flow_config/actions/workflows/generate_manifest.yml).
