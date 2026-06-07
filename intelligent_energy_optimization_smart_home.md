# Intelligent Energy Optimization for User Intelligible Goals in Smart Home Environments

**Authors:** Fulvio Corno, *Member, IEEE*, and Faisal Razzak, *Student Member, IEEE*

**Published in:** IEEE Transactions on Smart Grid, Vol. 3, No. 4, December 2012, pp. 2128–2135

**DOI:** 10.1109/TSG.2012.2214407

**Manuscript received:** November 14, 2011; revised June 06, 2012 and August 07, 2012; accepted August 15, 2012.

*The authors are with Politecnico di Torino, Dipartimento di Automatica e Informatica, 10129 Torino, Italy (e-mail: fulvio.corno@polito.it; faisal.razzak@polito.it).*

---

## Abstract

Intelligent management of energy consumption is one of the key issues for future energy distribution systems, smart buildings, and consumer appliances. The problem can be tackled both from the point of view of the utility provider, with the intelligence embedded in the smart grid, or from the point of view of the consumer, thanks to suitable local energy management systems (EMS). Conserving energy, however, should respect the user requirements regarding the desired state of the environment, therefore an EMS should constantly and intelligently find the balance between user requirements and energy saving. The paper proposes a solution to this problem, based on explicit high-level modeling of user intentions and automatic control of device states through the solution and optimization of a constrained Boolean satisfiability problem. The proposed approach has been integrated into a smart environment framework, and promising preliminary results are reported.

**Index Terms:** Building automation, domotic effects, electrical power optimization, energy management systems, energy optimization heuristic, home automation.

---

## I. Introduction

In the last decade, intelligence emerged as the basic component to design modern home and building automation systems. The term "intelligence" implies a provision of automated control over the buildings to solve interoperability issues among devices from different vendors, to sense the environment, to provide context-aware services to the residents and to manage safety and security issues. Regardless of how ambitious and diverse the notions might seem, the research community has demonstrated the ability to achieve such goals using pilot projects [1]–[4]. In the past few years, energy efficiency has become a key requirement for designing modern buildings and industries. The approaches in this regard not only rely on improving building structures and adopting more efficient appliances but also aim at increasing user awareness towards their energy usage.

Energy efficiency has become one of the major concerns in today's life, impacting almost all human activities, from industrial and commercial, to leisure and vacation. According to the statistics from the U.S. Department of Energy and the European Union Energy Commission, global energy consumption is likely to increase in the next decade, with residential and commercial buildings raising their aggregate figure to 20%–40% of the total yearly consumption. If only electricity is considered, the consumption share allocated to buildings is suppose to increase up to 73%, evenly distributed between residential and commercial buildings [5].

To cope with increasing energy needs the smart grid is a promising infrastructure [6] which focuses on demand side management. It provides customers an ability to make informed decisions about their energy consumption by adjusting timing and quantity of their electrical usage [7], [8]. This flexibility is enabled by pricing policies for electrical usage over time [9], [10] and/or by dynamic demand scheduling algorithms to optimize energy services in buildings [11], [12]. The smart grid infrastructure requires a two-way communication through which appliances can be monitored and controlled by a control center installed on the premises of the energy provider which may lead to privacy and security issues [13].

A complementary approach to energy management is the local optimization of energy consumption using a locally installed Energy Management System (EMS) on the building premises. Most EMS focus on making the consumer more aware of their electrical power usage and/or providing methods to share this information with energy providers or third party application developers [14]–[17]. The research focuses on different graphical illustrations of data related to consumed energy to ease consumer comprehension [18], [19] and on different tools and methodologies to share this data over the web [14]. All these approaches need active user participation in order to implement energy management strategies.

This paper proposes a more automated approach, where the EMS may automatically act on appliances and control their power consumption, while satisfying user requirements about the current environment state. The presented approach is based on two pillars: the availability of an explicit model for the smart home (such as provided by intelligent home gateways), and the expression of user needs in a more abstract way. The environment should be controlled by "user intelligible goals" that represent the state of the environment perceived by the user, on an abstract level. For example, the user may wish to illuminate a room and this may be done by acting on lamps, curtains, and shutters in different ways. Therefore, the user achieves the effect of illuminating the room on an abstract level.

The paper describes a novel approach to optimize the energy usage in a building while achieving user intelligible goals. The main contributions of the paper are: adopting an explicit formal modeling for user goals (based on the Domotic Effects modeling framework); proposing an architecture that is compatible with existing ambient intelligence solutions; describing an algorithm based on Boolean satisfiability (SAT) for computing the optimal solution and integrating the SAT algorithm with a suitable heuristic in order to tackle combinatorial explosion.

The paper is divided into seven sections. A literature overview is first provided in Section II. Section III describes the theoretical framework of the paper, i.e., the explicit high-level modeling of user intention. The problem tackled in the paper is then formalized in Section IV, while the approach adopted for optimization is described in Section V. Section VI shows detailed results of a preliminary experiment. Finally, Section VII concludes the paper and highlights future work.

---

## II. Related Works

Hubert et al. [20] outlined that in order to realize the potential of the smart grid, optimization of energy usage is required at different consumer levels, i.e., residential, commercial, industrial. In the domain of EMS, the literature on optimizing the electrical power usage while achieving user intelligible goals (in real time) is scarce but several researchers have addressed the energy optimization issue at different consumer levels.

