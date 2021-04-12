# Source data of molDiscovery paper
All the source data are available at Zenodo repository at [here](). See the following description for each dataset.

## `gnps/` directory
This contains data concerning the experiment searching the GNPS subset containing NIH natural products library spectra against DNP.
This contains three subdirectories: `gnps/accuracy/`, `gnps/time_and_memory/`, `gnps/mass_ranges/`.
The raw outputs of each method are not included to avoid re-distributing DNP structures without permission.

The `accuracy` directory contains a CSV for each method tested that indicates via a binary label for every tested spectrum whether the correct compound was in the top 1, top 3, top 5, and top 10 highest scoring compounds.
These CSVs were directly used to construct the plot comparing accuracies for the GNPS vs DNP experiment.

The `time_and_memory` directory contains the output of GNU time with the `-v` flag for each spectrum for every method. These are saved in `.time` files.
The CFM-ID and molDiscovery `.time` files are for running *after* preprocessing.
For CFM-ID and molDiscovery preprocessing a separate set of `.time` files is indicated with the `_preprocessing` suffix.
To compute total runtime the elapsed times were summed.
To compute maximum memory usage the maximum of the maximum resident set size over all spectra was computed.

The `mass_ranges` directory contains the ClassyFire superclass and mass for every spectrum tested.
It also contains `.time` files for CFM-ID and molDiscovery when run *without* pre-processing, for use in mass-window based scaling comparisons.

The `gnps/gnps_nih.ids` file contains the GNPS SPECTRUMID for all the spectra used in this experiment.
The `gnps/gnps_nih_no_csi_training.ids` file contains the GNPS SPECTRUMID for all the spectra used in this experiment where the true compound does not appear in the CSI:FingerID training dataset.
The `gnps/folds.csv` contains the cross-validation fold assignments.
The `gnps/accuracy.csv` and `gnps/accuracy_no_csi_training.csv` files contain the actual data plotted for accuracy comparison when CSI:FingerID training structures are not removed and are removed respectively.
The `gnps/tanimoto.csv` contains the accuracy for a given maximum Tanimoto similarity to the training dataset for both CSI:FingerID and molDiscovery.

## `mona/` directory
This contains data concerning the experiment searching MoNA spectra against a database of MoNA structures.
This contains two subdirectories: `mona/accuracy/` and `mona/raw/`.

The `raw` subdirectory contains raw outputs for each method.

The `accuracy` directory contains a CSV for each method tested that indicates via a binary label for every tested spectrum whether the correct compound was in the top 1, top 3, top 5, and top 10 highest scoring compounds.
These CSVs were directly used to construct the plot comparing accuracies for the MoNA experiment.

The `mona/mona.ids` file contains the IDs of the MoNA spectra used in this experiment.
The `mona/mona_no_csi_training.ids` file contains the IDs of the MoNA spectra used in this experiment where the true compound does not appear in the CSI:FingerID training dataset.

## `bond_types` directory
This contains data concerning the experiment of incorporating different bond types.
It was run on a subset of NIST20, which is not publicly available so raw data is not included.
This contains one subdirectory: `bond_types/accuracy/`.

The `accuracy` directory contains a CSV for each set of bond types tested that indicates via a binary label for every tested spectrum whether the correct compound was in the top 1, top 3, top 5, and top 10 highest scoring compounds.
These CSVs were directly used to construct the plot comparing accuracies for the bond type experiment.

The `bond_types/nist.ids` file contains the NISTNO for every NIST spectrum used in this test.
The `bond_types/accuracy.csv` file contains the actual data plotted for accuracy comparison.
The `bond_types/folds.csv` file contains the cross-validation fold assignment.

## `bgc` directory
This directory contains antismash results of three putative biosynthetic gene clusters reported in the paper. 

- `bgc/bgc.info.txt` bgc information
- `bgc/antismash/` antismash searching results of the three BGCs.

## `large_scale_spectral_search` directory
This directory contains the large scale spectral datasets searching results of 46 GNPS spectral datasets by molDiscovery.
- `large_scale_spectral_search/NIST17/`: NIST17 spectral library search results 
- `large_scale_spectral_search/Dereplicator+/`: Dereplicator+ search results 
- `large_scale_spectral_search/molDiscovery/`: molDiscovery search results. 

## `negative` directory
This directory contrains molDiscovery search results of negative mode spectra in GNPS spectral library. 
- `negative/all_matches.tsv` molDiscovery search results.
- `negative/final_neg_mode.ids`  negative mode spectra id.

## `pseudomonas` directory
Search results of pseudomonas dataset MSV000079450.
- `Pseud.molDisc.top100.annotated.tsv` top 100 identifications by molDiscovery
- `Pseud.Dereplicator+.top100.annotated.tsv` top 100 identifications by Dereplicator+
