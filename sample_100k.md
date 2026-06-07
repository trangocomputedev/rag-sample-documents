POLITECNICO DI TORINO
SCUOLA DI DOTTORATO
Dottorato in Ingegneria Informatica e dell’Automazione – XXIV ciclo

Tesi di Dottorato

The Role of Semantic Web
Technologies in Smart
Environments

Faisal Razzak

Tutore
Prof. Fulvio Corno

Coordinatore del corso di dottorato
Prof. Pietro Laface

February 2013

to my Family

# Acknowledgements
I will start “In the name of GOD, the Most Gracious and the Most Merciful”. I
thank GOD for giving me objectives in life and more importantly, the strength and
the knowledge to achieve those objectives.
I feel great privilege and pleasure to extend my heartfelt thanks and sense of
gratitude to my family. From beginning my parents taught me the worth of one
simple, yet a powerful concept. The concept of seeking knowledge and achieving
wisdom. It separates us (humans) from other species. It has helped us evolve over
uncountable number of years and it will help us, in the future, to evolve further in
order to explore the vast universe around us, and to bring the ability to seek knowledge in other species. My wife has always been very understanding and supportive
of all my endeavors. No amount of words can describe the sense of gratitude, I feel
towards her.
Last but not the least, I would also like to acknowledge efforts of my supervisor
(Prof. Fulvio Corno) whose profound interest, guidance and encouragement helped
me in every aspect of my PhD. His active supervision and inspirational guidance
proved to be essential for the completion of this thesis. Furthermore, I appreciate
all the members of e-Lite Research group for their useful and constructive feedback
on several topics of interest. A special thanks to all the teachers who taught courses
during my 4 years of PhD degree.


# Contents
# Acknowledgements


# 1 Introduction
1.1 Contribution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
1.2 Structure of the Thesis . . . . . . . . . . . . . . . . . . . . . . . . . .




Background

# 2 Semantic Web Technologies
2.1 Resource Description Framework . . . . . . . . . . . . . . . . . . . .
2.1.1 Concepts of RDF . . . . . . . . . . . . . . . . . . . . . . . . .
2.1.2 Three Views of Statement . . . . . . . . . . . . . . . . . . . .
2.2 Ontology (OWL) . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
2.2.1 Why OWL? . . . . . . . . . . . . . . . . . . . . . . . . . . . .
2.2.2 OWL in a nutshell . . . . . . . . . . . . . . . . . . . . . . . .
2.3 SPARQL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
2.4 Linked Data . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .


# 3 DogOnt & Dog
3.1 DogOnt . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
3.1.1 Device Modeling in DogOnt . . . . . . . . . . . . . . . . . . .
3.2 Domotic OSGi Gateway . . . . . . . . . . . . . . . . . . . . . . . . .
3.2.1 Api . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
3.2.2 Device Control . . . . . . . . . . . . . . . . . . . . . . . . . .
3.2.3 Device Management . . . . . . . . . . . . . . . . . . . . . . .
3.2.4 StartUp . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
3.2.5 Library . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .




User Intelligible Goals


# 4 State of the art


# 5 Domotic Effects Framework
5.1 Requirements . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 41
5.2 Formalism . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 43
# 6 Modeling
6.1 Modeling: DogEffects Ontology . . . . . . . . . . . . . . . . . . . . .
6.1.1 Core layer . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
6.1.2 Middle layer . . . . . . . . . . . . . . . . . . . . . . . . . . . .
6.1.3 Instance layer . . . . . . . . . . . . . . . . . . . . . . . . . . .
6.2 Related Works . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .


# 7 Evaluation
7.1 Problem Statement . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.2 Approach . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.3 Solution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.3.1 Architecture . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.3.2 Extensibility . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.4 Experimental Study . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.4.1 Feasibility Testing . . . . . . . . . . . . . . . . . . . . . . . .
7.4.2 Performance Evaluation . . . . . . . . . . . . . . . . . . . . .
7.4.3 Discussion . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.5 Related Works . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.6 Synopsis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .


# 8 Enforcement
8.1 Problem Statement . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8.2 Approach . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8.3 Architecture . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8.3.1 Domotic Effect Enforcement . . . . . . . . . . . . . . . . . . .
8.3.2 Extensibility . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8.4 Experimental evaluation . . . . . . . . . . . . . . . . . . . . . . . . .
8.4.1 Use cases . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8.4.2 Results and Discussion . . . . . . . . . . . . . . . . . . . . . .
8.4.3 Extensibility and Scalability . . . . . . . . . . . . . . . . . . .
8.5 Related Works . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8.6 Synopsis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .



# 9 Optimization
9.1 Formalism . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 99
9.1.1 Representing Power with Domotic Effects . . . . . . . . . . . 99
9.1.2 Domotic Effect Enforcement . . . . . . . . . . . . . . . . . . . 99
9.2 Problem Statement . . . . . . . . . . . . . . . . . . . . . . . . . . . . 99
9.3 Proposed Approach . . . . . . . . . . . . . . . . . . . . . . . . . . . . 100
9.3.1 Heuristic . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 101
9.4 Experimental evaluation . . . . . . . . . . . . . . . . . . . . . . . . . 103
9.4.1 Use Cases . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 103
9.4.2 Results . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 106
9.4.3 Discussion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 109
9.5 Related Works . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 109
9.6 Synopsis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 110


Semantic Data Exchange


# 10 Motivation and Scenarios
10.1 Scenario 1: Home Energy Management System (HEMS) . . . . . . . 117
10.2 Scenario 2: 2020 Intelligent Energy Grids . . . . . . . . . . . . . . . . 117
# 11 Linked Open (Dynamic) Data
11.1 Problem Definition . . . . . . . . . . . . . . . . . . . . . . . . . . . . 122
11.2 Proposed Framework . . . . . . . . . . . . . . . . . . . . . . . . . . . 124
11.2.1 Publisher Component . . . . . . . . . . . . . . . . . . . . . . . 125
11.2.2 Subscriber Component . . . . . . . . . . . . . . . . . . . . . . 129
11.3 Use Case: Energy Management Domain . . . . . . . . . . . . . . . . 130
11.4 Related Works . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 132
11.5 Synopsis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 134
# 12 RDF Publishing
12.1 Design Issues . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 136
12.1.1 Energy Consumption Information . . . . . . . . . . . . . . . . 136
12.1.2 Publishing in a Machine Understandable format . . . . . . . . 137
12.1.3 Information Publishing Control . . . . . . . . . . . . . . . . . 137
12.2 Web Of Domotics (WoD) . . . . . . . . . . . . . . . . . . . . . . . . . 137
12.2.1 Domotics Gateway Controller (DGC) . . . . . . . . . . . . . . 138
12.2.2 WoD Dynamic DNS . . . . . . . . . . . . . . . . . . . . . . . 140
12.2.3 Mobility Access Provider . . . . . . . . . . . . . . . . . . . . . 140
12.2.4 Mobile Application . . . . . . . . . . . . . . . . . . . . . . . . 141
12.3 Proposed Solution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 142

12.3.1 Energy Profile Ontology (E.P) . . . . . . . . . . . . . . . . . . 143
12.3.2 Information Access Control . . . . . . . . . . . . . . . . . . . 145
12.3.3 Machine Understandable format . . . . . . . . . . . . . . . . . 145
12.4 Semantic Energy Information Publishing Framework (SEIPF) . . . . 147
12.4.1 Publishing Unit . . . . . . . . . . . . . . . . . . . . . . . . . . 149
12.5 Implementation and Experiments . . . . . . . . . . . . . . . . . . . . 150
12.6 Related Works . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 153
12.7 Synopsis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 154
# 13 Conclusion


# Bibliography


A Use cases


B Publications
B.1 International Journals . . . . . . . . . . . . . . . . . . . . . . . . . . 179
B.2 Proceedings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 179


# List of Tables
6.1 Dining@Lunch functional form . . . . . . . . . . . . . . . . . . . . . . 54
7.1 Results of the feasibility testing . . . . . . . . . . . . . . . . . . . . . 70
7.2 Daily chores scenario performance parameters . . . . . . . . . . . . . 79
7.3 Maximal Propagation Scenario Statistics . . . . . . . . . . . . . . . . 80
8.1 Illumination functional form (CE B ) . . . . . . . . . . . . . . . . . . . 83
9.1 Enumeration approach statistics (a) . . . . . . . . . . . . . . . . . . . 104
9.2 Enumeration approach statistics (b) . . . . . . . . . . . . . . . . . . . 105
9.3 Time comparison between enumeration & heuristic approaches . . . . 107
## 9.4 Power value comparison between enumeration & heuristic approaches 108
11.1 Energy Publisher Information . . . . . . . . . . . . . . . . . . . . . . 131
12.1 List of Parameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . 148
A.1 Secure Home use case . . . . . . . . . . . . . . . . . . . . . . . . . . . 172
A.2 Bathroom Illumination functional form . . . . . . . . . . . . . . . . . 173
A.3 Home Illumination use case . . . . . . . . . . . . . . . . . . . . . . . 174
A.4 Afternoon Lunch Cooking use case . . . . . . . . . . . . . . . . . . . 175
A.5 Air Passage use case . . . . . . . . . . . . . . . . . . . . . . . . . . . 176
A.6 Morning Wake Up use case . . . . . . . . . . . . . . . . . . . . . . . . 177


# List of Figures
2.1 RDF Triple Structure . . . . . . . . . . . . . . . . . . . . . . . . . . .
2.2 An example of Triple pattern . . . . . . . . . . . . . . . . . . . . . .
2.3 An example of Basic Graph Pattern . . . . . . . . . . . . . . . . . . .
2.4 Examples of Group Graph Pattern . . . . . . . . . . . . . . . . . . .
2.5 Sample RDF data . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
2.6 SPARQL Query . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
2.7 Result of the SPARQL query . . . . . . . . . . . . . . . . . . . . . .
2.8 Sample RDF data . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
2.9 SPARQL Query with FILTER construct . . . . . . . . . . . . . . . .
2.10 Result of the SPARQL query . . . . . . . . . . . . . . . . . . . . . .
2.11 An example of FILTER Construct . . . . . . . . . . . . . . . . . . . .
2.12 An example of OPTIONAL graph pattern . . . . . . . . . . . . . . .
2.13 An example of UNION graph pattern . . . . . . . . . . . . . . . . . .
2.14 An example of UNION graph pattern . . . . . . . . . . . . . . . . . .
3.1 DogOnt top-level concepts. . . . . . . . . . . . . . . . . . . . . . . . .
3.2 Dimmer Lamp in DogOnt . . . . . . . . . . . . . . . . . . . . . . . .
3.3 Dog core bundles . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
4.1 User Goal Modeling . . . . . . . . . . . . . . . . . . . . . . . . . . . .
5.1 The DomoticEffects framework - Logic Architecture. . . . . . . . . .
5.2 SE and CE effects in the energy domain . . . . . . . . . . . . . . . .
5.3 SE and CE effects in the control domain . . . . . . . . . . . . . . . .
6.1 The DogEffects middle layer - Boolean Control Domain . . . . . . . .
6.2 The DogEffects middle layer - Energy Saving Domain . . . . . . . . .
6.3 “Illumination” use case (DogEffects Ontology) . . . . . . . . . . . . .
6.4 “ Dining@Lunch” use case (DogEffects Ontology) . . . . . . . . . . .
7.1 Evaluation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.2 ENN for the Dining@Lunch use case . . . . . . . . . . . . . . . . . .
7.3 Information template . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.4 DogEffects bundle . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7.5 Procedure to define a new effect operator. . . . . . . . . . . . . . . .
7.6 Template of abstract EffectNode Class . . . . . . . . . . . . . . . . .