Reference [21] advocates the need to build an intelligent decision support system which takes into account user preferences and behavior, and then tries to assist the user in reducing the energy consumption according to a dynamic notion of price. A model is proposed that learns user preferences and characteristics over time, and provides different alternatives for efficient energy usage. However, the practical implementation of such model, i.e., how to integrate it with a home automation system and its feasibility was not discussed. Moreover, the model focuses on user's preferences over devices rather than on higher level intelligible goal. A similar approach is proposed in [22]. Dynamic pricing and incentive pricing policies are adopted and advocated by many in the smart grid community to optimize the energy usage [9], [23] but the user perspective is often missing.

Amir-Hamed et al. [24] propose optimization of residential load control with price prediction in a real-time electricity pricing environment. It minimizes the householder's electricity costs by scheduling the operations of each appliance, subject to special needs of the user. The user perspective is modeled as a waiting parameter in the scheduling problem, whose cost increases with time. Therefore, each appliance operation is scheduled based on price of electricity and the value of the waiting parameter.

Reference [25] proposed a system model that uses game theory to design a energy consumption scheduling game among consumers to address demand side management. It considers a single energy source and multiple consumers. The consumers automatically coordinate among each other to find optimal energy consumption on an hourly basis. The scheduling problem is modeled over a set of consumers and could face scalability issues when the number of consumers increases. This technique also lacks the description of modeling consumer requirements.

One potential weakness of all above proposals is that they focus entirely on minimizing energy consumption and ignore other environment aspects, especially the user's perspective. The Ambient Intelligence (AmI) community has addressed such aspects in the domain of smart environments. Often missed is the point that the EMS inside a building will be part of a larger smart environment system, providing sensing, actuation and user interaction.

---

## III. User Intention Modeling

To control the environment, an EMS needs to be aware of the structure of the environment, including a list of devices, their locations, their available commands, and most importantly their power consumption in their various operating states. For environment and device modeling the DogOnt [26] ontology was adopted which is supported by the Dog [3] automation gateway. Device models include device features, functionalities, commands, and attainable states. In particular, for each device the set of possible internal working states is represented, and each state may influence power consumption. Information about power consumption of devices or device classes is encoded in a simple lightweight DogPower ontology, derived from the Energy Profile ontology proposed in [14]. The combination of DogOnt and DogPower gives all needed information about the environment.

User intentions, on the other hand, are modeled thanks to the "Domotic Effects" framework, presented in this section. It is an abstract high level modeling approach, which addresses the concerns from both AmI designer and resident points of view. Domotic Effects allow them to concentrate on high-level goals that the environment should accomplish, without worrying about the underlying device(s) fulfilling the goal.

Domotic Effects provide AmI designers with an abstraction layer that enables defining generic goals inside the environment, in a declarative way, and designing and developing intelligent applications. The high-level nature of Domotic Effects also allows the residents to program their personal, office, or work spaces as they see fit: they can define different achievement criteria for a particular generic goal, by using domain-specific operators.

### A. Conceptual Modeling

The Domotic Effects modeling framework is organized in three tiers (Fig. 1), supporting the needs of designers and users. The *core layer* contains the basic class definitions for expressing Domotic Effects. Each Domotic Effect (DE) is expressed as a function of existing device states or sensor values. Such function is expressed using a set of operators that can be extended or modified by the AmI designer. The *AmI layer* encodes the set of operators defined or customized by the AmI designer, depending on the application domain. Finally, the *Instance layer* represents the specific Domotic Effects being defined in a specific environment.

The choice of operators, and their associated numerical domains and ranges, are customized depending on the domain of application requirements. For example, in monitoring and control applications, Domotic Effects express logical values (in Boolean algebra), and the AmI designer would define Boolean operators to construct effects. On the other hand, in energy management applications, Domotic Effects would represent power and energy values, and AmI designers would define real-valued aggregation operators.

A DE can be a *Simple Effect* (SE) if it depends upon a single device being in a particular state or a sensor having some value range; otherwise it is a *Complex Effect* (CE) and depends upon combinations of other DEs (both simple and complex). A modular "DogEffects" ontology provides a formal knowledge base for describing DEs, and is organized in a structure that corresponds to the three tiers modeling framework.

Users can define several domotic effects, based on the operators defined for the environment. At any instant, each DE has a (Boolean or real) value associated with it. For example, a user may describe a Boolean Domotic Effect corresponding to the generic goal of lighting up a room, and this goal may be reached by acting, in different ways, on lamps, curtains, and window shutters in that room, possibly by taking in to account external conditions.

> *Fig. 1: Domotic effect modeling framework — three-tier structure showing Instance layer (House 1, House 2, SecureHome, TVScenario, Ventilation), AmI layer (Boolean, Real, HVAC, Lighting operators), and Core layer (Core Domotic Effect Classes), with User and AmI Designer access paths.*

### B. Domotic Effect Formalization

Given an intelligent ambient managing a set of devices **D**, each device *d* is associated with a set of allowed states *S(d)*; depending on the nature of the device, states may be discrete (e.g., {On, Off} for a lamp) or continuous (e.g., [0, 100] for a volume knob). During system evolution, the actual state of each device is a time-dependent function *s(d, t) ∈ S(d)*.

