# WD24_dataset
WD24 dataset is a water dimer dataset consisting of 100,000 geometries generated without molecular dynamics simulations. The dataset intends to uniformly sample the water dimer configuration space.

The contents of the files are:

`WD24_geometries.xyz` - all 100,000 generated water dimer geometries
`processed_data` - ALF descriptors as well as IQA energy, atomic multipole moments, and total energy. The data has already been filtered to remove points for which the absolute integration error associated with the AIMAll calculations is higher than 0.001. Since each atom, has its own dataset, a slightly different number of points is removed, depending on the integration error of the individual atom. Also, points for which the sum of the atomic IQA energies is off by more than 1 kJ mol<sup>-1</sup> from the total system energy
`processed_data_intersection` - Contains the exact same geometries across all atoms. While the molecular geometries are the same, the ALF descriptors calculated for each atom are going to be different. Every atom has a dataset size of 87,711 geometries from which a training set and test set are obtained.

`WD24.npz` - A numpy .npz file which contains the WD24 dataset results:

```python
import numpy as np

f = np.load("WD24.npz")

coordinates = f["coordinates"] # shape: (100000, 6, 3),  ntimesteps x natoms x 3
total_energy = f["total_energy"] # shape: (100000,),  ntimesteps
forces = f["forces"] # shape: (100000, 6, 3), ntimesteps x natoms x 3
iqa_energy = f["iqa_energy"] # shape: (100000, 6) ntimesteps x natoms
integration_error = f["integration_error"] # shape: (100000, 6) ntimesteps x natoms
```


The ordering of the atoms is O, H, H, O, H, H and is the same ordering as in the WD24.xyz trajectory file.

`B3LYP/aug-cc-pVTZ` level of theory is used for the calculations in the dataset.
