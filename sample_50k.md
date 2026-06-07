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