The whole environment possesses a *global state space* **G**, represented by the Cartesian product of all device state spaces: **G** = ∏_{d∈D} S(d), thus defining a global environment state *g ∈* **G**.

Formally, a Domotic Effect *DE* is defined as a function of the global state space: *DE : G → V*, where *V* is an application-dependent value space. For Boolean application domains, *V = {0, 1}*. A Simple Effect *SE* is a function that considers the state of only one device, *SE : S(d) → V*; such function is time-dependent since it depends on *s(d, t)*. An operator op is a function *op : V^N → V*, where *N* represents the number of operands of the specific op. A Complex Effect *CE* is represented by a couple *(op, (DE_1 ... DE_N))* composed of an operator name and a list of Domotic Effects *DE_i* whose values are used as operands. Such function is also time-dependent.

A set **I** contains all domotic effects defined for an environment, i.e., **I** = {DE_1, DE_2 ... DE_M}.

### C. Representing Power With Domotic Effects

Each device, in each operating state, consumes some amount of electrical power,¹ that is represented as a real-valued Simple Effect *P(s)*, *P : S(d) → ℝ⁺*.

> ¹ In this paper active instantaneous power is considered, although the modeling approach can be trivially extended to other electrical properties.

The instantaneous power consumed by the whole environment is therefore represented as a Complex Effect **P** aggregating all individual power measurements:

```
P(g) = Σ_{d∈D} P(s(d))     (1)
```

### D. Domotic Effect Enforcement

For Boolean valued domotic effects, the user can request the system to enforce particular domotic effects. "Effect Enforcement" addresses the problem of finding at least one configuration that satisfies the user request and using the automation system to bring the home devices into that satisfying state.

The *user request* **R** is defined as a subset of the declared Boolean domotic effects: **R** ⊆ **I**. In simple terms, the user request is the subset of *DE_i* that the user wants to be active (true) at a given instant.

Satisfying user requests amounts to solving the Boolean function *F_R(g)* defined as:

```
F_R(g) = ∏_{DE∈R} DE     (2)
```

To address the problem, the user request is transformed into a Boolean satisfiability problem (SAT). SAT is the problem of determining if the variables of a given Boolean expression can be assigned in such a way as to make the expression evaluate to *true*. Each domotic effect defined in the DogEffects ontology is mapped to a Boolean variable. The functionality of each effect operator defined in the AmI layer is mapped in terms of a Boolean sub-expression in the SAT problem. The Boolean expressions for all complex domotic effects present in the user request **R** are recursively constructed and conjuncted. The Boolean expressions are solved using a SAT solver, which if satisfiable gives the values (true or false) of all the variables. As simple domotic effects represent the terminal nodes of the expressions, the values corresponding to their variables give us the device configurations that will satisfy the user request.

---

## IV. Problem Statement

Given the definitions in the previous sections, the goal of the paper is to compute the minimum value of **P**(g), while satisfying the user request **R**. This corresponds to a constrained optimization of **P** subject to the Boolean constraint *F_R(g)*. In this paper, the basic SAT-based approach for effect enforcement has been extended to find a solution with minimum power consumption. Since the set of possible solutions may be extremely large, a suitable heuristic is proposed to get a satisfactory low-power solution in acceptable CPU times.

Energy management techniques should in fact respond in near real-time (NRT), by acting on a time scale comparable with user requests and device state change frequencies. Normally, the computational delay should be less than a few seconds.

---

## V. Proposed Approach

To minimize power **P**(g) subject to user-requested domotic effects *F_R(g)*, a *Domotic Effect Optimizer* module is developed (Fig. 2). The Domotic Effect Optimizer receives a user request and transforms it into a SAT problem, that is solved to find valid configuration(s). The number of configurations may be zero or more. If zero, the user request is not satisfiable. Otherwise, a configuration with minimum power consumption needs to be determined.

An exhaustive enumeration approach can be adopted, in which each valid configuration is checked for its total power consumption value **P**(g) and the one with minimum value is enforced on the environment. However, the enumerated approach becomes computationally expensive and practically infeasible if the number of configurations is too large.

To guarantee near real-time (NRT) execution, the number of configurations returned by the SAT solver is compared with an experimentally-tuned configurable threshold *T_c* that roughly corresponds to the number of configurations that may be enumerated in one second. If the number of configurations is lower than *T_c*, then exhaustive enumeration is fast enough to achieve NRT responsiveness. Otherwise, a heuristic is applied to guarantee results in NRT, even if the absolute optimum is no longer guaranteed.

The complete approach is highlighted in Fig. 2. At startup, the Domotic Effect Optimizer queries the DogEffects and DogPower ontologies to get all the domotic effects and their associated (device and power) information. The Domotic Effect Optimizer transforms the user request for particular values of domotic effects in to a correct set of Boolean equations and constraints, constructing a SAT problem. Then it feeds the SAT problem to a SAT solver. For the current implementation, the Sat4j [27] solver is used. Based on the set of Boolean equations, the Sat4j solver determines (if possible) the total number of configurations that satisfy the set of Boolean equations.

> *Fig. 2: Architecture of proposed approach — showing DogEffects ontology, DogPower ontology, and User Request R feeding into the Solver (Domotic Effect Optimizer), which constructs the SAT problem, applies heuristics via Sat4j library, and enforces the resulting configuration.*

### A. Heuristic