7.7 Action Sequence of Feasibility Testing. . . . . . . . . . . . . . . . . . 67
7.8 A Sample Structure of a house. . . . . . . . . . . . . . . . . . . . . . 69
7.9 Relationship b/w Average Evaluation Time & Total No. of DEs . . . 72
## 7.10 Relationship b/w Average Evaluation Time & Maximum level of ENN 72
7.11 Semantics of Effect Evaluation process in Experiment 1. . . . . . . . 73
7.12 Semantics of Effect Evaluation process in Experiment 2. . . . . . . . 74
## 7.13 Relationship between Average Evaluation Time & Total No. of DEs . 74
7.14 Average evaluation time, ENN levels & No. of DEs comparison . . . . 76
8.1 Enforcement . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 81
8.2 Domotic Effect Enforcement Architecture . . . . . . . . . . . . . . . . 85
8.3 Procedure to define a new effect operator. . . . . . . . . . . . . . . . 86
8.4 CPU time measurements (in ms, CT+ST) . . . . . . . . . . . . . . . 90
8.5 Number of solutions T C and involved devices Dev . . . . . . . . . . . 92
9.1 Architecture of proposed approach . . . . . . . . . . . . . . . . . . . 100
11.1 Architecture of the Framework . . . . . . . . . . . . . . . . . . . . . . 124
11.2 Publisher Ontology: Core layer . . . . . . . . . . . . . . . . . . . . . 127
11.3 Publisher Ontology: Energy Management domain . . . . . . . . . . . 128
11.4 University Metering System Use Case software infrastructure . . . . . 130
11.5 A snapshot of the Desktop Monitoring Application . . . . . . . . . . 133
12.1 The WoD reference architecture. . . . . . . . . . . . . . . . . . . . . . 138
12.2 Mobile Access Provider . . . . . . . . . . . . . . . . . . . . . . . . . . 141
12.3 Energy Profile Ontology . . . . . . . . . . . . . . . . . . . . . . . . . 143
## 12.4 An excerpt of the power consumption information about a device . . 145
12.5 SimpleDomoticData excerpt for a device’s energy consumption . . . . 147
12.6 Publishing Framework Architecture . . . . . . . . . . . . . . . . . . . 148
12.7 BTicino and KNX Domotic demo cases . . . . . . . . . . . . . . . . . 151
12.8 Current Power Consumption of Emulated Devices . . . . . . . . . . . 151
12.9 Power consumption snapshot obtained on COSM . . . . . . . . . . . 152

xi

Chapter 1
Introduction
In the last decade, both the industry and academia have focused on brining two
important and necessary changes in the global IT scene. The first change was the
ubiquity of computing technology for general masses, which mainly helped trigger
the second change; the advent of intelligent/personalized services for individuals
within general masses. The former effort is being driven by models of Ubiquitous
computing, Pervasive computing, Internet of Things etc. While, the latter effort is
driven by methods of artificial intelligence, i.e., enriching the available data, and
using algorithms or heuristics to bring intelligence.
On one hand, the drive to make intelligent distributed applications on a global
scale has provided impetus to the adoption of explicit semantic modeling of concepts
represented in web documents, and in general information systems. The semantic
modeling of concepts ensures that the data is machine readable, processable and
widely accessible. Semantic Web envisions the availability of semantically enriched
data on a large scale and it was put forward by Tim-Berners Lee [1]. In the beginning, different architectures ranging from a layered approach [2] to a tower based
approach [3] were proposed for the development of semantic web specifications and
applications. However, in recent years (post 2006) the vision of semantic web has
shifted from a traditional “logic+reasoning” approach, mainly proposed by research
groups coming from classical artificial intelligence community, to a more pragmatic
and engineered approach of having shared data semantics, and a web of data derived
from it. The proponents of engineered approach argue that intelligent agents can
flourish once languages, formalism and standards for data semantics and integration
are defined [4].
Focusing on the need of data semantics, standard organizations like the Internet
Engineering Task Force (IETF) and the World Wide Web Consortium (W3C) have
put major effort at specifying, developing, and deploying languages for defining and
sharing meaning of data. Hence, providing a technological foundation for semantic

1 – Introduction

interoperability. This technological foundation mainly consists of Resource Description Framework (RDF) [5], Resource Description Framework - Schema (RDFS) [6],
Ontology Web Language (OWL) [7], and SPARQL query language [8].
While the aforementioned technologies provide formalism for data semantics, the
integration of data on a global-scale is achieved by using Linked Data (LD) [9]. LD
approach [10] is based on Linking (i.e., using the RDF for creating references to information stored in different databases) Open Data (i.e., information freely retrievable
in RDF format through the SPARQL query language over the http protocol). The
simplicity of the LD approach stimulated the quick and enormous growth of the
number of data set providers joining the initiative1 . Formally, Linked Data is used
to describe recommended best practices for exposing, sharing, and connecting pieces
of data, information and knowledge over the web using URIs and RDF.
On the other hand, the emergence of economically viable and efficient sensor
technology, that can be integrated with appliances, has enabled system designers to
build smart environments [11]. The term “smart” refers to increased connectivity
among diverse elements of the environment and to give users intelligent services.
In literature, the vision of Smart Environments has been around since 1991 and
was first proposed by Mark Wiser in his paper [12]. He anticipated environments
interwoven with sensors, actuators, displays and computational elements, embedded
seamlessly in our every day lives and connected through a network.
Today our daily spaces are filled with sensors, device and computational gadgets
that measure or generate unstructured data over time, consequently presenting a
two-front opportunity for system designers and integrators. The first is by acting
on these islands of unstructured data and transforming them into structured data
with semantics. The outcome will be to enable automated and intelligent agents
to extract and act on the structured data. The second opportunity is to develop
automated and intelligent agents that can process the structured data and provide
some intelligent services to the users. Semantic web technologies have the potential to provide support for the representation of structured data, explicit context
representation, expressive context querying, and flexible context reasoning [13].
This thesis outlines the role of semantic web technologies in smart environments
like smart homes and smart energy systems. The potential of semantic web technologies in addressing some of the problems in smart environments is studied by
proposing some solutions.


http://richard.cyganiak.de/2007/10/lod


## 1.1 – Contribution

1.1

Contribution

This thesis makes two major contributions in the context of smart environments.
The first comes in the form of a Domotic Effects framework, which provides the
ability to control and monitor a smart environment in terms of user intelligible
goals. The second contribution of the thesis is to describe mechanisms for exchanging
semantically enriched data in a smart environment.
Bader et al. [14] described smart environments as heterogeneous dynamic ensembles: group of co-located devices of different device types, which evolve over
time. The presence of diverse devices and the associated complexity has given rise
to a major problem in the past years, i.e., the problem of providing users with the
ability to control and manage their respective environments. The first major contribution of this thesis is to provide users with the ability to control and monitor
their respective environments in terms of user intelligible goals. As acknowledged
in [15], this research trend has received little attention. A “Domotic Effects” (DE)
framework is being proposed. It models user intentions or goals in an environment,
and it provides a unified model for both control and monitoring. The framework
has several novelties.
First, at the modeling level, it addresses both the concerns of end-users and
system designers using a unified model. End-users have the ability to define their
spaces according to their intentions. On the other hand, system designers have
the flexibility to define governing rules for diverse smart environments, at a generic
level. The modeling is provided using a new “DogEffects” ontology. It is scalable
and extensible depending on the smart environment.
Second, at the monitoring level, users have the ability to monitor their respective
environments in terms of their intentions or goals, in near real-time. The novelty
comes from the ability to monitor each and every device in the environment and
then presenting a bigger picture to the user, i.e., pre-defined user goal. It is among
the few approaches present in the literature that provides a complete picture, i.e.,
conception, architecture, implementation and experimentation using use cases.
Third, at the control level, users have the ability to control their respective
environments by automatically enforcing their intentions or goals in near real-time.
It is among the few approaches present in the literature that provides a complete
picture, i.e., conception, architecture, implementation and experimentation using
use cases. The enforcement mechanism itself is also novel.
Extending the work at the control level, the DE framework also provides the
provision of optimizing enforcement with some criteria, in near real-time. In this
thesis, energy optimization is considered as the criteria. A novel heuristic is proposed
and tested for energy optimization.
The second major contribution of this thesis comes within the context of Energy
Management System (EMS). Two novel mechanisms are proposed for the exchange

1 – Introduction

of semantically enriched data. In recent years, the energy management has become a
key requirement for smart environments. Managing energy needs is a rising concern
these days for many countries around the world. The resources needed to generate
energy, their scarcity and the rising impact of those resources on the global environment have made energy management a top agenda on the tables of high government
officials around the world. An approach to this energy management issue is “Demand Side Management”, proposed by the Smart Grid community [16] which allows
customers to make informed decisions regarding their energy consumption, by adjusting both the timing and quantity of their electricity consumption [16, 17]. This
flexibility is enabled by pricing policies for electricity consumption over time [18,19]
and/or by dynamic demand scheduling algorithms to optimize energy services in
buildings [20]. Such scenarios underscore the need in which the appliances can share
the information about the energy usage with their energy provider. EMS provides
a complementary approach to energy management in an environment by providing
graphical illustrations [21–23] of consumed energy to ease consumer understanding,
hence making an energy conscious society.
First, a novel ontology driven framework based on the publisher-subscriber pattern [24], called LO(D)D2 is presented. LO(D)D is a light-weight publishing framework that can be integrated with smart environments to expose semantically annotated sensor’s or device’s data being continuously updated. This work is done
in the context of SMILE-O project3 . LO(D)D is inspired from the lessons learned
during the development of an earlier publishing framework called Semantic Energy
Information Publishing Framework (SEIPF). SEIPF has a client-server based architecture that is able to expose power consumed by different appliances installed
in an environment, in a machine understandable format (using SPARQL endpoint),
to support the development of 3rd party applications. It presents a novel ontology
based modeling mechanism for encoding power consumption of appliances in different states and then uses Linked Data principles to expose the data. This thesis
includes complete details from conception to experimentation of both frameworks.
Both the aforementioned mechanisms underline the need to have energy consumption details in a semantically enriched format and accessible on a global-scale,
in a structured format. Thus, enabling the energy provider or third party services to
utilize this information in order to provide better graphical illustrations, to design
better pricing policies and to perform dynamic demand scheduling.


