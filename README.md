# Project configurations for the [Data Flow App](https://github.com/Sage-Bionetworks/data_flow)

Each DCC that will use the Data Flow App will need a record in the `dcc_config.csv`.

| Configuration Parameter | Description |
| --- | --- |
| `project_name` | Name of DCC contribution project (shows up in select a DCC drop down) |
| `synapse_asset_view` | Asset store Synapse SynId |
| `manifest_dataset_id` | Dataset folder SynId of Data Flow manifest |
| `schema_url` | URL to jsonld schema (RAW github file) |
| `icon` | Convert TRUE / FALSE to checkmark / x icons |