A novel power minimizing heuristic is proposed to determine in near real-time a configuration that consumes minimal electrical power and satisfies the user's request. Since the heuristic is called only when the solution space is large (> *T_c*), this degree of freedom is exploited by trying to switch off appliances that have the highest electrical power consumption.

Forcing a device to be switched off reduces the size of the solution space, but it might render the SAT problem infeasible. Therefore a greedy approach was adopted which tries to force all the involved devices off, one by one, starting from the highest-consuming SE. Those SE that render the problem infeasible are kept free in the SAT problem. The others are forced off. There is no guarantee that the configuration received after applying the heuristic has the minimum power consumption. There might be cases in which the combination of small power consuming devices in total consumes more than the device with high power consumption, but such conditions are rare and the experiments (Section VI) prove the configuration with minimum power value is usually achieved.

**Algorithm 1: Overall Approach**

```
SAT = SAT problem derived from F_R(g)
if (solvable(SAT)) then
    if (num_solutions(SAT) > T_c) then
        SAT = Heuristic Algorithm (SAT)
    end if
    device states = solve (SAT)
end if
```

**Algorithm 2: Heuristic Algorithm (SAT)**

```
sorted_SE = sort(all_SE, decreasing_power)
for all (SE in sorted_SE) do
    SAT' = SAT ∩ (SE = false)
    if (solvable (SAT')) then
        SAT = SAT'
    end if
end for
return SAT
```

---

## VI. Experimental Evaluation

To prove the validity of the proposed approach and measure the performance of the proposed heuristic, a set of experiments were carried out. The "Domotic Effect" modeling framework was developed and integrated with Dog2.1 [3] as a new *Domotic Effect Optimizer* bundle running in the Dog OSGi framework.

A complete house environment was simulated, whose domotic structure was modeled as an instance of DogOnt ontology. A new test bundle was developed to test the approach and the proposed heuristic. The house environment contains 1500 user-defined Domotic Effects. These DE correspond to generic goals like securing or illuminating the house.

The experiments have been run on a standard personal computer with a quad-core Intel i5 processor and 4 GB of RAM.

### A. Use Cases

In the experiments, all possible combinations of six use cases were enforced on the environment one after another. These use cases were *Secure Home*, *BathRoom Illumination*, *Home Illumination*, *Afternoon Lunch*, *Isolated Kitchen*, and *Morning Wakeup* scenarios.

- **Secure Home** — secures all the exit points of the house, i.e., all exit doors and windows. This use case comprises many DEs providing the ability to secure different rooms of the house. This can be used in case of emergency, theft, robbery, or fire.
- **BathRoom Illumination** — combines small use cases that represent alternative ways to illuminate the bathroom.
- **Home Illumination** — requires that all the rooms of the house are illuminated. Illumination can be either natural or artificial.
- **Afternoon Lunch** — deals with the daily routine of cooking lunch inside the kitchen.
- **Isolated Kitchen** — represents isolating the kitchen from the rest of the house during cooking hours; this scenario does not consider the energy spent for cooking, since that action is not automated.
- **Morning WakeUp** — maps a typical scenario when a resident wants to perform a sequence of activities after waking up in morning, like illuminating the bedroom, the kitchen, and the bathroom, switching off the gas heater inside the bedroom, switching on the kitchen television and the bathroom radio.

Since |**I**| = 6, there were 2⁶ = 64 possible user requests, or 63 if the trivial **R** = ∅ is omitted, where no domotic effect is enforced.

**Table I: Enumeration Approach Statistics**

