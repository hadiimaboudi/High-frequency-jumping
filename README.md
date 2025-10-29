# High-Frequency Jumping
# Overview

This repository contains the code and analysis tools and simulation model of the early stages of the fly visual system, used in the paper "Synaptic high-frequency jumping synchronises vision to high-speed behaviour".

# Repository Structure

--  Model/
      Contains scripts and functions to simulate the Musca photoreceptor–LMC (Large Monopolar Cell) model. It model the process from light abstroption in photoreceptors (R1-R6) to the voltage response of the LMC.

The model simulates several complex biophysical processes:

1- Receptive Fields: Generation of Gaussian receptive fields.

2- Microsaccades: Physical movement of the rhabdomeres, which dynamically alters the receptive fields.

3- Quantal Sampling: Stochastic light absorption (Poisson process) in individual microvilli.

4- Photoreceptor Voltage: Simulation of the photoreceptor membrane potential based on quantal bumps.

5- Stochastic Synapse: A model of synaptic transmission from the photoreceptor to the LMC, including latency and refractory periods.

6- LMC Voltage: Simulation of the LMC membrane, which receives input from the photoreceptors.

7- Synaptic Feedback: A feedback loop where the LMC voltage modulates the photoreceptor's synaptic release probability.

- The code is structured into main scripts, core simulation functions, and helper utilities.

- How to Run the Example
The primary example script to run the full simulation is BurstyCalculationExample.m. Running this script will execute the full simulation pipeline:

a- Load Data: It loads the stimulus from Bursty_stim_photo_hres_200.mat.

b- Simulate Photoreceptors (Absorption): It calls MultipleRhabdomerewithScreen.m. This script: Sets up the parameters for 6 ommatidia, including lens positions, rhabdomere properties, and microsaccade movement physics.

c- Calls Lightmodelsimplewithfeedback2.m in a parallel loop (parfor) to simulate the quantal absorption for each photoreceptor.

d- Simulate Photoreceptor (Voltage): It calls CombinedAfterLatency.m to convert the discrete quantal absorption events (AfterLatency_a) into a continuous photoreceptor membrane voltage (Photovoltage).

e- Simulate LMC (Voltage): It calls PhotoLMCsimulationFeedback6.m, which takes the Photovoltage as input. This script simulates the stochastic synapse and the LMC membrane response, including the feedback loop.

f- Plot Results: Finally, it generates a figure with three subplots showing: The input light intensity, the simulated membrane voltage of the 6 photoreceptors, the final simulated LMC membrane voltage.

--  BarAnalysis/
      Includes software and scripts for analysing visual responses to narrowing bar stimuli.





