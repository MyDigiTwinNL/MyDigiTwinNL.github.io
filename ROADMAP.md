# MyDigiTwin Roadmap


## Completed milestones (2023-Q1 / 2024-Q4)


### Data Harmonization Pipeline
- [x] Designed and built a **FHIR-based harmonization framework** aligned with ZIB/MedMij standards:
  - [X]  [`CDF2MedMij-Mapping-tool`](https://github.com/MyDigiTwinNL/CDF2Medmij-Mapping-tool): a tool that generate FHIR resources based on cohort studies on the CDF format (an ad-hoc format for cohort study data defined for the project) and pairing rules defined with Typescripe.
  - [X] [`LifelinesCSV2CDF`](https://github.com/MyDigiTwinNL/LifelinesCSV2CDF): scripts for transforming Lifelines data into the CDS format required by the pipeline.
  - [X]  [`SQLonFHIR`](https://github.com/MyDigiTwinNL/SQLonFHIRProjections): tool to transform FHIR resources into a SQL database based on a set of FHIRPath or JSONPath expressions (to validate the generated FHIR resources within a cluster environment, and to 'flatten' them within a federated learning infrastructure).
  - [X] Established a **test-driven, Git-based workflow** for creating and validating mapping (pairing) rules.
  - [X] Scientific publication: [[1](https://dspace.library.uu.nl/bitstream/handle/1874/455542/SHTI-316-SHTI240735.pdf?sequence=1)]


### Proof-of-Concept Implementation
- [X] Harmonized the **Lifelines cohort dataset** (~150,000 participants) using the developed ETL pipeline.
- [X] [Guidelines for setting up a vantage6 node for the project's federated learning infrastructue](https://github.com/MyDigiTwinNL/MyDigiTwin-federeated-learning-node-setup-guidelines), validated and refined in collaboration with Lifelines data admins.
- [X] Trained a CVD prediction model using a **federated learning setup** and the FedAvg algorithm ([see algorithm implementation](https://github.com/MyDigiTwinNL/FedAvg_vantage6)) with 2 nodes on Lifelines (each one with half of the data).
- [X] Validated consistency between raw and harmonized data via SQL and script-based analyses.
- [X] Demonstrated performance improvement with federated learning (C-statistic increased from 0.764 → 0.788).
- [X] Scientific publication: [[2](https://arxiv.org/pdf/2501.12193)]
- [X] Knowledge transference (1st round): vantage6 workshop



## Current Focus (Q3 2025 -> ~)

### MyDigiTwin end-user environment

- [ ] Designing a module for integrating the models trained with MyDigiTwin's research infrastructure with the data a PGO has access to.

### Inclusion of a second data node on the research infrastructure

- [ ] Replicating the data harmonization process on the Rotterdam Study dataset.
  - [ ] Refining the generalizability of the data harmonization framework.
- [ ] Enabling pre-processing steps like the ones defined for the [FedAvg algorithm](https://github.com/MyDigiTwinNL/FedAvg_vantage6) to be executed within the federated infrastructure.
  - [ ] Upgrading the project's research infrastructure to version 5 of vanatage6 (with sessions support) once it is available.
- [ ] Setting up an additional node for the Rotterdam Study.
- [ ] Knowledge transference (2nd round): v6-compliant federated learning algorithm design + pre-processing

### From proof-of-concept to medically-sound aplication

- [ ] Phase 1: Initial Federated Experimentation
    - Goal: Evaluate feasibility of FL between Rotterdam and a subset of Lifelines (~17.000 patients).
    - Condition: Use only Lifelines data with verified ground truth (e.g., from CBS linkage if/when available).
    - Expected Benefit: Combining diverse Rotterdam data with the scale of Lifelines improves model generalizability.
    - Validation: Use an external dataset (e.g., UK Biobank) for unbiased testing.

- [ ] Phase 2: Rotterdam-Enriched Lifelines Model
    - Goal: Train on the full 150,000 Lifelines dataset augmented with enhanced Rotterdam data.
    - Methods of Enhancement:
        - Oversampling of underrepresented Rotterdam subgroups.
        - Synthetic Data Augmentation to simulate greater diversity.
    - Rationale: Compensates for Lifelines’ limited ethnic diversity using the heterogeneity in Rotterdam data.

- [ ] Phase 3: Cross-Synthetic Enrichment
    - Goal: Further improve generalization by cross-pollinating synthetic data between datasets.
    - Approach:
        - Generate synthetic Lifelines-like data to enrich Rotterdam.
        - Generate synthetic Rotterdam-like data to enrich Lifelines.
    - Reference: See [Intel's article on FL with synthetic data for methodological guidance](https://medium.com/intel-tech/the-power-of-federated-learning-with-synthetic-data-a-perfect-symbiosis-for-speed-and-performance-f2e529d061e6).

- [ ] Phase 4: Large-Scale Federated Training
    - Condition: CBS linkage completed; Lifelines ground truth validated.
    - Action: Train on the full Rotterdam dataset and all Lifelines data using federated learning.
    - Benefit: Combines deep clinical accuracy from Rotterdam with population-level insights from Lifelines.