| Secure Home | BathRoom Illumination | Home Illumination | Afternoon Lunch | Isolated Kitchen | Morning Wake Up | No. Of Configurations | Time (ms) |
|:-----------:|:---------------------:|:-----------------:|:---------------:|:----------------:|:---------------:|:---------------------:|:---------:|
| 0 | 0 | 0 | 0 | 0 | 1 | 32 | 220 |
| 0 | 0 | 0 | 0 | 1 | 0 | 3 | 16 |
| 0 | 0 | 0 | 0 | 1 | 1 | 32 | 56 |
| 0 | 0 | 0 | 1 | 0 | 0 | 3 | 18 |
| 0 | 0 | 0 | 1 | 0 | 1 | 32 | 65 |
| 0 | 0 | 0 | 1 | 1 | 0 | 3 | 13 |
| 0 | 0 | 0 | 1 | 1 | 1 | 32 | 73 |
| 0 | 0 | 1 | 0 | 0 | 0 | >100000 | unknown |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 10 |
| 0 | 0 | 1 | 0 | 1 | 0 | >100000 | unknown |
| 0 | 0 | 1 | 0 | 1 | 1 | 0 | 14 |
| 0 | 0 | 1 | 1 | 0 | 0 | >100000 | unknown |
| 0 | 0 | 1 | 1 | 0 | 1 | 0 | 15 |
| 0 | 0 | 1 | 1 | 1 | 0 | >100000 | unknown |
| 0 | 0 | 1 | 1 | 1 | 1 | 0 | 13 |
| 0 | 1 | 0 | 0 | 0 | 0 | 16 | 94 |
| 0 | 1 | 0 | 0 | 0 | 1 | 32 | 111 |
| 0 | 1 | 0 | 0 | 1 | 0 | 48 | 65 |
| 0 | 1 | 0 | 1 | 0 | 0 | 32 | 67 |
| 0 | 1 | 0 | 1 | 0 | 1 | 32 | 74 |
| 0 | 1 | 0 | 1 | 1 | 0 | 32 | 86 |
| 0 | 1 | 0 | 1 | 1 | 1 | 48 | 84 |
| 0 | 1 | 1 | 0 | 0 | 1 | 32 | 58 |
| 0 | 1 | 1 | 0 | 1 | 0 | >100000 | unknown |
| 0 | 1 | 1 | 0 | 1 | 1 | 0 | 11 |
| 0 | 1 | 1 | 1 | 0 | 0 | >100000 | unknown |
| 0 | 1 | 1 | 1 | 0 | 1 | 0 | 11 |
| 0 | 1 | 1 | 1 | 1 | 0 | >100000 | unknown |
| 0 | 1 | 1 | 1 | 1 | 1 | 0 | 11 |
| 1 | 0 | 0 | 0 | 0 | 0 | 192 | 534 |
| 1 | 0 | 0 | 0 | 0 | 1 | 0 | 12 |
| 1 | 0 | 0 | 0 | 1 | 0 | 48 | 97 |
| 1 | 0 | 0 | 0 | 1 | 1 | 0 | 16 |
| 1 | 0 | 0 | 1 | 0 | 0 | 48 | 95 |
| 1 | 0 | 0 | 1 | 0 | 1 | 0 | 19 |
| 1 | 0 | 0 | 1 | 1 | 0 | 48 | 113 |
| 1 | 0 | 0 | 1 | 1 | 1 | 0 | 14 |
| 1 | 0 | 1 | 0 | 0 | 0 | 2304 | 5100 |
| 1 | 0 | 1 | 0 | 0 | 1 | 0 | 18 |
| 1 | 0 | 1 | 0 | 1 | 0 | 576 | 1285 |
| 1 | 0 | 1 | 0 | 1 | 1 | 0 | 16 |
| 1 | 0 | 1 | 1 | 0 | 0 | 576 | 1424 |
| 1 | 0 | 1 | 1 | 0 | 1 | 0 | 15 |
| 1 | 0 | 1 | 1 | 1 | 0 | 576 | 1392 |
| 1 | 0 | 1 | 1 | 1 | 1 | 0 | 12 |
| 1 | 1 | 0 | 0 | 0 | 0 | 768 | 1421 |
| 1 | 1 | 0 | 0 | 0 | 1 | 0 | 13 |
| 1 | 1 | 0 | 0 | 1 | 0 | 192 | 394 |
| 1 | 1 | 0 | 0 | 1 | 1 | 0 | 13 |
| 1 | 1 | 0 | 1 | 0 | 0 | 192 | 416 |
| 1 | 1 | 0 | 1 | 0 | 1 | 0 | 50 |
| 1 | 1 | 0 | 1 | 1 | 0 | 192 | 417 |
| 1 | 1 | 0 | 1 | 1 | 1 | 0 | 13 |
| 1 | 1 | 1 | 0 | 0 | 0 | 2304 | 4650 |
| 1 | 1 | 1 | 0 | 0 | 1 | 0 | 39 |
| 1 | 1 | 1 | 0 | 1 | 0 | 576 | 1215 |
| 1 | 1 | 1 | 0 | 1 | 1 | 0 | 30 |
| 1 | 1 | 1 | 1 | 0 | 0 | 576 | 1195 |
| 1 | 1 | 1 | 1 | 0 | 1 | 0 | 9 |
| 1 | 1 | 1 | 1 | 1 | 0 | 576 | 1387 |
| 1 | 1 | 1 | 1 | 1 | 1 | 0 | 13 |

Table I shows the total number of configurations and the time taken by the exhaustive enumeration approach to find the total number of configurations, compute their power consumption and determine the configuration with minimum power consumption. The first 6 columns report which use cases are enforced (1) or not (0) by the user. The time is calculated in milliseconds. When the number of configurations were very large, the enumeration was stopped at 100,000.

For the application of the heuristic optimization, the problems that require more that one second to be enumerated were selected. From the analysis of the computation times in Table I, it is evident that these cases can be selected by choosing a threshold value *T_c* equal to 150.

From Table I, three types of cases are observed:

1. **Zero Configurations** — It refers to the case when the Sat4j solver cannot find a configuration satisfying the user's request, which means that the current combination of use cases can not be enforced together.
2. **Below Threshold** — It refers to the cases when the total number of configurations satisfying the user's request are less than *T_c*. In such cases, the enumeration approach is sufficient to determine in NRT a configuration with minimum power consumption and enforce it.
3. **Above Threshold** — It refers to the case when the total number of configurations satisfying the user's request exceeds the configuration threshold *T_c*. For such cases, the time to determine a configuration with minimum power consumption exceeds the NRT requirements, or is marked as *unknown*. Unknown refers to cases in which the number of configurations exceed 100,000. The enumeration approach is practically infeasible in such cases and the proposed heuristic must be applied.

### B. Results

To demonstrate the applicability and results of the proposed heuristic the Above Threshold cases were focused, only, since the exhaustive enumeration approach is sufficient for the Zero Configuration and Below Threshold cases, that have been dropped from the subsequent tables.

**Table II: Comparison of Solution Time (Milliseconds) Between the Enumeration Approach and the Proposed Heuristic Approach**

