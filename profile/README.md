<p align="center"> 
	<a href="#getting-started"><img alt="Data Flow Analysis" src="coffeeflowanalysis.png"></a>
</p>

Given today's interconnection of systems of systems and the growing demand for confidential and privacy-preserving data processing, analyzing software systems and finding violations at an early stage of their development is crucial. *Data Flow Diagrams (DFD)* were proposed for such structural analysis already more than [40 years ago](https://en.wikipedia.org/wiki/Structured_analysis). Until recently, however, there was a lack of both the diagram's expressiveness and the analysis capabilities to make statements about software systems from a software architectural point of view.

We provide an **open-source data flow analysis** that leverages the power of label propagation to provide software architects with simple yet powerful means to analyze privacy-related quality properties like confidentiality. The analysis has been incorporated with the [Palladio Software Architecture Simulator](https://www.palladio-simulator.com/) and also provides various input and output formats as well as a textual domain-specific language (DSL) for the formulation of data flow constraints and queries. The research originates from the DSiS group, KASTEL Institute, Karlsruhe Institute of Technology (KIT), is used in various research projects including [KASTEL](https://www.kastel.kit.edu/), [ANYMOS](https://www.anymos.de/), [SofDCar](https://sofdcar.de/), [Trust 4.0](https://github.com/Trust40-Project), and [FluidTrust](https://github.com/FluidTrust).
The project is led by [Nicolas Boltz](https://dsis.kastel.kit.edu/staff_nicolas_boltz.php) and [Sebastian Hahner](https://dsis.kastel.kit.edu/staff_sebastian_hahner.php).

## Data Flow Analysis

Our analysis uses *label propagation* to analyze the characteristics of data flows. First, we extract all possible data flows from data flow diagrams or annotated software architecture models. The extracted data flows are represented as *Transpose Flow Graph (TFGs)* that contain all relevant information about the characteristics of the flowing data and its processing, e.g., by components or servers. We propagate these characteristics through the flow graphs and compare the result against pre-formulated constraints to detect violations of confidentiality, or privacy in general. Exemplary questions are:

* Does personal data flow to unauthorized locations violating the GDPR?
* Does data leave an internal server without being encrypted first?
* Does the access to sensitive data follow Role-based Access Control (RBAC)?
* Are there any data flows that merge two distinct types of data that would void anonymity?

## Publications

The data flow analysis framework is presented in this **key publication**: 
* N. Boltz, S. Hahner, C. Gerking, R. Heinrich, "An Extensible Framework for Architecture-Based Data Flow Analysis for Information Security", in Software Architecture, Springer, 2024, [accepted, to appear](https://sebastianhahner.de/publications/2024/BoltzHahner2024_AnExtensibleFrameworkForArchitectureBasedDataFlowAnalysisForInformationSecurity.pdf)

Furthermore, these publications describe the underlying concepts in more detail:

* F. Schwickerath, N. Boltz, S. Hahner, M. Walter, C. Gerking, and R. Heinrich, "Tool-Supported Architecture-Based Data Flow Analysis for Confidentiality", presented at *17th European Conference on Software Architecture (ECSA), Tool & Demo Track*, Preprint, 2023, doi: [10.48550/arXiv.2308.01645](https://doi.org/10.48550/arXiv.2308.01645).
* S. Seifermann, R. Heinrich, D. Werle, and R. Reussner, "Detecting violations of access control and information flow policies in data flow diagrams", in *Journal of Systems and Software (JSS)*, vol. 184, Elsevier, 2022, doi: [10.1016/j.jss.2021.111138](https://doi.org/10.1016/j.jss.2021.111138).
* S. Seifermann, R. Heinrich, D. Werle, and R. Reussner, "A Unified Model to Detect Information Flow and Access Control Violations in Software Architectures", in *18th International Conference on Security and Cryptography (SECRYPT)*, SciTePress, 2021, doi: [10.5220/0010515300260037](https://doi.org/10.5220/0010515300260037).
* S. Hahner, S. Seifermann, R. Heinrich, M. Walter, T. Bureš, and P. Hnětynka, "Modeling Data Flow Constraints for Design-Time Confidentiality Analyses", presented at *18th International Conference on Software Architecture Companion (ICSA)*, IEEE, 2021, doi: [10.1109/ICSA-C52384.2021.00009](https://doi.org/10.1109/ICSA-C52384.2021.00009).
* S. Seifermann, R. Heinrich, and R. Reussner, "Data-Driven Software Architecture for Analyzing Confidentiality", in *International Conference on Software Architecture (ICSA)*, IEEE, 2019, doi: [10.1109/ICSA.2019.00009](https://doi.org/10.1109/ICSA.2019.00009).

## Project Structure

The following table shows the structure of the analysis. The most important repositories are pinned below.

| # | Repository | Description | Status |
| - | ---------- | ----------- | ------ |
| 1 | [DataFlowAnalysis](https://github.com/DataFlowAnalysis/DataFlowAnalysis) | The core repository containing the data flow extraction rules as well as the label propagation algorithm and analysis. Depends on [2](https://github.com/DataFlowAnalysis/DFD-Metamodel) and [3](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension). | [![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/DataFlowAnalysis/main.yml?label=&logo=github&style=flat-square)](https://github.com/DataFlowAnalysis/DataFlowAnalysis/actions) |
| 2 | [DFD-Metamodel](https://github.com/DataFlowAnalysis/DFD-Metamodel) | The meta model is used to model data flow diagrams with characterized data flows and as input to the [data flow analysis](https://github.com/DataFlowAnalysis/DataFlowAnalysis). | [![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/DFD-Metamodel/updatesite.yml?label=&logo=github&style=flat-square)](https://github.com/DataFlowAnalysis/DFD-Metamodel/actions) |
| 3 | [PCM-DataFlowAnalysis-Extension](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension) | This extension consists of meta models for annotating [Palladio](https://www.palladio-simulator.com/) software architecture models and serves as analysis input. | [![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension/main.yml?label=&logo=github&style=flat-square)](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension/actions) |
| 4 | [WebEditor](https://github.com/DataFlowAnalysis/WebEditor) | With this [online available](https://dataflowanalysis.github.io/WebEditor/) editor, data flow diagrams with privacy information can be created that serve as analysis input. | [![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/WebEditor/pages.yaml?label=&logo=github&style=flat-square)](https://github.com/DataFlowAnalysis/WebEditor/actions) |
| 5 | [Converter](https://github.com/DataFlowAnalysis/Converter) | Contains converters to and from other diagram representations, e.g., the [Web Editor](https://dataflowanalysis.github.io/WebEditor/) and [microSecEnD](https://github.com/tuhh-softsec/microSecEnD). Depends on [1](https://github.com/DataFlowAnalysis/DataFlowAnalysis), [2](https://github.com/DataFlowAnalysis/DFD-Metamodel) and [3](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension). | [![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/Converter/main.yml?label=&logo=github&style=flat-square)](https://github.com/DataFlowAnalysis/Converter/actions) |



## Analysis Extensions

There are currently two extensions of the data flow analysis available:

* [ABUNAI](https://github.com/abunai-dev) stands for *Architecture-Based Uncertainty-Aware Confidentiality AnalysIs* and supports the modeling and analysis of uncertainty and its impact on confidentiality. By combining the data flow analysis with architecture-based uncertainty propagation, predictions can be made on the interaction of uncertainty and confidentiality.
* [MDPA](https://github.com/Model-Based-Data-Protection-Assessments) provides *Model-Based Data Protection Assessments*. By incorporating legal information from the GDPR, experts can make statements about data privacy from a software architectural viewpoint.

## Getting Started

[![Eclipse Product](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/product/build.yml?label=Product&logo=eclipseide&style=flat-square)](https://updatesite.palladio-simulator.com/DataFlowAnalysis/product/releases/)
[![Eclipse Updatesite](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/DataFlowAnalysis/main.yml?label=Updatesite&logo=eclipseide&style=flat-square)](https://dataflowanalysis.github.io/updatesite/)
[![Web Editor](https://img.shields.io/badge/Web%20Editor-Online-blue?style=flat-square&logo=github)](https://dataflowanalysis.github.io/WebEditor/)

The easiest way to get started is by downloading our ready-to-use [Eclipse product](https://updatesite.palladio-simulator.com/DataFlowAnalysis/product/releases/).
Alternatively, all main repositories' artifacts are available on our Eclipse [updatesite](https://dataflowanalysis.github.io/updatesite/) to be directly installed into the [Eclipse Modeling Framework](https://eclipse.dev/modeling/emf/), see this [guide](https://github.com/DataFlowAnalysis/DataFlowAnalysis#installation).
[This recent publication](https://sebastianhahner.de/publications/2024/BoltzHahner2024_AnExtensibleFrameworkForArchitectureBasedDataFlowAnalysisForInformationSecurity.pdf) presents the data flow analysis framework which helps in getting started.
