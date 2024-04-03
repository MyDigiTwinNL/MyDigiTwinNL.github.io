# MyDigiTwin - GitHub organization

![Your Organization Logo](https://github.com/MyDigiTwinNL/.github/raw/main/profile/793693_14833bd197c84acd8ccfdd07b77f8d61~mv2.png)


## Project Description

MyDigiTwin is a scientific initiative to develop a platform in which individuals can, for the first time, directly compare their personal health data with big-data reference data available from multiple cohorts, including ±200,000 national and ±500,000 international volunteers with long-term follow-up. This big-data will be queried via FAIR data access points and “on the fly” comparison by Artificial Intelligence (AI)-based algorithms will return results that will be used to render a “Digital Twin” (representative) of each individual user. This “Digital Twin” informs the user on the actual observed cardiovascular events of the identified “most alike” volunteers from big-data reference sets. The “Digital Twin” can also be modified for input variables to allow the user to simulate the effect of changes (e.g. in Lifestyle) and assess benefits or harm. The MyDigiTwin platform will also make AI tools available to the users to “check” whether their personal data, including possible pharmacotherapy, is in line with the official recommendations from professional cardiovascular practice guidelines. Dedicated research will be directed to obtain fundamental insights into the readiness of society to optimally align the foreseen platform and cockpit (user interface) with the needs and expectations of users. A co-creation strategy will be used to develop MyDigiTwin and its efficacy, in order to empower patients and enable shared decision-making. This will be tested in a real-life setting by our clinicians. MyDigiTwin contributes to self-management and improved interaction with health care professionals through knowledge-driven empowerment, technical solutions to enhance communication, and reports to simulate shared decision making.

## Key repositories

### System and Software architecture

1. **[MyDigiTwin architecture (requires organization membership)](https://github.com/MyDigiTwinNL/MyDigiTwin-architecture-documentation)**: (Living) Architecture documentation for the MyDigiTwin project, based on arc42, a lightweight template for documenting software architectures.

### Data harmonization

The MedMij/FHIR standard was chosen as the mean for unifying the structure, formats, and dimensions across the aforementioned big-data reference datasets. Given this and the privacy-preserving principles that guide MyDigiTwin's system architecture, there are two key requirements for this harmonization process: (1) the reference datasets/biobanks must not leave their host, hence their transformations (to the FHIR standard) need to be performed within their corresponding cluster environment, and (2) any computations on the transformed data must also be performed within the cluster environment.

Given these requirements, the following tools are currently under development:

1. **[LifelinesCSV2CDF](https://github.com/MyDigiTwinNL/LifelinesCSV2CDF)**: for pre-processing and rearranging the assessment-centered Lifelines' CSV data (one file per assessment, with the results of N participants), into patient-centered CDF files (N files, each one with all the assessment of one participant). This format servers as an intermediate, standardized format that simplifies the computation of pairing rules defined for transforming any reference dataset into FHIR format.
2. **[CDF2FHIR](https://github.com/MyDigiTwinNL/CDF2Medmij-Mapping-tool)**: Framework for transforming cohort data structured as CDF files into standard FHIR-resource bundles, giving a set of pairing rules.

### Harmonized-data access (for researchers and federated-learning nodes)

1. **[Lifelines harmonized data access documentation (requires organization membership)](https://github.com/MyDigiTwinNL/LifelinesDataAccessDocumentation)**: A tool for traversing local FHIR resources, getting the properties that are relevant for research purposes and making them explorable/usable on any regular programming language.


## Contact

For any questions or support, please open an issue on our GitHub repositories.

## License

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.