Linked Open (Dynamic) Data


http://www.smile-o.org (a Regione-Piemonte project)


## 1.2 – Structure of the Thesis

1.2

Structure of the Thesis

The remainder of this thesis is organized into three parts, consisting of twelve chapters.
For the easy comprehension of thesis, Part I describes the underlying concepts
and technologies and comprises two chapters. Chapter 2 introduces different Semantic Web standards and technologies which are used in the design of User Intelligible Goals and Semantic Data Exchange. Chapter 3 briefly define technologies
used to represent and emulate a smart environment.
Part II consists of six chapters describing user intelligible goals in smart environments. Chapter 4 presents the state-of-the-art and makes the case for designing
user intelligible goals. Chapter 5 introduces the DE framework for modeling user
intelligible goals. Formally, the modeling is explicated in Chapter 6. Chapter 7
and Chapter 8 move in parallel and contain details of conception, architecture and
implementation of Evaluation and Enforcement, respectively. Chapter 9 extends
the work in the preceding chapter and discusses the privilege of advanced intelligent
support in DE framework, in the context of energy management domain.
Part III consists of three chapters addressing the issue of semantic data exchange in smart environments. Chapter 10 describes the need of semantic data
exchange in smart environments. The case of energy management domain is specifically considered. In order to support the development of 3rd party applications
two frameworks are presented. Chapter 11 presents an ontology driven framework, called LO(D)D. LO(D)D gives smart sensing and measuring environments
the ability to expose semantically annotated sensor’s or device’s data being continuously updated; such updates might be issued at specific time intervals or be bound
to some environment-specific event. Chapter 12 presents a Semantic Energy Information Publishing Framework (SEIPF). SEIPF uses RDF publishing to enable
residential gateways to expose power consumed by different appliances installed in
a house to support the development of external applications.
In the end, Chapter 13 concludes the thesis and provides possible future directions.


Part I
Background

Chapter 2
Semantic Web Technologies
This dissertation discusses the role of semantic web technologies’ in smart environments. In order to develop a better and shared understanding on the topic, this
chapter briefly highlights key Semantic Web technologies and concepts.
Semantic Web is often described as a web of data; it creates a universal medium
for the exchange of data [25]. It envisions an automated negotiation and retrieval
of machine understandable information among web applications, services and intelligence agents. This chapter discusses several key technologies that are developed
by World Wide Web Consortium (W3C) to achieve the vision of Semantic Web.

2.1

Resource Description Framework

RDF [26] is a data model that is used to describe resources over the web. Its basic
building block is an object-attribute-value triple, called a statement. XML syntax [27]
is popularly used to represent and transmit RDF data model. However, other textual
representations like Turtle1 and Notation32 are also being used increasingly by the
Semantic Web community. In RDF, no assumptions about a particular domain of
use is made and therefore, RDF is domain independent in nature. It is up to the
users to define their own terminology in a schema language called RDF Schema
(RDFS). RDFS defines the terms that can be used in a RDF data-model. RDFS
can specify which objects exist and which properties can be applied to them, and
what values they can take.


http://www.w3.org/TR/turtle


http://www.w3.org/TeamSubmission/n3


2 – Semantic Web Technologies

2.1.1

Concepts of RDF

Resources
A resource can be described as an object or a thing that need to be described.
Resources may be authors, books, events, peoples, rooms, search queries, devices,
and so on. Every resource has a URL, a Universal Resource Identifier. A URI
can be a URL (Unified Resource Locater or Web address) or some other kind of
unique identifier. URI schemes are defined not only for web locations but also
for diverse objects like telephone numbers, ISBN numbers and geographic locations.
The discussion on URI schemes is beyond the scope of thesis. In short, it is assumed
that a URI is a unique identifier of a resource.
Properties
Properties are special kind of resources; they describe relationship between resources,
for instance “written by”,“generated by”, “author”, “title”, and so on. In RDF,
properties are also described by URIs (and in practice URLs). The choice of using
URLs (for both resources and properties) gives users the opportunity to adopt a
global, worldwide and unique naming scheme.
Statements
Statements represent the properties of resources. A statement is an object-attributevalue triple, consisting of a resource, a property and a value. A Value can either be
a resource or a literal. Literals are atomic values (string), that can have a specific
XSD type3 .

2.1.2

Three Views of Statement