| Secure Home | BathRoom Illumination | Home Illumination | Afternoon Lunch | Isolated Kitchen | Morning Wake Up | No. Of Solution | Enumeration Solution Time (ms) | Heuristic Solution Time | Result |
|:-----------:|:---------------------:|:-----------------:|:---------------:|:----------------:|:---------------:|:---------------:|:------------------------------:|:-----------------------:|:------:|
| 0 | 0 | 1 | 0 | 0 | 0 | >100000 | unknown | 556 | Solved |
| 0 | 0 | 1 | 0 | 1 | 0 | >100000 | unknown | 743 | Solved |
| 0 | 0 | 1 | 1 | 0 | 0 | >100000 | unknown | 689 | Solved |
| 0 | 0 | 1 | 1 | 1 | 0 | >100000 | unknown | 1123 | Solved |
| 0 | 1 | 1 | 0 | 0 | 0 | >100000 | unknown | 829 | Solved |
| 0 | 1 | 1 | 0 | 1 | 0 | >100000 | unknown | 463 | Solved |
| 0 | 1 | 1 | 1 | 0 | 0 | >100000 | unknown | 760 | Solved |
| 0 | 1 | 1 | 1 | 1 | 0 | >100000 | unknown | 1172 | Solved |
| 1 | 0 | 0 | 0 | 0 | 0 | 192 | 534 | 506 | Good |
| 1 | 0 | 1 | 0 | 0 | 0 | 2304 | 5100 | 708 | Good |
| 1 | 0 | 1 | 0 | 1 | 0 | 576 | 1285 | 662 | Good |
| 1 | 0 | 1 | 1 | 0 | 0 | 576 | 1424 | 1299 | Good |
| 1 | 0 | 1 | 1 | 1 | 0 | 576 | 1392 | 907 | Good |
| 1 | 1 | 0 | 0 | 0 | 0 | 768 | 1421 | 443 | Good |
| 1 | 1 | 0 | 0 | 1 | 0 | 192 | 394 | 972 | Responsive |
| 1 | 1 | 0 | 1 | 0 | 0 | 192 | 416 | 578 | Responsive |
| 1 | 1 | 0 | 1 | 1 | 0 | 192 | 417 | 1252 | Responsive |
| 1 | 1 | 1 | 0 | 0 | 0 | 2304 | 4650 | 2358 | Good |
| 1 | 1 | 1 | 0 | 1 | 0 | 576 | 1215 | 1296 | Responsive |
| 1 | 1 | 1 | 1 | 0 | 0 | 576 | 1195 | 1018 | Good |
| 1 | 1 | 1 | 1 | 1 | 0 | 576 | 1387 | 1371 | Good |

Table II compares the time taken by the exhaustive enumeration approach against the time taken by the heuristic described in Section V-A to determine a configuration with minimal power usage. The *Enumeration Solution Time* column represents the time (in milliseconds) taken by the enumeration approach. The *Heuristic Solution Time* column represents the time (in milliseconds) taken by the heuristic. The *Result* column reports the comparison, i.e., Solved, Good, or Responsive. The case is "Solved" when the heuristic is able to find a configuration with minimal power consumption in NRT while the enumeration approach is infeasible. The "Good" cases mean that the heuristic solution is faster than enumeration, while the "Responsive" label means that the heuristic solution is slower but still well inside NRT.

**Table III: Comparison of Computed Power Value Between the Enumeration Approach and the Proposed Heuristic Approach**

| Secure Home | BathRoom Illumination | Home Illumination | Afternoon Lunch | Isolated Kitchen | Morning Wake Up | No. Of Solution | Enumeration Power Value | Enumeration Est. Power Value | Heuristic Power Value | Result |
|:-----------:|:---------------------:|:-----------------:|:---------------:|:----------------:|:---------------:|:---------------:|:----------------------:|:---------------------------:|:--------------------:|:------:|
| 0 | 0 | 1 | 0 | 0 | 0 | >100000 | N/A | 4047.02 | 5411.29 | Poor |
| 0 | 0 | 1 | 0 | 1 | 0 | >100000 | N/A | 3355.93 | 2763.87 | Better |
| 0 | 0 | 1 | 1 | 0 | 0 | >100000 | N/A | 4728.43 | 4136.37 | Better |
| 0 | 0 | 1 | 1 | 1 | 0 | >100000 | N/A | 4728.43 | 4136.37 | Better |
| 0 | 1 | 1 | 0 | 0 | 0 | >100000 | N/A | 3408.39 | 5411.29 | Poor |
| 0 | 1 | 1 | 0 | 1 | 0 | >100000 | N/A | 2961.98 | 2763.87 | Better |
| 0 | 1 | 1 | 1 | 0 | 0 | >100000 | N/A | 4334.48 | 4136.37 | Better |
| 0 | 1 | 1 | 1 | 1 | 0 | >100000 | N/A | 4334.48 | 4136.37 | Better |
| 1 | 0 | 0 | 0 | 0 | 0 | 192 | 0 | N/A | 0 | Equal |
| 1 | 0 | 1 | 0 | 0 | 0 | 2304 | 2583.16 | N/A | 2583.16 | Equal |
| 1 | 0 | 1 | 0 | 1 | 0 | 576 | 2763.87 | N/A | 2763.87 | Equal |
| 1 | 0 | 1 | 1 | 0 | 0 | 576 | 4136.37 | N/A | 4136.37 | Equal |
| 1 | 0 | 1 | 1 | 1 | 0 | 576 | 4136.37 | N/A | 4136.37 | Equal |
| 1 | 1 | 0 | 0 | 0 | 0 | 768 | 175.88 | N/A | 175.88 | Equal |
| 1 | 1 | 0 | 0 | 1 | 0 | 192 | 1146.36 | N/A | 1146.36 | Equal |
| 1 | 1 | 0 | 1 | 0 | 0 | 192 | 2518.86 | N/A | 2518.86 | Equal |
| 1 | 1 | 0 | 1 | 1 | 0 | 192 | 2518.86 | N/A | 2518.86 | Equal |
| 1 | 1 | 1 | 0 | 0 | 0 | 2304 | 2583.16 | N/A | 2583.16 | Equal |
| 1 | 1 | 1 | 0 | 1 | 0 | 576 | 2763.87 | N/A | 2763.87 | Equal |
| 1 | 1 | 1 | 1 | 0 | 0 | 576 | 4136.37 | N/A | 4136.37 | Equal |
| 1 | 1 | 1 | 1 | 1 | 0 | 576 | 4136.37 | N/A | 4136.37 | Equal |

