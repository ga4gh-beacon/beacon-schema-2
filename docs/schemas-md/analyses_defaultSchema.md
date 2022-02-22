|Field | Description | Type | Properties | Example | Enum|
| ---| ---| ---| ---| ---| --- |
| [aligner](./obj/aligner.md) | Reference to mapping/alignment software | string | NA | bwa-0.7.8 | NA|
| [analysisDate](./obj/analysisDate.md) | Date at which analysis was performed. | string | NA | NA | NA|
| [biosampleId](./obj/biosampleId.md) | Reference to Biosample ID. | string | NA | S0001 | NA|
| [id](./obj/id.md) | Analysis reference ID (external accession or internal ID) | string | NA | NA | NA|
| [individualId](./obj/individualId.md) | Reference to Individual ID. | string | NA | P0001 | NA|
| [info](./obj/info.md) | Placeholder to allow the Beacon to return any additional information that is necessary or could be of interest in relation to the query or the entry returned. It is recommended to encapsulate additional informations in this attribute instead of directly adding attributes at the same level than the others in order to avoid collision in the names of attributes in future versions of the specification. | object | NA | NA | NA|
| [pipelineName](./obj/pipelineName.md) | Analysis pipeline and version if a standardized pipeline was used | string | NA | NA | NA|
| [pipelineRef](./obj/pipelineRef.md) | Link to Analysis pipeline resource | string | NA | NA | NA|
| [runId](./obj/runId.md) | Run identifier (external accession or internal ID). | string | NA | SRR10903401 | NA|
| [variantCaller](./obj/variantCaller.md) | Reference to variant calling software / pipeline | string | NA | GATK4.0 | NA|
