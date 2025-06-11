<p align="center"> 
	<a href="#getting-started"><img alt="Data Flow Analysis" src="dfa-artwork.png"></a>
</p>

## DFA – The Karlsruhe Data Flow Diagram Analysis

[![Eclipse Product](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/product/build.yml?label=Product&logo=eclipseide&style=flat-square)](https://updatesite.palladio-simulator.com/DataFlowAnalysis/product/releases/)
[![Eclipse Updatesite](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/DataFlowAnalysis/main.yml?label=Updatesite&logo=eclipseide&style=flat-square)](https://dataflowanalysis.github.io/updatesite/)
[![Release](https://img.shields.io/github/v/release/DataFlowAnalysis/DataFlowAnalysis?style=flat-square&label=Release&logo=eclipseide)](https://dataflowanalysis.org/download/)
[![Documentation](https://img.shields.io/badge/Documentation-Online-green?style=flat-square&logo=GitBook&logoColor=white)](https://dataflowanalysis.org/wiki/)
[![Examples](https://img.shields.io/badge/Examples-24-purple?style=flat-square&logo=UML&logoColor=white)](https://dataflowanalysis.org/examples/)
[![Online Editor](https://img.shields.io/badge/Online%20Editor-Available-teal?style=flat-square&logo=github)](https://editor.dataflowanalysis.org)


The Karlsruhe Data Flow Diagram Analysis (DFA) is an extensible framework for data flow analysis in information security.
It is released under a permissive open-source license, developed and maintained by the [DSiS group](https://dsis.kastel.kit.edu/) from the Karlsruhe Institute of Technology (KIT), and subject to [active research](https://dataflowanalysis.org/publications/).
The framework is used in various research projects including [KASTEL](https://www.kastel.kit.edu/), [ANYMOS](https://www.anymos.de/), [SofDCar](https://sofdcar.de/), [Trust 4.0](https://github.com/Trust40-Project), and [FluidTrust](https://github.com/FluidTrust).
For more information, please see [dataflowanalysis.org](https://dataflowanalysis.org/).

By analyzing all possible data flows in [data flow diagrams](https://en.wikipedia.org/wiki/Data-flow_diagram) and other [software architecture models](https://www.palladio-simulator.com/), we can identify information security issues like confidentiality violations. Exemplary questions are:

* Does personal data flow to unauthorized locations, violating the GDPR?
* Does data leave an internal server without being encrypted first?
* Does the access to sensitive data follow Role-based Access Control (RBAC)?
* Are there any data flows that merge two distinct types of data that would void anonymity?

The framework is presented in this **key publication**:
N. Boltz and S. Hahner, et al., "**[An Extensible Framework for Architecture-Based Data Flow Analysis for Information Security](https://sebastianhahner.de/publications/2024/BoltzHahner2024_AnExtensibleFrameworkForArchitectureBasedDataFlowAnalysisForInformationSecurity.pdf)**",
ECSA, Springer, 2024, doi: [10.1007/978-3-031-66326-0_21](https://doi.org/10.1007/978-3-031-66326-0_21).

## Project Structure

The following table shows the structure of the extensible analysis framework. The most important repositories are pinned below.

| # | Repository | Description | Status |
| - | ---------- | ----------- | ------ |
| 1 | [DataFlowAnalysis](https://github.com/DataFlowAnalysis/DataFlowAnalysis) | The main repository contains the analysis, converter logic, example models, and all documentation. | [![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/DataFlowAnalysis/main.yml?label=&logo=github&style=flat-square)](https://github.com/DataFlowAnalysis/DataFlowAnalysis/actions) |
| 4 | [WebEditor](https://github.com/DataFlowAnalysis/WebEditor) | With this [online available](https://editor.dataflowanalysis.org) editor, data flow diagrams can be modeled and analyzed within your browser. | [![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/WebEditor/pages.yaml?label=&logo=github&style=flat-square)](https://github.com/DataFlowAnalysis/WebEditor/actions) |
| 3 | [PCM-DataFlowAnalysis-Extension](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension) | This extension consists of meta models for annotating [Palladio](https://www.palladio-simulator.com/) software architecture models than can serve as analysis input. | [![Status](https://img.shields.io/github/actions/workflow/status/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension/main.yml?label=&logo=github&style=flat-square)](https://github.com/DataFlowAnalysis/PCM-DataFlowAnalysis-Extension/actions) |

## Getting Started

Please see the [download](https://dataflowanalysis.org/download/) page for all relevant information.
The easiest way to get started is by downloading our ready-to-use [Eclipse product](https://updatesite.palladio-simulator.com/DataFlowAnalysis/product/releases/).
Alternatively, all main repositories' artifacts are available on our Eclipse [updatesite](https://dataflowanalysis.github.io/updatesite/) to be directly installed into the [Eclipse Modeling Framework](https://eclipse.dev/modeling/emf/).
After downloading, please see the [getting started](https://dataflowanalysis.org/wiki/gettingstarted.html) guide.
