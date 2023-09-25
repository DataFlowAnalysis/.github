<p align="center"> 
	<img alt="Data Flow Analysis" src="profile/coffeeflowanalysis.png">
</p>

# Data Flow Analysis

Given today's interconnection of systems of systems and the growing demand for confidential and privacy-preserving data processing, analyzing software systems and finding violations at an early stage of their development is crucial. *Data Flow Diagrams (DFD)* were proposed for such structural analysis already more than [40 years ago](https://en.wikipedia.org/wiki/Structured_analysis). Until recently, however, there was a lack of both the diagram's expressiveness and the analysis capabilities to make statements about software systems from a software architectural point of view.

We provide an **open-source data flow analysis** that leverages the power of label propagation to provide software architects with simple yet powerful means to analyze privacy-related quality properties like confidentiality. The analysis has been incorporated with the [Palladio Software Architecture Simulator](https://www.palladio-simulator.com/) and also provides various input and output formats as well as a textual domain-specific language (DSL) for the formulation of data flow constraints and queries. The research originates from the DSiS group, KASTEL Institute, Karlsruhe Institute of Technology (KIT) and is currently being driven by [Nicolas Boltz](https://dsis.kastel.kit.edu/staff_nicolas_boltz.php) and [Sebastian Hahner](https://dsis.kastel.kit.edu/staff_sebastian_hahner.php).

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
* S. Seifermann, R. Heinrich, and R. Reussner, "Data-Driven Software Architecture for Analyzing Confidentiality", in: *International Conference on Software Architecture (ICSA)*, IEEE, 2019, doi: [10.1109/ICSA.2019.00009](https://doi.org/10.1109/ICSA.2019.00009).


## Structure

*Work in Progress: This section will be updated with relevant information once all relevant repositories have been moved.*

## Extensions

*Work in Progress: This section will be updated with relevant information about [ABUNAI](https://github.com/abunai-dev) and [MDPA](https://github.com/Model-Based-Data-Protection-Assessments) once all relevant repositories have been moved.*

## Getting Started

*Work in Progress: This section will be updated with relevant information on the build and update site once all relevant repositories have been moved.*