Consider a statement:
Faisal is the owner of the web page “http://polito.academia.edu/FaisalRazzak”
The simplest way to represent the preceding statement is to use the definition of
a triple and encode the statement as (“http://polito.academia.edu/FaisalRazzak”,
“http://www.mydomain.com/site-owner”,“Faisal”). This triple (x, P, y) can be represented as a logical formula P(x,y), where the binary predicate P relates the object
x to the value y. In fact, RDF only supports binary predicates.

http://www.w3.org/TR/xmlschema-2


## 2.2 – Ontology (OWL)

site-owner

Faisal

http://polito.academia.edu/FaisalRazzak

Figure 2.1.

RDF Triple Structure

The second view of the statement is the graph model (Figure 2.1). It is a directed
graph with labeled nodes and arcs; the arcs are directed from the resource (the
subject of the statement) to the value (the object of the statement). This kind of
graph is known in the Artificial Intelligence community as a semantic net.
Graphs are a powerful tool for human understanding, but the Semantic Web
vision requires machine accessible and machine processable representations. Therefore, thee is a third representation possibility based on XML. According to this possibility, an RDF document is represented by an XML element with the rdf rdf:RDF.
The content of this element is a number of descriptions, which use rdf:Description
tags. Every description makes a statement about a resource.

<?xml version=”1.0” encoding=”UTF-8”?>
<rdf:RDF
xmlns:rdf=”http://www.w3.org/1999/02/22-rdf-syntax-ns#”
xmlns:mydomain=”http://www.mydomain.net/my-rdf-ns”>
<rdf:Description about=”http://polito.academia.edu/FaisalRazzak”>
<mydomain:site-owner>
Faisal
</mydomain:site-owner>
</rdf:Description>
</rdf:RDF>

2.2

Ontology (OWL)

To capture domain knowledge in a generic way, and provide a commonly agreed
understanding of a domain, which may be reused and shared across applications and
groups, the concept of Ontology is used. An ontology is a formal specification of a
shared conceptualization [28]. W3C provides the Ontology web Language (OWL)
to describe ontologies about a particular domain [29]. OWL has three increasinglyexpressive sub languages: OWL Lite, OWL DL, and OWL Full.

2 – Semantic Web Technologies

2.2.1

Why OWL?

The expressiveness of RDF and RDFS is very limited (and this is a deliberate
choice): RDF is roughly limited to model binary relationships and RDF-S is limited
to sub-class hierarchies and property hierarchies, with restrictions on the domain
and range of the lasts.
However a number of research groups have identified different characteristic usecases for the Semantic Web that would require much more expressiveness than RDF
and RDF-S offer. Initiatives from both Europe and United States came up with
proposals for richer languages, respectively named OIL and DAML-ONT, whose
merging DAML+OIL was taken by the W3C as the starting point for the Web
Ontology Language OWL.
Ontology languages must allow users to write explicit, formal conceptualizations
of domain knowledge, the main requirements are therefore:
• a well defined syntax,
• a formal semantics,
• an efficient reasoning support,
• a sufficient expressive power,
• a convenience of expression.
The importance of a well-defined syntax is clear, and known from the area of programming languages: it is a necessary condition for “machine understandability”
and thus for machine processing of information. Both RDF/RDF-S and OWL have
this kind of syntax. A formal semantics allows to describe the meaning of knowledge
precisely. Precisely means that semantics does not refer to subjective intuitions and
is not open to different interpretations by different people (or different machines).
The importance of a formal semantics is well known, for example, in the domain of
mathematical logic. Formal semantics is needed for allowing people to reason about
knowledge. This, for ontologies, means that we may reason about:
• Class membership. If x is an instance of a class C, and C is a subclass of D,
we can infer that x is also an instance of D.
• Equivalence of classes. If a class A is equivalent to a class B, and B is equivalent to C, then A is equivalent to C, too.
• Consistency. Let x be an instance of A, and suppose that A is a subclass of
B ∩ C and of D. Now suppose that B and D are disjoint. There is a clear
inconsistence in our model because A should be empty but has the instance
x. Inconsistencies like this indicate errors in the ontology definition.

## 2.2 – Ontology (OWL)

• Classification. If we have declared that certain property-value pairs are sufficient conditions for membership in a class A, then if an individual (instance)
x satisfies such conditions, we can conclude that x must be an instance of A.
Semantics is a prerequisite for reasoning support. Derivation such as the preceding ones can be made by machines instead of being made by hand. Reasoning is
important because allows to:
• check the consistency of the ontology and of the knowledge model,
• check for unintended relationships between classes,
• automatically classify instances.
Automatic reasoning allows to check much more cases than could be checked manually. Such checks become critical when developing large ontologies, where multiple
authors are involved, as well as when integrating and sharing ontologies from various
sources.
Formal semantics is obtained by defining an explicit mapping between an ontology language and a known logic formalism, and by using automated reasoners that
already exist for that formalism. OWL, for instance, is (partially) mapped on description logic, and makes use of existing reasoners such as Fact, Pellet and RACER.
Description logics are a subset of predicate logic for which efficient reasoning support
is possible.

2.2.2

OWL in a nutshell

OWL documents are usually called OWL ontologies. Since they are built on RDF
and RDFS, they are essentially RDF documents. The following sections explain key
elements of an OWL document.
Header
The root element of an ontology is an rdf:RDF element, which specifies a number
of namespaces:
<rdf:RDF
xmlns:owl = ”http://www.w3.org/2002/07/owl#”
xmlns:rdf = ”http://www.w3.org/1999/02/22-rdf-syntax-ns#”
xmlns:rdfs = ”http://www.w3.org/2000/01/rdf-schema#”
xmlns:xsd = ”http://www.w3.org/2001/XMLSchema#”>


2 – Semantic Web Technologies

An OWL ontology can start with a set of assertions for house keeping purpose. These
assertions are grouped under an owl:Ontology element, which contains comments,
version control, and inclusion of other ontologies.
<owl:Ontology rdf:about=”http://elite.polito.it/ontologies/simpleHomeEffects.owl”>
<rdfs:comment>A sample Ontology </rdfs:comment>
<owl:priorVersion
rdf:resource=”http://elite.polito.it/ontologies/effectsOld.owl”/>
<owl:imports
rdf:resource=”http://elite.polito.it/ontologies/effects.owl”/>
<rdfs:label>Domotic Effects</rdfs:label>
</owl:Ontology>
The most important of the above assertions is the owl:imports, which lists other
ontologies whose content is assumed to be part of the current ontology. It is important to be aware that the owl:imports is a transitive property: if the ontology A
imports the ontology B, and the ontology B imports the ontology C, then A is also
importing C.
Classes
Classes are defined using the owl:Class element and can be organized in hierarchies
by means of the rdfs:subClassOf construct.
<owl:Class rdf:ID=”associateProfessor”>
<rdfs:subClassOf rdf:resource=”#academicStaffMember”/>
</owl:Class>
It is also possible to indicate that two classes are completely disjoint such as the
associateProfessor,assistantprofessor and the Professor, using the owl:disjointWith
construct.
<owl:Class rdf:about=”#associateProfessor”>
<owl:disjointWith rdf:resource=”#assistantProfessor”/>
<owl:disjointWith rdf:resource=”#Professor”/>
</owl:Class>
Equivalence of classes may be defined using the owl:equivalentClass element.
<owl:Class rdf:ID=”#faculty”>
<owl:equivalentClass rdf:resource=”#academicStaffMember”/>
</owl:Class>

## 2.2 – Ontology (OWL)

Eventually there are two predefined classes, owl:Thing and owl:Nothing, which,
respectively, indicate the most general class containing everything in a OWL document, and the empty class. As a consequence, every owl:Class is a subclass of
owl:Thing and a superclass of owl:Nothing.
Properties
In OWL are defined two kinds of properties:
• Object properties, which relate objects to other objects. Example are isTaughtBy
and supervises relationships.
• Datatype properties, which relate objects with datatype values. Examples are
age, name, and so on. OWL has not any predefined data types, nor does it
provide special definition facilities. Instead, it allows the use of XML-Schema
data types.
Here there are two examples, the first for a Datatype property while the second is
for Object properties:
<owl:DatatypeProperty rdf:ID=”age”>
<rdfs:range rdf:resource=”&xsd;#nonNegativeInteger”/>
</owl:DatatypeProperty>

<owl:ObjectProperty rdf:ID=”isTaughtBy”>
<rdfs:domain rdf:resource=”#course”/>
<rdfs:range rdf:resource=”#academicStaffMember”/>
</owl:ObjectProperty>
Restrictions on properties
In RDFS it is possible to declare a class C as a subclass of a class C 0 , then every
instance of C will be also an instance of C 0 . OWL allows to specify classes C 0
that satisfy some precise conditions, i.e., all instances of C satisfy the conditions.
This is done by defining C as a subclass of the class C 00 which collects all the
objects that satisfy the conditions. In general, C 00 remains anonymous. In OWL
there are three specific elements for defining classes basing on restrictions, they
are owl:allValuesFrom, owl:someValuesFrom and owl:hasValue, and they are
always nested into a owl:Restriction element. The owl:allValuesFrom specify a
universal quantification (∀). For example, the following element requires first-year
courses to be taught by Professors only.

2 – Semantic Web Technologies

<owl:Class rdf:about=”#firstYearCourse”>
<rdfs:subClassOf>
<owl:Restriction>
<owl:onProperty rdf:resource=”#isTaughtBy”/>
<owl:allValuesFrom
rdf:resource=”#Professor”/>
</owl:Restriction>
</rdfs:subClassOf>
</owl:Class>
The owl:someValuesFrom defines an existential quantification (∃). For example,
there exist an undergraduate course taught by an instance of the class of academic
staff members (existential quantification).
<owl:Class rdf:about=”#academicStaffMember”>
<rdfs:subClassOf>
<owl:Restriction>
<owl:onProperty rdf:resource=”#teaches”/>
<owl:someValuesFrom
rdf:resource=”#undergraduateCourse”/>
</owl:Restriction>
</rdfs:subClassOf>
</owl:Class>
The owl:hasValue defines a specific value that the property must have. In
general an owl:Restriction element contains an owl:onProperty element and
one ore more restriction declarations. Restrictions for defining the cardinality of a
given class are also supported through the elements:
• owl:minCardinality,
• owl:maxCardinality,
• owl:Cardinality.
The latter is a shortcut for a cardinality definition in which owl:minCardinality
and owl:maxCardinality assume the same value.
Special properties
Some properties of the property element can be defined directly:
• owl:TransitiveProperty defines a transitive property, such as “has better
grade than”, “is older than”, etc.

## 2.2 – Ontology (OWL)

• owl:SymmetricProperty defines a symmetric property, such as “has same
grade as” or “is sibling of”.
• owl:FunctionalProperty defines a property that has at most one value for
each object, such as “age”, “height”, “directSupervisor”, etc.
• owl:InverseFunctionalProperty defines a property for which two different
objects cannot have the same value, for example “is identity ID for”.
Instances
Instances of classes, in OWL, are declared as in RDF:
<rdf:Description rdf:ID=”160850”>
<rdf:type rdf:resource=”#academicStaffMember”/>
</rdf:Description>
OWL, unlike typical database systems, does not adopt a unique-names assumption therefore two instances that have different names are not required to be actually
two different individuals. Then, to ensure that different individuals are recognized
by automated reasoners as such, inequality must be explicitly asserted.
<lecturer rdf:ID=”160850”>
<owl:differentFrom rdf:resource=”#187833”/>
</lecturer>
Because such inequality statements frequently occur, and the required number of
statements would explode for stating the inequality of a large number of individual,
OWL provides a shorthand notation to assert the pairwise inequality for all the
individuals in a list: owl:AllDifferent.
<owl:AllDifferent>
<owl:distinctMembers rdf:parseType=”Collection”>
<lecturer rdf:about=”#160850”/>
<lecturer rdf:about=”#187833”/>
<lecturer rdf:about=”#160596”/>
</owl:distinctMembers>
</owl:AllDifferent>
Note that owl:distinctMembers can only be used in combination with the
owl:AllDifferent element.

2 – Semantic Web Technologies

2.3

SPARQL

The SPARQL Protocol and RDF Query Language (SPARQL) is a query language
and protocol for RDF [8]. The protocol allows a SPARQL endpoint which acts as
a gateway for RDF knowledge base. On the other hand, the query language is used
to retrieve and manipulate data stored in RDF format. SPARQL permits four kind
of queries, i.e., SELECT, ASK, CONSTRUCT and DESCRIBE queries. SELECT
queries is used to extract raw values from the RDF information and the results are
returned in a table format. CONSTRUCT query is used to extract information
from the SPARQL endpoint and transform the results into valid RDF. ASK query
is used to provide a simple True/False result for a query on a SPARQL endpoint.
DESCRIBE query is Used to extract an RDF graph from the SPARQL endpoint,
the contents of which is left to the endpoint to decide based on what the maintainer
deems as useful information.
SPARQL is based on matching graph patterns against RDF graphs. In order to
define graph pattern, we must first define triple patterns. A triple pattern is like
an RDF triple, but with the option of a variable in place of RDF terms, i.e., IRIs,
literals or blank nodes, in the subject, predicate or object positions. For example,
“?title” represents a variable in the triple pattern shown in Figure 2.2.
<ht t p : / / example . o r g / book / book1>
<ht t p : / / p u r l . o r g / dc / e l e m e n t s / 1 . 1 / t i t l e > ? t i t l e .
Figure 2.2.

An example of Triple pattern

There are four elementary graph patterns over which group graph patterns can
be defined. They are i) BASIC graph pattern ii) FILTER graph pattern iii) OPTIONAL graph pattern iv) ALTERNATIVE graph pattern .
A BASIC graph pattern (BGP) is a set of triple patterns written as a sequence
of triple patterns (separated by a period if necessary). A BGP is understood as the
conjunction of its triple patterns. See Figure 2.3 for a BGP example.
?x f o a f : name ?name . ?x f o a f : mbox ?mbox
Figure 2.3.

An example of Basic Graph Pattern

A group graph pattern is a set of graph patterns delimited with braces {}.
Figure 2.4 shows examples of group graph patterns. All of them are equivalent
since they are only made of BGPs and therefore, these patterns are interpreted
conjunctively.

## 2.3 – SPARQL

{ ?x f o a f : name ?name . ?x f o a f : mbox ?mbox }
or
{ ?x f o a f : name ?name . ?x f o a f : mbox ?mbox . }
or

{ { ?x f o a f : name ?name . }
{ ?x f o a f : mbox ?mbox . } }
Figure 2.4.

Examples of Group Graph Pattern

A SPARQL query matches variables against its values in the data. Consider the
RDF data shown in Figure 2.5. The SPARQL SELECT query (Figure 2.6) matches
the values of the variables request in the query construct (?name and ?mbox) from
the RDF data. The result of the query is shown in Figure 2.7.
@ p r e f i x f o a f : <ht t p : / / xmlns . com/ f o a f /0.1/ > .
_: a f o a f : name " Johnny Lee Outlaw " .
_: a f o a f : mbox <m a i l t o : jlow@example . com> .
_: b f o a f : name " P e t e r Goodguy " .
_: b f o a f : mbox <m a i l t o : peter@example . org> .
_: c f o a f : mbox <m a i l t o : carol@example . org> .
Figure 2.5.

Sample RDF data

PREFIX f o a f : <ht t p : / / xmlns . com/ f o a f /0.1/ >
SELECT ?name ?mbox
WHERE { ?x f o a f : name ?name . ?x f o a f : mbox ?mbox }
Figure 2.6.

SPARQL Query

The FILTER construct restricts variable bindings to those for which the filter
expression evaluated to TRUE. Figure 2.9 shows a SPARQL SELECT query with
a filter construct, over the data (Figure 2.8). The result is shown in Figure 2.10.
Another example is shown in Figure 2.11.
The OPTIONAL graph pattern matching allows information to be added to the
answer where the information is available, but do not reject the answer because

2 – Semantic Web Technologies

?name
?mbox
−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−
P e t e r Goodguy
<m a i l t o : peter@example . org>
Johnny Lee Outlaw <m a i l t o : jlow@example . com>
Figure 2.7.

Result of the SPARQL query

@ p r e f i x dc : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.1/ > .
@ p r e f i x : <ht t p : / / example . o r g / book/> .
@ p r e f i x ns : <ht t p : / / example . o r g / ns#> .
: book1 dc : t i t l e "SPARQL T u t o r i a l " .
: book1 ns : p r i c e 42 .
: book2 dc : t i t l e " The Semantic Web" .
: book2 ns : p r i c e 23 .
Figure 2.8.

Sample RDF data

some part of the query pattern does not match. if the optional part does not
match, it creates no bindings but does not eliminate the solution. Figure 2.12 shows
an example of SPARQL SELECT query with OPTIONAL graph pattern and its
associated data and results.
SPARQL provides a means of forming the disjunction of graph patterns so that
one of several ALTERNATIVE graph patterns may match. If more than one of the
alternatives match, all the possible pattern solutions are found. Pattern alternatives
are syntactically specified with the keyword UNION. Figure 2.13 and Figure 2.14
show examples of SPARQL SELECT query with UNION graph pattern and its
associated data and results.
For more detailed insight on SPARQL, readers are referred to [8, 30–32].

