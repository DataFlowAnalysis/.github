<p align="center"> 
	<a href="#getting-started"><img alt="Data Flow Analysis" src="profile/coffeeflowanalysis.png"></a>
</p>

# Data Flow Analysis

Given today's interconnection of systems of systems and the growing demand for confidential and privacy-preserving data processing, analyzing software systems and finding violations at an early stage of their development is crucial. *Data Flow Diagrams (DFD)* were proposed for such structural analysis already more than [40 years ago](https://en.wikipedia.org/wiki/Structured_analysis). Until recently, however, there was a lack of both the diagram's expressiveness and the analysis capabilities to make statements about software systems from a software architectural point of view.

We provide an **open-source data flow analysis** that leverages the power of label propagation to provide software architects with simple yet powerful means to analyze privacy-related quality properties like confidentiality. The analysis has been incorporated with the [Palladio Software Architecture Simulator](https://www.palladio-simulator.com/) and also provides various input and output formats as well as a textual domain-specific language (DSL) for the formulation of data flow constraints and queries. The research originates from the DSiS group, KASTEL Institute, Karlsruhe Institute of Technology (KIT), is used in various research projects including [KASTEL](https://www.kastel.kit.edu/), [ANYMOS](https://www.anymos.de/), [SofDCar](https://sofdcar.de/), [Trust 4.0](https://github.com/Trust40-Project), and [FluidTrust](https://github.com/FluidTrust), and is currently being driven by [Nicolas Boltz](https://dsis.kastel.kit.edu/staff_nicolas_boltz.php) and [Sebastian Hahner](https://dsis.kastel.kit.edu/staff_sebastian_hahner.php).

## Idea

Our analysis uses *label propagation* to analyze the characteristics of data flows. First, we extract all possible data flows from data flow diagrams or annotated software architecture models. The extracted data flows (also called *action sequences*) contain all relevant information about the characteristics of the flowing data and its processing, e.g., by components or servers. We propagate these characteristics through the data flows and compare the result against pre-formulated constraints to detect violations of confidentiality, or privacy in general. Exemplary questions are:

* Does personal data flow to unauthorized locations violating the GDPR?
* Does data leave an internal server without being encrypted first?
* Does the access to sensitive data follow Role-based Access Control (RBAC)?
* Are there any data flows that merge two distinct types of data that would void anonymity?

More information can be found in these key publications:

* F. Schwickerath, N. Boltz, S. Hahner, M. Walter, C. Gerking, and R. Heinrich, "Tool-Supported Architecture-Based Data Flow Analysis for Confidentiality", presented at *17th European Conference on Software Architecture (ECSA), Tool & Demo Track*, Preprint, 2023, doi: [10.48550/arXiv.2308.01645](https://doi.org/10.48550/arXiv.2308.01645).
* S. Seifermann, R. Heinrich, D. Werle, and R. Reussner, "Detecting violations of access control and information flow policies in data flow diagrams", in *Journal of Systems and Software (JSS)*, vol. 184, Elsevier, 2022, doi: [10.1016/j.jss.2021.111138](https://doi.org/10.1016/j.jss.2021.111138).
* S. Seifermann, R. Heinrich, D. Werle, and R. Reussner, "A Unified Model to Detect Information Flow and Access Control Violations in Software Architectures", in *18th International Conference on Security and Cryptography (SECRYPT)*, SciTePress, 2021, doi: [10.5220/0010515300260037](https://doi.org/10.5220/0010515300260037).
* S. Hahner, S. Seifermann, R. Heinrich, M. Walter, T. Bureš, and P. Hnětynka, "Modeling Data Flow Constraints for Design-Time Confidentiality Analyses", presented at *18th International Conference on Software Architecture Companion (ICSA)*, IEEE, 2021, doi: [10.1109/ICSA-C52384.2021.00009](https://doi.org/10.1109/ICSA-C52384.2021.00009).
* S. Seifermann, R. Heinrich, and R. Reussner, "Data-Driven Software Architecture for Analyzing Confidentiality", in *International Conference on Software Architecture (ICSA)*, IEEE, 2019, doi: [10.1109/ICSA.2019.00009](https://doi.org/10.1109/ICSA.2019.00009).

## Structure

The following table shows the structure of the analysis. The most important repositories are pinned below.

| # | Repository | Description | Status |
| - | ---------- | ----------- | ------ |
| 1 | [DataFlowAnalysis](https://github.com/DataFlowAnalysis/DataFlowAnalysis) | The core repository containing the data flow extraction rules as well as the label propagation algorithm and analysis. Depends on [2](https://github.com/DataFlowAnalysis/DFD-Metamodel) and [3](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension). | ![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/DataFlowAnalysis/main.yml?label=&logo=github&style=flat-square) |
| 2 | [DFD-Metamodel](https://github.com/DataFlowAnalysis/DFD-Metamodel) | The meta model is used to directly model data flow diagrams with characterized data flows and as analysis input by [1](https://github.com/DataFlowAnalysis/DataFlowAnalysis) as well as transformation output, e.g., by [6](https://github.com/DataFlowAnalysis/JSON2DFD) and [7](https://github.com/DataFlowAnalysis/ASs2DFD). | ![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/DFD-Metamodel/updatesite.yml?label=&logo=github&style=flat-square) |
| 3 | [PCM-DataFlowAnalysis-Extension](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension) | This extension consists of meta models for annotating [Palladio](https://www.palladio-simulator.com/) software architecture models and serves as analysis input for [1](https://github.com/DataFlowAnalysis/DataFlowAnalysis). | ![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension/main.yml?label=&logo=github&style=flat-square) |
| 4 | [WebEditor](https://github.com/DataFlowAnalysis/WebEditor) | With this [online available](https://dataflowanalysis.github.io/WebEditor/) editor, data flow diagrams with privacy information can be created that serve as analysis input via [6](https://github.com/DataFlowAnalysis/JSON2DFD). | ![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/WebEditor/pages.yaml?label=&logo=github&style=flat-square) |
| 5 | [DFD2JSON](https://github.com/DataFlowAnalysis/DFD2Json) | This transformation takes data flow diagrams following [2](https://github.com/DataFlowAnalysis/DFD-Metamodel) and yields JSON-files for the [WebEditor](https://github.com/DataFlowAnalysis/WebEditor). | - |
| 6 | [JSON2DFD](https://github.com/DataFlowAnalysis/JSON2DFD) | This transformation takes JSON representations from the [WebEditor](https://github.com/DataFlowAnalysis/WebEditor) or [microSecEnD](https://github.com/tuhh-softsec/microSecEnD) and yields data flow diagrams following [2](https://github.com/DataFlowAnalysis/DFD-Metamodel). | - |
| 7 | [ASs2DFD](https://github.com/DataFlowAnalysis/ASs2DFD) | This transformation takes action sequences extracted from [Palladio](https://www.palladio-simulator.com/) models annotated with [3](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension) and data flow diagrams following [2](https://github.com/DataFlowAnalysis/DFD-Metamodel). | - |

## Extensions

There are currently two extensions of the data flow analysis available:

* [ABUNAI](https://github.com/abunai-dev) stands for *Architecture-Based Uncertainty-Aware Confidentiality AnalysIs* and supports the modeling and analysis of uncertainty and its impact on confidentiality. By combining the data flow analysis with architecture-based uncertainty propagation, predictions on the interaction of uncertainty and confidentiality can be made.
* [MDPA](https://github.com/Model-Based-Data-Protection-Assessments) provides *Model-Based Data Protection Assessments*. By incorporating legal information from the GDPR, experts can make statements about data privacy from an software architectural viewpoint.

## Getting Started

The easiest way to get started is by downloading our ready-to-use [Eclipse product](https://updatesite.palladio-simulator.com/DataFlowAnalysis/product/nightly/).
Alternatively, all main repositories' artifacts are available on our Eclipse [updatesite](https://dataflowanalysis.github.io/updatesite/) to be directly installed into the [Eclipse Modeling Framework](https://eclipse.dev/modeling/emf/), see this [guide](https://github.com/DataFlowAnalysis/DataFlowAnalysis#installation).
[This recent publication](https://doi.org/10.48550/arXiv.2308.01645) also provides a good overview of the analysis.
