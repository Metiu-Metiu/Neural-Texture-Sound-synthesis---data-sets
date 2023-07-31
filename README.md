# Synthetic and Real Datasets
Synthetic sounds datasets and real sounds datasets of waterflow sounds for the repo 'SMC_Thesis'.

In the context of synthetic-to-real Unsupervised Domain Adaptation, a synthetic sounds dataset is created together with the Synthesis Control Parameters used to generate the sounds.
Then, a Neural Network is trained on the supervised task of extracting the Synthetis Control Parameters from the synthetic sounds.
Afterwards, Domain Adaptation is performed on the Network; since it is trained on the synthetic data distribution, the latent representation of the real sounds dataset is shifted to resemble as much as possible 
the representation of the synthetic dataset. By doing so, we can extract Synthesis Control Parameters from un-labelled real sounds datasets.

The synthetic datasets are created with Max 8 and the SDT_v2.2-078 (Sound Design Toolkit).
The real sounds datasets are subset of the FSD50K dataset.

See 'SMC_Thesis' repo for more details.
