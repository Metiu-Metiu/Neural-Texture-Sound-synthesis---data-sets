# Synthetic and Real Datasets
Synthetic sounds datasets and real sounds datasets of waterflow sounds for the repo 'Neural-Texture-Sound-Synthesis-with-physically-driven-continuous-controls'.

In the context of synthetic-to-real Unsupervised Domain Adaptation, a synthetic sounds dataset is created together with the Synthesis Control Parameters used to generate the sounds.
Then, a Neural Network is trained on the supervised task of extracting the Synthetis Control Parameters from the synthetic sounds.
Afterwards, Domain Adaptation is performed on the Network; since it is trained on the synthetic data distribution, the latent representation of the real sounds dataset is shifted to resemble as much as possible 
the representation of the synthetic dataset. By doing so, we can extract Synthesis Control Parameters from un-labelled real sounds datasets.

The synthetic datasets are created using Max 8 and the SDT_v2.2-078 (Sound Design Toolkit, https://github.com/SkAT-VG/SDT) as Sound Engine. The probability distribution of each Synthesis Control Parameter is managed by the 'Creation_of_synthetic_Audio_datasets.py' file, and its relative JSON dictionary interface, in the SMC_Thesis repository (https://github.com/Metiu-Metiu/Neural-Texture-Sound-Synthesis-with-physically-driven-continuous-controls). Please have a look at the documentation of that repository for specifics on the creation of the Synthetic Sounds Datasets.
The real sounds datasets are subsets of the FSD50K dataset (https://zenodo.org/record/4060432, https://annotator.freesound.org/fsd/release/FSD50K/). Please refer to the script 'Creation_of_Audio_segmentedSubsets_of_datasets.py' in the Neural-Texture-Sound-Synthesis-with-physically-driven-continuous-controls repository (https://github.com/Metiu-Metiu/Neural-Texture-Sound-Synthesis-with-physically-driven-continuous-controls) for specifics on Real Sounds datasets creation.

# Synthetic waterflow sounds datasets
All synthetic waterflow sounds datasets have been synthesised controlling 4 Synthesis Control Parameters;
- avgRate (float): Average n. of bubbles per second [0.0, 100000.0]
- minRadius (float): Minimum bubble radius [0.15, 150.0]
- maxRadius (float): Maximum bubble radius [0.15, 150.0]
- expRadius (float): Bubble radius gamma factor [0.0, 10.0]

Each dataset's folder contains a .csv file with the Synthesis Control Parameters' values used at the synthesis stage (usable as ground truth), and a .json file representing the JSON dictionary interface with the settings used by the user who created the dataset (e.g. number of sound files, ecc.)

## SDT_FluidFlow_dataset_1000_1sec
Synthetic waterflow sounds dataset created with the SDT_v2.2-078 (Sound Design Toolkit) Max 8 patch.
There are 1,000 sounds samples, each of 1 second duration, 44.1 kHz sample rate.
The Synthesis Control Parameters distribution is UNIFORM_CONTROLLABLE_VARIANCE_LINEARLY_SPACED_VALUES_UNIFORM_JOINT_DISTRIBUTION (see 'Creation_of_synthetic_Audio_datasets.py').

## SDT_FluidFlow_dataset_1000_1sec_UNIFORM_LINEARLY_SPACED_VALUES
Synthetic waterflow sounds dataset created with the SDT_v2.2-078 (Sound Design Toolkit) Max 8 patch.
There are 1,000 sounds samples, each of 1 second duration, 44.1 kHz sample rate.
The Synthesis Control Parameters distribution is UNIFORM_LINEARLY_SPACED_VALUES (see 'Creation_of_synthetic_Audio_datasets.py').

## SDT_FluidFlow_dataset_10000_1sec
Synthetic waterflow sounds dataset created with the SDT_v2.2-078 (Sound Design Toolkit) Max 8 patch.
There are 10,000 sounds samples, each of 1 second duration, 44.1 kHz sample rate.
The Synthesis Control Parameters distribution is UNIFORM_CONTROLLABLE_VARIANCE_LINEARLY_SPACED_VALUES_UNIFORM_JOINT_DISTRIBUTION (see 'Creation_of_synthetic_Audio_datasets.py').

# Real waterflow sounds datasets
The real waterflow sounds datasets are subsets of the FSD50K dataset.
While creating the subset (script 'Creation_of_Audio_segmentedSubsets_of_datasets.py' in the SMC_thesis repository -https://github.com/Metiu-Metiu/SMC_thesis-), each file's tag in the canonical FSD50K dataset is compared against 2 list, specified in the 'Creation_of_Audio_segmentedSubsets_of_datasets.py' file. One list refers to the labels that need to be present in the subset, the oher list refers to the labels that are to be excluded from the created subset (the files labelled with those labels are not included in the subset).
You can find these specifications in the '_creatorDescriptorDict.json' file, among the other settings used while creating the subsets.
Each file in the subset is also further segmented in subsequent chunks of a pre-determined smaller duration.

## FSD50K_Water_Stream_subset
Subset of the FSD50K dataset containing waterflow sounds of 3 seconds duration each.

## FSD50K_Water_Stream_subset_1sec
Subset of the FSD50K dataset containing waterflow sounds of 1 second duration each.

# Shower sounds datasets
20 minutes recordings of a household shower waterflow sound, recorded while manually adjusting the water flow amount (approximately every 2 minutes, the shower handle was turned clockwise 1/10 of its full range).
Unsegmented_20Minutes_shower_withDifferentFlowRates is the original dataset sampled at 16 kHz. The others are segmented/upsampled versions of it, with .params files created for the conditional training of the MTCRNN model (https://github.com/lonce/MTCRNN.Fork) by Lonce Wyse. The .params files were created by running inference on the Synthesis Parameters Extractor network (https://github.com/Metiu-Metiu/Neural-Texture-Sound-synthesis---trained-Neural-Networks/tree/main/2D_CNN_SynthParamExtractor_June26_2023_Batch128_NoDropouts_10000Dataset_32kHz_3FCLayers_4ConvFilters_IncreasedNumberOfChannels_BatchNorm_DBScale) with this recorded shower dataset.
