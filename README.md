# H1N1 Epidemic Simulation (2009)

## Overview

This repository contains a simulation study of the 2009 H1N1 influenza pandemic using network-based epidemic modeling.

The project was developed for the course *Network Dynamics and Learning* and includes:

- Simulation of epidemic spreading on structured and random networks  
- Implementation of a stochastic discrete-time SIR model  
- Vaccination modeling  
- Parameter estimation using real epidemic data  
- Model validation using RMSE  

All implementations and experiments are contained in `h1n1-epidemic-simulation` notebook.

## Epidemic Model

We use a discrete-time stochastic SIR (Susceptible–Infected–Recovered) model defined on a graph.

Each node represents an individual in one of three states:

- S — Susceptible  
- I — Infected  
- R — Recovered  

### Infection Probability

If a susceptible node has m infected neighbors:

$$
P(S \to I) = 1 - (1 - \beta)^m
$$

where:
- β is the infection probability per contact  
- m is the number of infected neighbors  

### Recovery Probability

$$
P(I \to R) = \rho
$$

where:
- ρ is the recovery probability  

---

## Network Models

The epidemic is simulated on:

1. A symmetric k-regular graph  
2. A preferential attachment random graph  

The preferential attachment model allows generation of networks with controllable average degree \( k \), capturing heterogeneous social contact structures.

---

## Vaccination Modeling

Vaccination is introduced as an absorbing state:

- Vaccinated individuals cannot become infected  
- Vaccinated individuals cannot infect others  
- Vaccination is applied weekly according to predefined schedules  

The vaccination rollout follows real data from the 2009 Swedish H1N1 campaign (using a scaled population model).

---

## Parameter Estimation

To approximate the real epidemic dynamics:

- The population is scaled down  
- Real infection data is used as reference  
- A gradient-based search is performed over:
  - Average degree k  
  - Infection probability β   
  - Recovery probability ρ

Model accuracy is evaluated using Root Mean Square Error (RMSE):

$$
RMSE = \sqrt{\frac{1}{T} \sum_{t=1}^{T} (I(t) - I_0(t))^2}
$$

The optimal parameter set minimizes the RMSE between simulated and real infection curves.

---

## Implementation

- Language: Python  
- Libraries: NumPy, SciPy, NetworkX, Matplotlib  

---

## Report

The file `report.pdf` contains the complete lab report, including:

- Detailed explanation of the SIR epidemic model  
- Network generation methodology (k-regular and preferential attachment)  
- Vaccination modeling strategy  
- Parameter estimation procedure  
- RMSE-based model validation  
- Simulation results and plots  
- Discussion of findings and conclusions  

The report is written as a standalone document and can be read independently of the code.

---

## Learning Outcomes

- Understanding epidemic spreading on networks  
- Impact of network topology on disease dynamics  
- Effectiveness of vaccination strategies  
- Practical parameter estimation in stochastic models  