PREFIX dc : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.1/ >
PREFIX ns : <ht t p : / / example . o r g / ns#>
SELECT ? t i t l e ? p r i c e
WHERE { ?x ns : p r i c e ? p r i c e .
FILTER ( ? p r i c e < 3 0 . 5 )
?x dc : t i t l e ? t i t l e . }
Figure 2.9.

SPARQL Query with FILTER construct


## 2.4 – Linked Data

? title
? price
−−−−−−−−−−−−−−−−−−−−−−−−−−−−
The Semantic Web
Figure 2.10.

Result of the SPARQL query

Query :
PREFIX dc : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.1/ >
SELECT ? t i t l e
WHERE { ?x dc : t i t l e ? t i t l e
FILTER r e g e x ( ? t i t l e , "^SPARQL" )
}
Result :
? title
−−−−−−−−−−−−−−−−−−−−
SPARQL T u t o r i a l
Figure 2.11.

2.4

An example of FILTER Construct

Linked Data

According to Tim Berners-Lee’s web architecture note [9], the Semantic web is
not just about exposing machine understandable information over the Internet but
making links between different exposed information sets, so that a machine, an
application, a service or a person can find related information. The availability of
data from different sources in a universal format and linked together is known as
‘Linked Data’. Linked Data4 (LD) assumes that information is available in RDF
format.
The term Linked Data refers to a set of best practices for publishing and interlinking structured data on the Web. Tim Berners-Lee presented following Linked
Data principles:
1. Use URIs as names for things.
2. Use HTTP URIs, so that people can look up those names.

http://linkeddata.org


2 – Semantic Web Technologies

Data :
@ p r e f i x f o a f : <ht t p : / / xmlns . com/ f o a f /0.1/ > .
@ p r e f i x r d f : <ht t p : / /www. w3 . o r g /1999/02/22 − r d f −synt a xns#>
.
_: a r d f : type f o a f : Person .
_: a f o a f : name " A l i c e " .
_: a f o a f : mbox <m a i l t o : a lice@ exa mp le . com> .
_: a f o a f : mbox <m a i l t o : a lice@ wo r k . example> .
_: b r d f : type f o a f : Person .
_: b f o a f : name " Bob " .
Query :
PREFIX f o a f : <ht t p : / / xmlns . com/ f o a f /0.1/ >
SELECT ?name ?mbox
WHERE { ?x f o a f : name ?name .
OPTIONAL { ?x f o a f : mbox ?mbox }
}
Result :

?name
?mbox
−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−
Alice
<m a i l t o : a lice@ exa mpl e . com>
Alice
<m a i l t o : a lice@ wo r k . example>
Bob
Figure 2.12.

An example of OPTIONAL graph pattern

3. When someone looks up a URI, provide useful information, using the standards
(RDF, SPARQL).
4. Include links to other URIs, so that they can discover more things.
Linked Data builds directly on Web architecture [33] and applies this architecture
to the task of sharing data on global scale. it intends to transform the current Web
in to a Web of Data. For more details, readers are referred to [10, 34].


## 2.4 – Linked Data

Data :
@ p r e f i x dc10 : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.0/ > .
@ p r e f i x dc11 : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.1/ > .
_: a dc10 : t i t l e "SPARQL Query Language T u t o r i a l " .
_: a dc10 : c r e a t o r " A l i c e " .
_: b dc11 : t i t l e "SPARQL P r o t o c o l T u t o r i a l " .
_: b dc11 : c r e a t o r " Bob " .
_: c dc10 : t i t l e "SPARQL" .
_: c dc11 : t i t l e "SPARQL ( updated ) " .

Query :
PREFIX dc10 : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.0/ >
PREFIX dc11 : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.1/ >
SELECT ? t i t l e
WHERE { { ? book dc10 : t i t l e ? t i t l e }
UNION
{ ? book dc11 : t i t l e ? t i t l e }
}
Result :
? title
−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−
SPARQL P r o t o c o l T u t o r i a l
SPARQL
SPARQL ( updated )
SPARQL Query Language T u t o r i a l
Figure 2.13.

An example of UNION graph pattern


2 – Semantic Web Technologies

Data :
@ p r e f i x dc10 : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.0/ > .
@ p r e f i x dc11 : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.1/ > .
_: a dc10 : t i t l e "SPARQL Query Language T u t o r i a l " .
_: a dc10 : c r e a t o r " A l i c e " .
_: b dc11 : t i t l e "SPARQL P r o t o c o l T u t o r i a l " .
_: b dc11 : c r e a t o r " Bob " .
_: c dc10 : t i t l e "SPARQL" .
_: c dc11 : t i t l e "SPARQL ( updated ) " .

Query :
PREFIX dc10 : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.0/ >
PREFIX dc11 : <ht t p : / / p u r l . o r g / dc / e l e m e n t s /1.1/ >
SELECT ? a ut ho r ? t i t l e
WHERE { { ? book dc10 : t i t l e ? t i t l e .
? book dc10 : c r e a t o r ? a ut ho r . }
UNION
{ ? book dc11 : t i t l e ? t i t l e .
? book dc11 : c r e a t o r ? a ut ho r . }
}

Result :
? a ut ho r
? title
−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−
Alice
Bob

SPARQL Query Language T u t o r i a l
SPARQL Query Language T u t o r i a l
Figure 2.14.

An example of UNION graph pattern


Chapter 3
DogOnt & Dog
The work presented in this thesis is not an isolated research effort, but it is a work
well integrated into a more general theme of research that is taking place in the e-Lite
research group of the Turin’s Polytechnic. The work, both user intelligible goals and
semantic data exchange, builds upon two important contribution made by former
members of the e-Lite research group. The first is the DogOnt [35] ontology which
models the structure of an environment (In particular, a home). The second is an
ontology driven home automation system, called Domotic OSGi Gateway (Dog) [36].
Therefore, before discoursing on the role of semantic web technologies in smart
environments, this chapter briefly defines the technologies used to emulate a smart
environment.

3.1

DogOnt

DogOnt ontology provides the semantic core to model the domotic system of an environment (house). It focuses on representing devices, appliances, states and functionalities. Modularity is exploited for integrating the core set of modeling primitives
with additional features for energy profiling, user modeling, privacy management,
etc. DogOnt is organized along eight main hierarchies of concepts (see Figure 3.1)
respectively rooted at:
1. “Building Environment”: models structural elements of the environment. For
instance building, flat, garage, garden, rooms (bathroom, bedroom, diningroom, kitchen, living-room, etc);
2. “Building Things”: models physical objects (devices) present in the environment. The physical objects may be electrically controllable or uncontrollable.
The electrically controlled devices (like coffee maker, boiler, cooker, fan, lamp,
actuator, sensors and various others) are categorized under the Controllable

3 – DogOnt & Dog

category. Physical objects (like table, sofa, wall, ceiling and others), which
can not be electrically controlled are categorized under the Uncontrollable
category.
3. “Functionality”: models different functionalities provided by the controllable
devices. DogOnt further classifies them as Control Functionality, Notification
Functionality or Query Functionality. Control functionalities are the actions
that devices can perform (like a Lamp has “on” and “off” functionalities).
Most controllable devices have the ability to send a notification back, as an
acknowledgment of the completion of the assigned task. These notification capabilities are modeled under the Notification functionalities classification. For
performing the task intelligently, usually, it is required to have a mechanism
through which the status of devices can be queried at any time, which are
modeled under the Query functionalities classification;
4. “Commands”: Controllable devices perform their Control functionalities by
receiving some particular commands, whose modeling and classification is performed under this category;
5. “Notification”: Controllable devices send different types of notifications, such
as notifying when their state changes, which are modeled and classified under
this category;
6. “State” and “State Values”: At any instant, a controllable device possesses
an internal state, which is modeled as a set of orthogonal state spaces (called
“States”), with different “State Values” each. A complete description of the
state of a device is therefore a valid State Value for each of the States defined
for that device. State Values can be discrete (e.g., in Lamp “onState” and
“offState”) or continuous within a specific range of values (e.g, a DimmerLamp
device has a “Light-Intensity-State” whose value ranges from 0% to 100%).
7. “Domotic Network Component”: Controllable devices adopt widely different
network protocols. This modeling dimension describes the protocol characteristic and network addressing scheme.

3.1.1

Device Modeling in DogOnt

According to the DogOnt classification dimensions, each device is modeled by creating instances for all relevant DogOnt classes, and according to the ontology constraints. The device modeling process is briefly explained by illustrating the model
of a “Dimmer Lamp” device (Figure 3.2), which is a subclass of “Lamp” and “Controllable”, and has all inherited features of these super classes.

## 3.2 – Domotic OSGi Gateway

Figure 3.1.

DogOnt top-level concepts.

A dimmer lamp has all the functionalities which a “Lamp” can hold, such as,
it can be (switched) “on” and “off”, and can be placed at a certain location in the
IE. Furthermore, “Dimmer Lamp” has an extra “Light-Regulation-Functionality”
by which the “Light-Intensity” of the lamp can be managed. The value of “LightIntensity” ranges from 0 to 100. With the “Light-Regulation-Functionality” it may
be increased or decreased with a step 10 through “stepUp” or “stepDown” commands
respectively, or it may also be directly set to a specific value with “set(value)” command. As “Dimmer Lamp” is a type of Controllable device, two more functionalities
are inherited from the class of “Controllable”, these are “Query-Functionality” and
“State-Change-Notification-Functionality”.

3.2

Domotic OSGi Gateway

Domotic OSGi Gateway (Dog) is an ontology-powered home automation gateway.
It is empowered by the DogOnt ontology and therefore, it is able to expose different

3 – DogOnt & Dog

Figure 3.2.

Dimmer Lamp in DogOnt

domotic networks as a single and technology neutral home automation system. Dog
is versatile as it is built on top of the OSGi framework1 and the adoption of semantic
modeling techniques allows Dog to support intelligent operations inside the home
environment. It has a modular architecture (Figure 3.3) and it is divided in five
main categories: API, Device Management, Device Control, StartUp and Library.

3.2.1

Api

This category includes bundles offering technology independent programming interfaces for both external applications and OSGi-based plugins.

http://www.osgi.org


## 3.2 – Domotic OSGi Gateway

Figure 3.3.

Dog core bundles

DogRESTEndPoint: provides a REST endpoint for services offered by Dog. It is
based on JSON and XML bases messaging system, thus enabling DOG access
for non-OSGi or non-Java applications.
DogXmlEndPoint: provides an XML-RPC endpoint for services offered by the DogApi bundle, thus enabling DOG access for non-OSGi or non-Java applications. it helps retrieve the house configuration, send commands to devices
managed by DOG and receive house events.

3.2.2

Device Control