Table III shows the comparison of the computed power consumption values between the enumeration and the heuristic approaches. The *Enumeration Power Value* column shows the minimum electrical power (Watt), when it can be exhaustively computed. The *Enumeration Est. Power Value* column shows the estimated minimum electrical power (Watt) found after 100,000 iterations. The column *Heuristic Power Value* shows the power value (Watt) of the configuration found by the heuristic. The *Result* column shows observations: Better, Poor, or Equal.

The size of the search space seems also to influence the effectiveness of the heuristic procedure: for example, the first row in Table III puts very few constraints over device states, and the heuristic is usable to find a good solution, while the second row adds some constraints (i.e., Isolated Kitchen), and the narrower search space allows to find a better solution. The same applies to rows 5 and 6.

### C. Discussion

In our experiments, a total of 63 iterations were performed, corresponding to each possible **R** defined over an environment with over 1500 declared DEs. Two performance comparisons were measured between the proposed heuristic and the enumeration approach:

- the comparison of time taken by the approaches to compute the best solution to the user's request (Table II);
- the consumed electrical power by the enforced settings of domotic effects (Table III).

From Table II, it can be seen that our proposed heuristic was able to solve all cases in NRT, even where the total number of configurations made the enumeration approach infeasible. Most cases took around 1 second to be solved by the heuristic. By observing the results, it can be stated that the proposed approach is feasible for integration with intelligent building systems.

Table III compares the power values of the configuration obtained using the enumeration and the heuristic approach. In cases where the total number of configurations were less than 100,000 it can be seen that the proposed heuristic always finds the configuration with the absolute minimum electrical power value. On the other hand, the cases in which the number of configurations exceeds 100,000, the heuristic was able to quickly solve all of them, and in most of the cases it was able to find a configuration that consumed less electrical power, compared to an (inapplicable) enumeration approach. Hence the experiments prove the feasibility of the complete approach as well as highlighting the robustness of the proposed optimization heuristic.

---

## VII. Conclusion

This paper tackles the minimization of power consumption from the point of view of individual buildings or homes. Smart environments may be equipped with an energy management system that is able to intelligently control the activation of devices and to minimize power accordingly, taking into account the varying requirements of the users. The approach exploits the degrees of freedom that are available when the users express their requirements at a higher level, in a user-intelligible way, rather than directly controlling the state of each device.

The Domotic Effects modeling framework that has been presented effectively enables users to easily express their needs at a higher level, by means of a Boolean formalization of the Domotic Effects enforcement and a SAT problem. The Boolean problem has been extended to minimize power consumption, in near real-time, while satisfying user requirements, and a heuristic algorithm has been proposed to find satisfactory power results while respecting timing constraints.

The extensive results reported on a case study show the feasibility and the robustness of the approach, making it suitable for adoption in smart environments. The proposed approach can be extended to include further constraints like reducing the number of state changes to conserve the lifetime of the appliances, or taking into account the energy needed to switch between states (e.g., for mechanically actuated devices).

Currently the work is being done towards a better integration of the approach in the Dog gateway open source distribution, and on devising intuitive user interfaces to monitor and control the environments through the Domotic Effects paradigm.

---

## References

[1] D. J. Cook, J. C. Augusto, and V. R. Jakkula, "Ambient intelligence: Technologies, applications, and opportunities," *Pervasive Mobile Comput.*, vol. 5, no. 4, pp. 277–298, 2009.

[2] D. Cook, M. Youngblood, E. Heierman III, K. Gopalratnam, S. Rao, A. Litvin, and F. Khawaja, "MavHome: An agent-based smart home," in *Proc. First IEEE Int. Conf. Pervasive Comput. Commun. (PerCom 2003)*, pp. 521–524.

[3] D. Bonino, E. Castellina, and F. Corno, "The dog gateway: Enabling ontology-based intelligent domotic environments," *IEEE Trans. Consum. Electron.*, vol. 54, no. 4, pp. 1656–1664, Nov. 2008.

