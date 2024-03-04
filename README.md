# Project configurations for the [Data Flow App](https://github.com/Sage-Bionetworks/data_flow)

## Add DCC to `tenants.json`

The tenants.json file determines which DCCs show up in the "Select a DCC" dropdown that is displayed when DFA loads.

Each DCC should have it's own JSON object within tenants.json containing the following:

- name: The name of the DCC to appear in the DCC selection menu
- synapse_asset_view: The synapse ID of the DCCs fileview. Must include "syn".
- config_location: Filepath to the DCC's `dfa_config.json` file.

## Configure `dfa_config.json`

Each DCC has it's own directory, that at a minimum will contain the `dfa_config.json` file. Other files such as schemas can optionally be kept here too. This configuration file contains two top-level JSON objects: `dcc` and `dfa`.

### `dcc` contains configuration parameters related to the DCC and data model

| Configuration Parameter | Required | Description                                                           |
| ----------------------- | -------- | --------------------------------------------------------------------- |
| `project_name`          | TRUE     | Name of DCC contribution project (shows up in select a DCC drop down) |
| `synapse_asset_view`    | TRUE     | Asset store Synapse SynId                                             |
| `manifest_dataset_id`   | TRUE     | Dataset folder SynId of Data Flow manifest                            |
| `schema_url`            | TRUE     | URL to jsonld schema (RAW github file)                                |

### `dfa` contains configuration parameters related to the Data Flow App

| Configuration Parameter | Required | Description                                                                                                         |
| ----------------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| `icon`                  | TRUE     | Convert TRUE / FALSE to checkmark / x icons                                                                         |
| `display_name`          | FALSE    | Dashboard display names for schema attributes. If no display name is specified, attribute is hidden from dashboard. |