This category includes bundles dedicated to device control and monitoring. They
encompass:
DogStateMonitor: provides information about the current states of the devices connected to the Dog platform. It keeps the snapshot of the states of all the
devices. The device state notification is compliant with the OSGi Monitor
Admin Service Specification [37].
DogExecutor: allows the other Dog bundles to execute commands on devices. Executing commands means calling methods of the DogDeviceModel classes.
Thanks to DogSemanticHouseModel, DogExecutor can verify both the syntax
and semantics of received commands. In the first case command compliance
with the corresponding ontology definition is analyzed (e.g., a simple lamp can
only accept an on command with no parameters), whereas in the latter the
received commands are checked against the set of allowed commands deduced
from the DogOnt device functionalities (e.g., a door cannot be switched on).

3 – DogOnt & Dog

DogScheduler: offers a centralized service for scheduling both command execution
and device monitoring jobs. DogScheduler exploits the DogExecutor and
DogStateMonitor services.

3.2.3

Device Management

The Device Management category groups all the bundles needed to comply with the
Device Access Specification Version 1.1 defined in the OSGi Service Compendium
[37]. This specification defines the logic and the entities (i.e., bundles) that must be
designed and implemented by Dog to support automatic detection and attachment
of existing devices and to assist the dynamic plugging of new devices. It comprises:
DogDeviceManager: detects registration of Device services and associates these devices with an appropriate Driver service.
DogNotificationManager: dispatches notification and state change notifications. It
is based on the publisher subscriber model and it filters inner state change
notifications from outer ones (visible to applications).
DogDeviceFactory: creates device instances according to the runtime home configuration (defined using DogOnt). It is usually provided by DogSemanticHouseModel.
DogOntLibrary: is programmatically generated from DogOnt. It consists of all device interfaces, functionalities classes, state classes etc.
DogDeviceModel: is the Dog object representing DogOnt-defined device classes. It is
a software proxy of a physical device that can be attached by a Driver service.
DogSemanticHouseModel: can be seen as the Dog nervous system. It exploits standard DogOnt classes and DogOnt instances referred to a specific IDE environment to provide knowledge-rich access to the environment properties and
capabilities. Inference and reasoning tasks are carried at this level, both at the
gateway start-up, for computing consistency checking and transitive closure,
and at runtime. In particular, runtime reasoning is adopted for generating
inter-operation rules and pre-defined scenarios, and for dealing with unknown
devices through classification reasoning thus detecting compatible device types
on the basis of formalized capabilities (dogont:Functionality). A SPARQL
endpoint allows Dog to be extended by additional knowledge-based policies
offering un-filtered query access to the whole DogOnt IDE model. This allows, for example, to support advanced policies based on additional context
information, e.g., energy saving policies.

## 3.2 – Domotic OSGi Gateway

Dog exploits semantics mainly through the DogSemanticHouseModel bundle,
which manages all DogOnt related tasks, for supporting the device/driver attachment paradigm. In case of micro-Dog installations where the computational power
of the hardware running the gateway is too low for supporting on-line ontology
management and inference, the DogSemanticHouseModel bundle is replaced by a
SimpleHouseModel bundle that encodes static ontology information (queried from
the ontology at configuration time); in this case all inference tasks are carried off-line,
thus trading-off computational power with support for on-line inference.

3.2.4

StartUp

This category comprises of:
DogConfigurator: manages bundle-specific configurations. For instance, specific
property files, XML files and/or Additional files (ontology, images, etc.). It
provides startup configuration to all bundles of Dog.
DogLogger: provides logging facilities to all Core bundles.

3.2.5

Library

The category consists of bundles that act as simple repositories of classes and interfaces needed by the other Dog bundles. Dog2Library defines all the message
types for inter-bundle communication. It also provides utility classes to other bundles. DogJaxBLibrary provides XML serialization / de-serialization for all message
types. DogSemanticLibrary encapsulates and makes available all semantics-related
libraries like Jena, Pellet, SPARQL query facilitator etc. MeasureLibrary exports
the JScience library2 to all Dog bundles.


http://jscience.org


Part II
User Intelligible Goals

Chapter 4
State of the art
In this part of the dissertation, a unified approach based on user goal modeling is
presented (Figure 4.1). The approach addressing the concerns of both AmI designers
and end-users. User goal modeling is a higher level design for user interaction and
control, which has received little attention till now, as acknowledged in [15].

Figure 4.1.

User Goal Modeling

In 2006, DavidOff et al. [38] narrated that personal spaces, such as home play
an important role in group and individual self-definition: rather than just using
personal spaces for a specific function, users pour their personalities and lives in the
way they use and transform their personal environments. The outcome was the focus

4 – State of the art

on developing user programmable spaces. Such spaces either focused on allowing
users to control and manage their environments or learning users’ preferences, as
the environments become populated with computational elements.
Garcia-Herranz et al. [39, 40] proposes an application-independent indirect control programming system to program complex behaviors with the simplicity required
to allow novice users to program their smart environments. The motive is to allow
users to create powerful and personal behavior without expert assistance.
In [41] an Artefact framework is proposed which allows end users to deploy ubicomp systems easily in a Do-it-yourself fashion. Secondly, it allows developers to
write applications and to build augmented artefacts in a generic manner. The Artefact framework provides a layered architecture where basic artefact functionalities
are combined in a core component. Additional augmented features can be added
as plugins into the core. Each augmented feature is called a profile. Each profile
defines a specific functionality and implements the underlying logic of the functions,
e.g., room temperature, lamp brightness.
Katasonov [42] motivates to build Digital fluency in smart environments by enabling the non programmers to design, create and modify their smart environments.
The paper proposes a higher level of abstraction in application design, on-the-fly development, flexibility with respect to adding new devices and software components.
Rashidi et al. [43] proposes a software architecture which incorporates learning
techniques to discover patterns in user’s daily activities. While the patterns of user’s
activities are observed and stored, the user can also define their own activity patterns
as well. The activity pattern are observed as changes in states of devices occur in
the house. Similarly, Salomons et al. [44] introduces a generic model for intelligent
homes that describes the current state, the target state and the transition. The
model is based on storing preferences on individual devices.
Cheng et al. [45] proposes a smart home reasoning system called ASBR system.
The system learns user’s preferences by adaptive history scenarios and put forwards
a way to rebuild reasoned knowledge in other smart homes. They propose that
contextual information can be extracted and reasoned as a set of scenarios. In
addition, the system can derive personalize habits and store them in OWL files.
Similarly, Dey et al. [46] proposes a software infrastructure solution to detect the
current states of the environment (called Context) and take action based on it. The
infrastructure is focused on developing context aware applications.
All the aforementioned approaches focused on user programmable spaces, but
suffered from a “device-centric” vision. The “device-centric” vision limited the ability of the users to program their environments in terms of specific devices and their
functionalities. In 2003, the Ambient Intelligence (AmI) community had identified key research directions for building intelligence in different environments, i.e.,
homes, offices, schools and control centers [47]. These directions include the need

to develop and innovate new concepts and abstract models to address heterogeneity, intelligence, innovative interaction management techniques and human centric
expressions of personal style. Though the role of users in personal environments
is important, the role of AmI designers in order to build intelligence can not be
ignored. In 2008, Doorn et al. [48] carried a series of workshops and interviews,
and concluded that designers work top-down and like to start from abstract vague
descriptions; therefore, approaches having device-centric vision limit the ability of
AmI designers to design, implement and test general algorithms and solutions that
might apply to a range of different environments, especially in large and complex
buildings.
In [49,50] a goal based interaction has been proposed, and extended in [51], that
takes a user’s goal and finds a path achieving the goal.
Hemrik Dibowski et al. [52] proposes an automatic design approach for large
building automation systems (BAS). The top-down approach initiates by defining
the structure of the building, then the system integrators define requirements using
ontologies.
A neuro-cognitive model for Environment Recognition, Decision-making, and
Action execution inside automated buildings is proposed in [53–55]. They introduce
separate models for perception known as Artificial Recognition System-PerCeption
(ARS-PC) and decision making, identified as Artificial Recognition System-PsychoAnalysis
(ARS-PA).
D-HTN [56] is a planning system for AmI applications, based on the hierarchical
task network (HTN) approach, that is able to find courses of actions to address
given goals.
Though [49, 50, 52–56] provide abstract design approaches for smart environments, the ability to allow users to program their environments is lacking.
In the literature the concerns of AmI designers and end-users are mostly addressed separately. Therefore, their exists a need for developing a unified approach
that can address the issues of both AmI designers and end-users. On one hand, the
approach should allow a user to program his/her own personal environment and on
the other hand, the approach should allow AmI designers to work on an abstract
level without focusing on a specific environment.


Chapter 5
Domotic Effects Framework
The last decade saw the emergence of economically viable and efficient sensor technology which can be integrated with appliances, enabling them to sense different
parameters of their respective environments, i.e., temperature, luminosity, pressure
etc. It helped realizing the vision of of smart environments [12] by developing heterogeneous dynamic ensembles: groups of co-located devices of different types which
evolve over time [14]. Such environments promise to offer additional intelligent capabilities that go beyond the integrated and remote control of appliances present in
the environment. But the presence of diverse devices and the associated complexity
has given rise to a major problem in the past years, i.e., the problem of providing
users with the ability to control and manage their respective environments.
State of the art revolves around the issues related to communication protocols
and technologies [41, 43, 46]. Many approaches are furthermore based on abstract
modeling of smart devices, resorting to some knowledge representation tool (e.g., ontologies [35,49,50]), but the research trend is moving from a traditional device-centric
vision (bottom-up) to a vision of providing higher level design for user interaction
and control [45,47,56,57], i.e., user goal modeling. However, this research trend has
received little attention as acknowledged in [15].
“Domotic Effects” (DE) framework provides a 3-tiered ontology driven modeling technique that models user intentions or goals (Figure 5.1). It addresses the
concerns from perspectives of the AmI designer and the residents. It provides AmI
designers with an abstraction layer that enables the definition of generic goals inside
the environment, in a declarative way, and that can be used to design and develop
intelligent applications. It provides a general framework for expressing functional
properties, in a domain-dependent way: for each application domain, the AmI designer may choose the most suitable representation, and define suitable functional
operators. Using these operators, various user goals are then defined in a specific
environment. The high-level nature of the Domotic Effects, on the other hand, also
allows the residents to program their personal, office or work spaces as they see fit:

5 – Domotic Effects Framework

they can define different achievement criteria for a particular generic goal, by using
the domain-specific operators defined in the previous phase.

Instance layer

Ventilation

TVScenario

AmI layer
Boolean
HVAC

Real

...

Lighting

Core layer

Framework

SecureHome

AmI Designer

House 2

User

House 1

Core Concepts

Figure 5.1.

The DomoticEffects framework - Logic Architecture.

