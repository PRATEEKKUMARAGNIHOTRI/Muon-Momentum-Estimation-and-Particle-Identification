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
The second array ‘parameters’ contains 3 columns.<br><br>

Column | 0 | 1 | 2 
--- | --- | --- | ---
Parameters | q/pt | Phi angle | Eta angle

Note: in the dataset, a unit in phi is 1/60 = 0.01667 deg, a unit in theta is approx 0.285 deg.

## Dataset for Task 3
Task 3 uses ParticleNet’s data for Quark/Gluon jet classification available [here](https://zenodo.org/record/3164691#.Xk1VwS2B1QI).<br> 
In particle physics, a jet is associated with a spray of particles spread across the detector, and we are interested in identifying the elementary particle that initiated the decays forming this jet. <br> The dataset contains 2 million jet events detected at CMS with a transverse momentum range from 500 GeV to 550 GeV and rapidity < 1.7. These jets were constructed with the anti-kt algorithm with R=0.4. The dataset contains information about the particles in each jet. It is split into 20 Npz files  each of which contains 2 Numpy arrays: X of shape (100000,M,4) where 100,000 is the number of jets per file,  M is the max multiplicity of the jets and 4 is the number of features per point cloud (particle). The four features are the particle’s pt, rapidity, azimuthal angle and pdgid. The second Numpy file y and contains the class label for each jet: label 0 is assigned for gluons and label 1 for quarks.  
