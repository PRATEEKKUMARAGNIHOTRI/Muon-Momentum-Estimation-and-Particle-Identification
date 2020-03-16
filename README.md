# Muon-Momentum-Estimation-and-Particle-Identification
Muon momentum estimation using GNNs and other deep learning variants

## Dataset for Task 1 and 2
The first two tasks use Monte-Carlo simulated data from the Cathode Strip Chambers (CSC) at the CMS experiment.
These chambers detect muon particles in the outer layer of the CMS detector, allowing us to store information about the hit locations.<br>

The [dataset](https://www.dropbox.com/s/c1pzdacnzhvi6pm/histos_tba.20.npz?dl=0) is an npz file containing 2 numpy arrays ‘variables’ and ‘parameters’. <br><br>The first array ‘variables’ contains 87 features, 84 of which serve as input variables and 3 other serving as road variables. This is due to the fact that we have 12 detector planes in the CSCs, each of which contains 7 features (12*7=84).

Column range | 0-11 | 12-23 | 24-35 | 36-47 | 48-59 | 60-71 | 72-83 | 84 | 85 | 86
--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |--- 
Particle hit features | Phi Coordinate | Theta coordinate | Bending angle | Time info | Ring number | Front/rear hit | Mask | Pattern straightness | Zone | Median theta 

<br>
The second array ‘parameters’ contains 3 columns.<br>

Column | 0 | 1 | 2 
--- | --- | --- | ---
Parameters | q/pt | Phi angle | Eta angle

Note: in the dataset, a unit in phi is 1/60 = 0.01667 deg, a unit in theta is approx 0.285 deg.