Every device in the environment is capable of providing certain visible (perceivable) effects for a user. These effects are fulfilled by possible states of the device.
For example, an effect of illumination can be provided by a lamp in “ON” state.
However, modern devices are complicated in nature and a single device can have a
composite state, which may be modeled as concurrent sub-states. These sub-states
are orthogonal regions combining multiple descriptions of a device. For example, a
TV set may have an on-off state (with possible values On or Off), a volume state
(with possible values 0 through 100), a channel state (with possible values depending
on the set of programmed channels). A device state is therefore composite in nature
and therefore it is modeled as the parallel composition of different sub-states.
There might be cases in which an effect can only be fulfilled by a combination of
devices having particular states. For example, the effect of securing a building may
require all the exit doors and windows to be closed. In the context of DE framework,
an effect that depends upon a single device (having a state or sub-states) is called
a simple effect (SE) and an effect dependent on a combination of devices (having
particular states and sub-states) is called a complex effect (CE). A CE is described

## 5.1 – Requirements

by combining SEs and other CEs.
For discussion in this thesis, the applicability of the DE framework to Boolean application domains is considered, i.e., domains in which user goals (effects) can either
be true (active) or false (inactive) depending on the value(s) of the involved states
and sub-states, that may be Boolean, discretely enumerate or real-valued. This covers most control applications and many monitoring use cases in smart homes, offices
and industrial plants.
The chapter is divided into two sections. Section 5.1 defines requirements for
modeling human-intelligible effects (goals) and Section 5.2 introduces Domotic Effects and their formalization.

5.1

Requirements

Domotic Effects (DE) provide abstraction for modeling current (state) and future
(goals) configurations of a smart environment. These configurations shall be expressed in a human-intelligible way and must support machine-based evaluation,
solution and activation, with almost no human intervention. Formally, effects can
either be simple or complex. Simple effects (SEs) are the terminal nodes of this
functional representation and they correspond to functions applied to the state (or
value) of a single device (sensor). Complex effects (CEs), on the other hand, derive from the application of domain-specific operators to SEs and other CEs. This
permits the definition of modular and stratified effects built on top of simpler ones
(Figure 5.2 and Figure 5.3).

Figure 5.2.

SE and CE effects in the energy domain

Simple and complex effects must fulfill well defined requirements to effectively

5 – Domotic Effects Framework

Figure 5.3.

SE and CE effects in the control domain

address the representation issues discussed in Chapter 6. Such requirements encompass:
• Formal definition. Effects must have a formal, machine understandable
specification thus enabling automatic elaboration and mapping into set of
device states/activations; the same applies to operators, which are required
to be machine processable.
• Domain dependency. Effects must be composable in different ways depending on the knowledge and/or application domain in which they are defined.
As an example, real-valued effects (e.g., energy or power effects) will undergo
operations such as aggregation of values (sum, average, last in a time window), derivation/integration (to convert energy to power and back), etc, as
in Figure 5.2. Instead, boolean-valued effects (e.g., active/not-active) might
be aggregated by straightforward boolean operators (and, or, not, etc.), as in
Figure 5.3.
• Modularity. Whilst a restricted core set of modeling primitives is required
to set up a sound representation framework, modeling shall be adaptable to
different needs, i.e., knowledge domains, and to different actors such as AmI
designers and home inhabitants.
• Evaluation support. Evaluating effects means computing their amount
starting from the values of each device state and sensor value, according to
the definition of the effects (SEs) and the semantics of the operators (that
might change depending on the domain). The effect values must be updated
whenever a device/sensor changes its state/value, therefore evaluation shall be

## 5.2 – Formalism

quick, i.e., comparable with the latency of home automation systems (roughly
under one second), and well integrated with the smart environment management system (e.g., an home gateway). Different evaluation algorithms and
computational models may be applied depending on the involved physical values and on the modeled operators.
• Enforcement support. Human-defined effects should be translated automatically into sequences of device activations (commands). This requires
the inverse computability of the effect definition, which typically results in
many, alternative solutions. Exploration of the solutions space may also enable
optimization of second-level metrics, such as reducing the number of device
switches or the energy consumption.
• Advanced intelligence support. A new breed of intelligent applications
will generate and/or exploit domotic effects. For example, advanced in-home
interfaces might exploit effects to offer “intelligent widgets” bound to effects
instead of devices. Semantic reasoning might exploit effects to infer common
automation recipes applicable to different smart environments. Hybrid and
probabilistic reasoning might empower (semi-)automatic selection of alternative home configurations, e.g., raising shutters instead of switching on lamps,
or vice-versa, depending on the values of defined effects. Context information
might be defined on top of effects instead of devices, supporting higher level
policies and behaviors.
• Human-intelligibility. While effects shall be uniquely identifiable (e.g., by
using URIs), final users shall be able to give meaningful personalized names,
to easily identify and understand the represented configurations. Moreover
their formal definition shall be informative, i.e., the mechanisms with which
SEs are composed into CEs must be easy to understand, even for unskilled
users.
• End user accessibility. Effects shall be easy to define and to understand
by end users, e.g., home inhabitants, through intuitive GUIs [58]. This allows
bridging the gap between device-centric and interaction-centric modeling providing means for users to explicitly inform AmI about the sequences of effects
(or goals) that activities require.

5.2

Formalism

Given an intelligent environment, we define as D the set of installed controllable
devices d ∈ D. Each device is characterized by a device category that, among the

5 – Domotic Effects Framework

other things, defines the allowed sub-states for a device. Depending on the device
category, for each device d we define the set of allowed sub-states S(d); this set
may be discrete (e.g., {On, Off} for a lamp) or continuous (e.g., [0, 100] for a
volume knob). During system evolution, the actual state of each device is a timedependent function s(d, t) ∈ S(d). The whole environment therefore possesses a
global state space G, represented by the Cartesian product of all device state spaces:
Q
G = d∈D S(d), thus defining a global environment state g ∈ G.
Formally, a Domotic Effect DE is defined as a function of the global state space:
DE : G → V, where V is an application-dependent value space. For example, for
control applications, V = {0, 1} since each Domotic Effect represents the activation
of a given state configuration; conversely, when dealing with energy savings, V = <+
since Domotic Effects may be used to represent consumed power.
AmI designers and end users may define custom Domotic Effects by working
with a domain-specific set of operators. Such operators work on the value space
V relevant to the specific application domain1 . The specification of a DE function
requires three levels of formalization:
1. defining Simple Effects (SE), to extract a V-valued quantity from a single
device state. Formally, SE is a function that considers the state on only one
device, SE : S(d) → V; such function is also time-dependent since it depends
on s(d, t).
2. defining effect operators working within V-space algebraic semantics, suitable
for composing new functions in the application domain. Formally, an operator
op is a function op : V N → V, where N represents the number of operands of
the specific op.
3. defining Complex Effects (CE), by applying effect operators to the values
computed by other SE or CE. Formally, a CE is represented by a couple
(op, (DE 1 . . . DE N )) composed of an operator name op and a list of Domotic
Effects DE i whose values are used as operands.
For each application domain, there would be a set of pre-defined SE and a set
of operators that the users may combine to compute the values of interest. For
example, if we consider control applications (V = {0, 1}), then the SE functions
that may be adopted are:
• for discrete-valued states, a SE detects whether a device currently is in any
given state. E.g., SE On (d, t) = (s(d, t) == On).

for cross-domain applications, V would be the union of all relevant value spaces


## 5.2 – Formalism

• for real-valued sensors, a SE usually compares the current sensor data with a
threshold. E.g., SE Hot (d, t) = (s(d, t) > 30o C).
Conversely, if we consider energy savings applications (V = <+ ), the SE usually
just extracts the current energy or power measurements from the real-valued sensor:
SE Power (d, t) = s(d, t).
The instance layer in the “DogEffects” ontology defines a set I of all defined
domotic effects (instances), i.e., I = {DE 1 , DE 2 . . . DE N }.


Chapter 6
Modeling
Modeling formalisms and techniques play a crucial role in smart environments research. Human activities are modeled to better interpret human-home interaction
detected by pervasive sensors. Human behaviors are analyzed and related to activities and to temporal evolutions with the aim of learning recurrent patterns, and
possibly inferring user wills or goals. The context in which interactions occur, i.e.,
the environment state, the time, the weather, the season or the users’ mood, are
modeled to account for all possible factors influencing human behaviors. Together
with home inhabitants, environment structure and components are modeled to support better design/operation of environments, e.g. detecting problems or design
choices that might hamper usability or accessibility to impaired people. Moreover,
device modeling is exploited to overcome integration issues and to offer a shared
knowledge on how the environment works and on how it can be controlled.
All these modeling aspects can be roughly divided in two main categories: modeling of environment interactions, e.g., activity, behavior and context modeling
[59–61], and modeling of environment set-up, including home fixtures and devices
[35, 62]. Modeling of environment interactions treats people living in the environment as hidden targets: users are modeled with the aim of learning typical behaviors
and understanding the underlying semantics, i.e., the carried activities. Environment set-up, instead, completely ignores the human presence and adopts a devicecentric modeling approach addressing integration issues rising from the proliferation
of automation devices and communication protocols, which are often incompatible
with each other. These two last categories increasingly exploit semantics, i.e., ontologies and reasoning facilities stemming from the Semantic Web community (see
Section 6.2 for more details).
Despite this intense modeling activity, a relevant aspect is still quite neglected,
although needed to correlate human activities and device-centric descriptions: human intelligible state and goal modeling. Intelligible states and goals may relate
to environmental variables (illumination, temperature, . . . ) or to more abstract

6 – Modeling

conditions such as security and energy saving. Domotic Effects represent such a
human-understandable vision, i.e., how the home inhabitants perceive/represent the
current environment configuration (state) and how they plan the next environment
state (goals).
In this paper we introduce explicit and semantic modeling of such Domotic Effects, by empowering the AmI designer, and the end user, to define and specify
its own vision of the ambient state, at a human-intelligible level of abstraction.
Domotic Effects are defined as named sets of states for environment devices, constructed through domain-dependent functional operators (e.g., boolean operators
in the direct control domain). They are formally defined through a three tiered
modeling approach based on the newly designed DogEffects ontology. For each application domain, the AmI designer (or the end user, in second instance) defines
the most suitable algebraic representation of domotic effects and the corresponding
functional operators.
The proposed formal model is complemented by a DomoticEffects software framework that links it with the current state of a real smart environment, bidirectionally
(Domotic Effects to device states, and device states to Domotic Effects).
Advantages are clear: AmI designers can work on top of an abstraction layer
enabling the definition of generic, device-independent goals in a declarative way.
Intelligent applications and operations inside the house can therefore be explicitly
related to abstract effects, and their actual implementation may vary depending
on the underlying infrastructure. Interaction designers can rely on such a shared
knowledge, enabling a more natural human-home interaction. For example, user
interfaces might concentrate on high-level abstract interactions, instead of single
activations, and the DE framework would take care of mapping such goals into
desired device states and environment configurations.
The main focus of this chapter is the definition of the formal modeling framework
and the adopted DogEffects ontology.
The reminder of this chapter is organized as follows: The underlying ontology
for the DE framework is discussed in Section 6.1, while Section 6.2 compares the
proposed approach with the current state-of-the-art.

