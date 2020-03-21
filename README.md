# Muon-Momentum-Estimation-and-Particle-Identification
Muon momentum estimation and particle type identification using GNNs and other deep learning variants

## Key points
The details of problem solved can be found in file [Task details](https://github.com/PRATEEKKUMARAGNIHOTRI/Muon-Momentum-Estimation-and-Particle-Identification/blob/master/Task%20details.pdf). Their solutions with well explained codes can be found in jupyter notebooks.

Some key points of the solutions are -

### Task-3:

(Input --> Node representation --> Graph representation --> Classify)

+ Used Pytorch geometric to code

+ Fully connected graph topology with learnable edge features in intermediate MPL layers (Reference - https://dl4physicalsciences.github.io/files/nips_dlps_2017_29.pdf )

+ Custom written MPL convolution layer and SAGE convolution are used to generate node representation

+ TopKPooling to get relevant nodes

+ Global Mean Pooling and Global Max pooling to generate graph representation

+ Skip or residual connections are added to all layers ( i.e. graph convolution layers, pooled graph representations and dense layers)

+ Dropout in dense layers

### Task-2:

![Attached image](https://github.com/PRATEEKKUMARAGNIHOTRI/Muon-Momentum-Estimation-and-Particle-Identification/blob/master/raw/Model%20Architecture%20Task2.PNG)

+ Path of particles are projected in XY, YZ and XZ planes and converted into images

+ Obtained single channel images are passed to three different CNNs

+ Other features are passed through a dense NN

+ Output of three fully connected CNNs and a dense NN are concatenated and passed to a dense NN to generate output

### Task-1:

+ Features are standarized

+ Features with zero variance are dropped

+ nan is replaced with zero

+ A dense NN is trained

+ Callbacks like - Save best model, early stopping, reduce lr on plateau are used durong training models of all three tasks

Note - Due to less time and limited colab hardware, task two and three are trained using a subsample of entire datasets (1500 samples in task 2 and 1 npz file in task 3), but samples are sufficient enough to show that code is working and models are training quite well.

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