[4] C. Ge, Y. Li, X. Zhi, and W. Tong, "The intelligent stb-implementation of next generation of residential gateway in digital home," in *Proc. 2nd Int. Conf. Pervasive Comput. Appl. (ICPCA 2007)*, pp. 256–261.

[5] Department of Energy, "2008 buildings energy data book," Buildings Technologies Program Energy Efficiency and Renewable Energy, Tech. Rep., 2009.

[6] S. Lukovic, V. Congradac, and F. Kulic, "A system level model of possible integration of building management system in smartgrid," *Complexity Eng.*, pp. 58–60, 2010.

[7] B. Davito, H. Tai, and R. Uhlaner, "The smart grid and the promise of demand-side-management," McKinsey & Co., Tech. Rep., 2011.

[8] P. Palensky and D. Dietrich, "Demand side management: Demand response, intelligent energy systems, and smart loads," *IEEE Trans. Ind. Informatics*, vol. 7, no. 3, pp. 381–388, 2011.

[9] H. Sui, Y. Sun, and W. Lee, "A demand side management model based on advanced metering infrastructure," in *Proc. 2011 4th Int. Conf. Elec. Util. Deregulation Restructuring Power Technol. (DRPT)*, pp. 1586–1589.

[10] A. Faruqui, R. Hledik, and J. Tsoukalis, "The power of dynamic pricing," *Electr. J.*, vol. 22, no. 3, pp. 42–56, 2009.

[11] I. Koutsopoulos and L. Tassiulas, "Challenges in demand load control for the smart grid," *IEEE Network*, vol. 25, no. 5, pp. 16–21, 2011.

[12] M. Pedrasa, T. Spooner, and I. MacGill, "Coordinated scheduling of residential distributed energy resources to optimize smart home energy services," *IEEE Trans. Smart Grid*, vol. 1, no. 2, pp. 134–143, 2010.

[13] P. McDaniel and S. McLaughlin, "Security and privacy challenges in the smart grid," *IEEE Security Privacy*, pp. 75–77, 2009.

[14] D. Bonino, F. Corno, and F. Razzak, "Enabling machine understandable exchange of energy consumption information in intelligent domotic environments," *Energy Buildings*, vol. 43, no. 6, pp. 1392–1402, 2011.

[15] N. Fumo, P. Mago, and R. Luck, "Methodology to estimate building energy consumption using energyplus benchmark models," *Energy Buildings*, vol. 42, no. 12, pp. 2331–2337, 2010.

[16] L. Pérez-Lombard, J. Ortiz, and C. Pout, "A review on buildings energy consumption information," *Energy Buildings*, vol. 40, no. 3, pp. 394–398, 2008.

[17] M. Weiss, F. Mattern, T. Graml, T. Staake, and E. Fleisch, "Handy feedback: Connecting smart meters with mobile phones," in *Proc. 8th Int. Conf. Mobile Ubiquitous Multimedia*, New York, 2009, ser. MUM'09, pp. 15:1–15:4.

[18] Y. Riche, J. Dodge, and R. A. Metoyer, "Studying always-on electricity feedback in the home," in *Proc. 28th Int. Conf. Human Factors Comput. Syst.*, New York, 2010, ser. CHI'10, pp. 1995–1998.

[19] S. Roberts, H. Humphries, and V. Hyldon, "Consumer preferences for improving energy consumption feedback," Centre for Sustainable Energy, Tech. Rep., 2004.

[20] T. Hubert and S. Grijalva, "Realizing smart grid benefits requires energy optimization algorithms at residential level," in *Proc. IEEE PES Innov. Smart Grid Technol. (ISGT)*, Jan. 2011, pp. 1–8.

[21] O. Sianaki, O. Hussain, T. Dillon, and A. Tabesh, "Intelligent decision support system for including consumers preferences in residential energy consumption in smart grid," in *Proc. 2010 2nd Int. Conf. Comput. Intell., Model., Simul.*, pp. 154–159.

[22] H. Zhang, X. Xia, and J. Zhang, "A residential energy and power conservation system utilizing an optimization model," in *Proc. AFRICON*, Sep. 2009, pp. 1–6.

[23] T. Kim and H. Poor, "Scheduling power consumption with price uncertainty," *IEEE Trans. Smart Grid*, vol. 2, no. 3, pp. 519–527, Sep. 2011.

[24] A.-H. Mohsenian-Rad and A. Leon-Garcia, "Optimal residential load control with price prediction in real-time electricity pricing environments," *IEEE Trans. Smart Grid*, vol. 1, no. 2, pp. 120–133, Sep. 2010.

[25] A. Mohsenian-Rad, V. Wong, J. Jatskevich, R. Schober, and A. Leon-Garcia, "Autonomous demand-side management based on game-theoretic energy consumption scheduling for the future smart grid," *IEEE Trans. Smart Grid*, vol. 1, no. 3, pp. 320–331, Dec. 2010.

[26] D. Bonino and F. Corno, "Dogont—Ontology modeling for intelligent domotic environments," in *Proc. 7th Int. Conf. Semantic Web*, Berlin, Germany, 2008, ser. ISWC'08, pp. 790–803.

[27] D. Le Berre and A. Parrain, "The Sat4j library, release 2.2 system description," *J. Satisfiability, Boolean Model., Comput.*, vol. 7, pp. 59–64, 2010.
