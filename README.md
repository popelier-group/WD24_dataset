# WD24_dataset
WD24 dataset is a water dimer dataset consisting of 100,000 geometries generated without molecular dynamics simulations. The dataset intends to uniformly sample the water dimer configuration space.

The contents of the files are:

`WD24_geometries.xyz` - all 100,000 generated water dimer geometries
`processed_data` - ALF descriptors as well as IQA energy, atomic multipole moments, and total energy. The data has already been filtered to remove points for which the absolute integration error associated with the AIMAll calculations is higher than 0.001. Since each atom, has its own dataset, a slightly different number of points is removed, depending on the integration error of the individual atom. Also, points for which the sum of the atomic IQA energies is off by more than 1 kJ mol<sup>-1</sup> from the total system energy
`processed_data_intersection` - Contains the exact same geometries across all atoms. While the molecular geometries are the same, the ALF descriptors calculated for each atom are going to be different. Every atom has a dataset size of 87,711 geometries from which a training set and test set are obtained.
