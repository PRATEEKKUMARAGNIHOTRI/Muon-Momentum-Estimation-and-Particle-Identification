# Muon-Momentum-Estimation-and-Particle-Identification
Muon momentum estimation using GNNs and other deep learning variants

## Dataset for Task 1 and 2
The first two tasks use Monte-Carlo simulated data from the Cathode Strip Chambers (CSC) at the CMS experiment.
These chambers detect muon particles in the outer layer of the CMS detector, allowing us to store information about the hit locations. The latter are measured using the pseudo-rapidity  and the azimuth angle  as shown in Figure 1. Our dataset consists of more than 3 million muon events generated using Pythia and could be downloaded from the following link. As can be seen, the dataset is an npz file containing 2 numpy arrays ‘variables’ and ‘parameters’. The first array ‘variables’ contains 87 features, 84 of which serve as input variables and 3 other serving as road variables (pattern straightness, zone, median theta, respectively). This is due to the fact that we have 12 detector planes in the CSCs, each of which contains 7 features (12*7=84). For a better perspective on the data format of this array please refer to Table 3. The second array ‘parameters’ contains 3 columns described in Table 4. 