6.1

Modeling: DogEffects Ontology

In order to provide the formal knowledge base for the DE framework, a 3-tiered
ontology-based approach has been adopted (Figure 5.1). The ontology is called
the DogEffects ontology1 and it is formalized by using the OWL Web Ontology

The ontology can be reached at: http://elite.polito.it/ontologies/effects.owl


## 6.1 – Modeling: DogEffects Ontology

Language [29]. The DogEffects ontology is based on the modularity pattern, which
allows it to be easily attached to other ambient ontologies that model the devices
installed in an environment and their properties (especially the concept of state).
Three modeling layers are defined, with decreasing usage complexity: a core layer,
designed to establish the basic semantics of effects, a middle-layer allowing AmI
designers to define SEs and domain-dependent operators for combining them into
complex effects, and finally an instance layer where specific effects can either be
defined by AmI designers or by final users, through suitable user interfaces.

6.1.1

Core layer

The core layer contains the basic class definitions for expressing Domotic Effects
(Figures 6.1, 6.2, upper side); this layer is not meant to be modified by AmI designers nor by final users. Every Domotic Effect is formally organized into a concept hierarchy inheriting from the dogEffects:Effect class. Effects can either be
simple (dogEffects:SimpleEffect) or complex (dogEffects:ComplexDeviceEffect). For both kinds of effects, domain-dependent subclasses are defined at the
middle layer.
Simple Effects (SEs) are the terminal nodes of the representation and compute
a value depending on a device state or sensor value. SEs act as interface points
between the DogEffects ontology and some device description ontology (e.g., DogOnt
[35]). The dogEffects:effectOf and dogEffects:functionOf open relations (i.e.,
relations without range restrictions) permit to identify the device and the device
state for which a given SE is computed, respectively.
Every Complex Effect (CE) represents a functional expression of SEs and other
CEs declared by using domain-dependent operators defined at the middle-layer of the
DE framework. Effect operators take either simple or complex effects as operands
(through the dogEffects:hasOperand relation) and generate new CEs as result,
identified by means of dogEffects:hasResult relation.
Two main disjoint families of operators are modeled: unary operators (dogEffects:UnaryOperator) and non-unary operators (dogEffects:NonUnaryOperator).Unary operators only involve one dogEffects:Operand (cardinality restriction on the dogEffects:hasOperand relation), which can either map to a SE or
a CE (by the dogEffects:operandEffect relation). Typical examples of unary
operators are the NOT operator (in the boolean control domain) or the Integration operator (in the energy domain). Non-unary operators are further specialized (disjoint union) into commutative (dogEffects:CommutativeOperator) and
not-commutative (dogEffects:NotCommutativeOperator) operators. According to
the mathematical definition of commutative (not-commutative) operators, the result produced by the former (dogEffects:CommutativeOperator) is independent
on the order in which operands are evaluated while, the latter operator provides

6 – Modeling

a results depending on the order of the effect operands. In such a case the dogEffects:OrderedOperand subclass of operands shall be used to account for the
operand order, expressed as an ascending integer number by the dogEffects:hasPositionN property. Typical examples of non-unary effects are the AND, OR and
EX-OR logic operators, in the boolean control domain, or the SUM and the DIFFERENCE operators in the continuous energy domain. The latter, in particular, is
also not commutative as the result of a mathematical difference changes depending
on the order of the operands.

6.1.2

Middle layer

The middle layer encodes domain-dependent operators typically defined by AmI
designers. Every application domain will define different operator classes for this
layer by sub-classing the general operator classes defined in the core layer. Two
sample middle layers dealing with control (Boolean application domain) and with
energy saving are defined below.
Boolean Application Domain
In the control domain, simple effects correspond to devices (sensors) being in specific
states (measuring specific range of values). SEs and CEs can only evaluate to true
or false, and Boolean logic is sufficient to compute CEs and to implement rather
advanced activation scenarios. From the modeling point of view, mapping operators
to Boolean logic requires a minimum set of logic operators, e.g., AND (∧), OR
(∨) and NOT (¬) (Figure 6.1); however, AmI designers may choose to define more
complex and user-intelligible Boolean operators such as:
1. ImpliedOperator: This operator represents the “logical implication” relationship. As it requires only a single operand, it is modeled as a unary operator.
2. AlternateOperator: This operator represents a function whose value is active
when exactly one of its operands is active. It is commutative and non-unary.
Mathematically,
 the Alternate effect operator can be defined as: Alt(x1 . . . xn ) =
Q
P 
j/
=i xj .
i xi ·
3. ExactlyMOperator: This non-unary operator represents a function whose value
is active when exactly M number of its operands are active. Suppose there
are n operands, i.e., OP = {1,2, . . . n}. Then the ExactlyMOperator effect
operator can be defined as:
ExactlyM (x1 . . . xn ) =


O⊆OP,|P |=M





Y

i∈O

xi ·

Y

j/
∈O



xj 

## 6.1 – Modeling: DogEffects Ontology

Figure 6.1.

The DogEffects middle layer - Boolean Control Domain


6 – Modeling

Energy saving
In the energy saving domain typical elaborations involve continuous data such as
power or energy measures coming from meters located in the smart environment.
While simple effects are still defined as sensor-value couples, complex effects require operators such as integration for translating power measures into energy measures (and derivation for doing the inverse), thresholding for detecting overloads or
anomalies, average for comparing consumption in a period, etc. With respect to the
Boolean control domain, operator modeling is much more complex in this domain,
and many different operators can be defined depending on the AmI designer’s focus
and on the application scope. Figure 6.2 shows a sample middle layer for energy
where integration/derivation, average, sum, difference and threshold are defined.
Although this sample energy operator modeling might be somewhat simplistic
to be used in full-featured energy aware applications, it’s important to notice how
the framework easily supports domain-dependent operators. Moreover, modeling
accuracy and granularity can easily be adapted to the problem under examination,
thus providing AmI designers a powerful tool for defining abstract effects on which
more advanced policies can be built.

6.1.3

Instance layer

The instance layer of the Domotic Effects framework represents specific Domotic
Effects defined in a given smart environment. They are modeled as instances of the
classes defined in the core or middle layer and they relate to each other (functional
composition) by means of domain dependent operators defined at the middle layer.
Effect instances are typically defined by AmI designers or by final users. Following
paragraphs better detail this layer by providing sample effect instances for both the
Boolean control and the energy saving domain.
Boolean control
Since the current focus is geared towards the applicability of the DE framework to
Boolean application domains, this section illustrates two use cases which are used
through out this thesis.
Figure 6.3 illustrates a sample “Illumination” use case corresponding to the
generic goal of lightening up the room. The illumination can be artificial by switching on the mirror lamps or ceiling lamp in different combinations, or illumination
can be natural by opening the shutter of the window.
Figure 6.4 illustrates a simplified “ Dining@Lunch” use case corresponding to the
overall state of a dining room, in a house, during lunch hours. The “Dining@Lunch”
use case includes isolating the kitchen, illuminating the dining room and switching

## 6.1 – Modeling: DogEffects Ontology

Figure 6.2.

The DogEffects middle layer - Energy Saving Domain


6 – Modeling

value

dogont:
Controllable

hasOperand

opName

isA

Effect
Operator

effectOf (=1)

Core Layer

Operand

operandEffect (=1)
Effect

Ordered
Operand

hasOperand
(=1)

isA
Simple
Effect
isA

hasPositionN

hasOperand (>=2)

hasResult (=1)
functionOf (>=1)

Unary
Operator

isA
hasOperand (only)

isA

dogont:
StateValue

isA

NonUnary
Operator

Complex
Effect
NotCommutative
Operator

Commutative
Operator
isA

Complement
Operator
Boolean
Simple Effect

isA

Not

isA

Or
Operator

opName

AmI layer
(Boolean Domain)

isA

Alternate
Operator

And
Operator
opName

opName

opName

And
Alternate

Or

Instance Layer

hasResult
Illumination

MirrorLamp
Illumination

Or1
hasOperand

Artificial Illumination

hasResult

operandEffect
Op1

And1

operandEffect

hasOperand

hasOperand

hasOperand

Op5

Al1

hasOperand

Natural Illumination

effectOf

Ceiling Lamp
Illumination

functionOf

effectOf

Figure 6.3.

hasOperand

Op4

Op2

operandEffect

hasResult

Op3

Left Mirror Lamp
Illumination

operandEffect
functionOf

Op6

operandEffect

effectOf

functionOf

operandEffect

Right Mirror Lamp
Illumination

effectOf

functionOf

“Illumination” use case (DogEffects Ontology)

on the television for entertainment. The functional representation of the use case is
outlined in Table 6.1.
Table 6.1.

Dining@Lunch functional form

Dining@Lunch = And(IsolateKitchen, T vEntertainment, LampIllumination)
IsolateKitchen = And(Door_Kitchen_Isolate, F an_Of f, Kitchen_F low)
LampIllumination = And(Lef tW allLampIllumination, RightW allLampIllumination)
RightW allLampIllumination = SE(Lamp5, OnState_lamp5)
Lef tW allLampIllumination = SE(Lamp4, OnState_lamp4)
Door_Kitchen_Isolate = SE(Door_Kitchen, Of f State_Doorkitchen)
F an_Of f = SE(F AN_Kitchen, Of f State_F ankitchen)
Kitchen_F low = SE(ShutterActuator_Kitchen, UpState_SAKitchen)
T vEntertainment = SE(T v1, OnState_T v1, V olume_40)


## 6.2 – Related Works

value

hasOperand

opName

isA

Effect
Operator

effectOf (=1)

dogont:
Controllable

Core Layer

Operand

operandEffect (=1)
Effect

Ordered
Operand

hasOperand
(=1)

isA
Simple
Effect
isA

hasPositionN

hasOperand (>=2)

hasResult (=1)
functionOf (>=1)

Unary
Operator

isA
hasOperand (only)

isA

dogont:
StateValue

isA

NonUnary
Operator

Complex
Effect
NotCommutative
Operator

Commutative
Operator
isA

Complement
Operator
Boolean
Simple Effect

isA
And
Operator

opName

isA

Not

AmI layer
(Boolean Domain)

isA

Alternate
Operator

Or
Operator

opName

opName

opName

Or
Alternate

And

Instance Layer

hasResult

Dinning@Lunch

And1

Lamp
Illumination

Isolate Kitchen

hasResult
Or1

operandEffect
hasOperand
hasOperand

operandEffect

Op1
Op2

hasResult

hasOperand

hasOperand

Op4

And2
operandEffect

Op3

Op6

hasOperand

Kitchen_Flow

FAN_OFF

effectOf functionOf

effectOf functionOf

Figure 6.4.