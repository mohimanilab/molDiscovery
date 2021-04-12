# Source data of molDiscovery paper
All the source data of molDiscovery paper are available at [Zenodo](https://zenodo.org/record/4680231#.YHTJLxRKhZh). See the following description for each dataset.

## `gnps/` directory
This contains data concerning the experiment searching the GNPS subset containing NIH natural products library spectra against DNP.
This contains three subdirectories: `gnps/accuracy/`, `gnps/time_and_memory/`, `gnps/mass_ranges/`.
The raw outputs of each method are not included to avoid re-distributing DNP structures without permission.

- `gnps/accuracy` directory contains a CSV for each method tested that indicates via a binary label for every tested spectrum whether the correct compound was in the top 1, top 3, top 5, and top 10 highest scoring compounds. These CSVs were directly used to construct the plot comparing accuracies for the GNPS vs DNP experiment.
- `gnps/time_and_memory` directory contains the output of GNU time with the `-v` flag for each spectrum for every method. These are saved in `.time` files. The CFM-ID and molDiscovery `.time` files are for running *after* preprocessing. For CFM-ID and molDiscovery preprocessing runtimes there are a separate set of `.time` files, indicated with the `_preprocessing` suffix. To compute total runtime the elapsed times were summed.
To compute maximum memory usage the maximum of the maximum resident set size over all spectra was computed.
- `gnps/mass_ranges` directory contains the ClassyFire superclass and mass for every spectrum tested. It also contains `.time` files for CFM-ID and molDiscovery when run *without* pre-processing, for use in mass-window based scaling comparisons.
- `gnps/gnps_nih.ids` file contains the GNPS SPECTRUMID for all the spectra used in this experiment.
- `gnps/gnps_nih_no_csi_training.ids` file contains the GNPS SPECTRUMID for all the spectra used in this experiment where the true compound does not appear in the CSI:FingerID training dataset, as determined by 14-character InChIKey prefix matching.
- `gnps/folds.csv` contains the cross-validation fold assignments.
- `gnps/accuracy.csv` and `gnps/accuracy_no_csi_training.csv` files contain the actual data plotted for accuracy comparison when CSI:FingerID training structures are not removed and are removed respectively.
- `gnps/tanimoto.csv` contains the accuracy for a given maximum Tanimoto similarity to the training dataset for both CSI:FingerID and molDiscovery.

## `mona/` directory
This contains data concerning the experiment searching MoNA spectra against a database of MoNA structures.
This contains two subdirectories: `mona/accuracy/` and `mona/raw/`.

- `raw` subdirectory contains raw outputs for each method.
- `accuracy` directory contains a CSV for each method tested that indicates via a binary label for every tested spectrum whether the correct compound was in the top 1, top 3, top 5, and top 10 highest scoring compounds.
These CSVs were directly used to construct the plot comparing accuracies for the MoNA experiment.
- `mona/mona.ids` file contains the IDs of the MoNA spectra used in this experiment.
- `mona/mona_no_csi_training.ids` file contains the IDs of the MoNA spectra used in this experiment where the true compound does not appear in the CSI:FingerID training dataset.

## `csi-fingerid` raw data
Since the output files of csi-fingerid on MoNA benchmarking are very large. We split the files into five batches as follows:
- `mona_csi-fingerid_raw_batch1.tar` 
- `mona_csi-fingerid_raw_batch2.tar` 
- `mona_csi-fingerid_raw_batch3.tar` 
- `mona_csi-fingerid_raw_batch4.tar` 
- `mona_csi-fingerid_raw_batch5.tar` 


## `bond_types` directory
This contains data concerning the experiment of incorporating different bond types.
It was run on a subset of NIST20, which is not publicly available so raw data is not included.
This contains one subdirectory: `bond_types/accuracy/`.

- `bond_types/accuracy` directory contains a CSV for each set of bond types tested that indicates via a binary label for every tested spectrum whether the correct compound was in the top 1, top 3, top 5, and top 10 highest scoring compounds. These CSVs were directly used to construct the plot comparing accuracies for the bond type experiment.
- `bond_types/nist.ids` file contains the NISTNO for every NIST spectrum used in this test.
- `bond_types/accuracy.csv` file contains the actual data plotted for accuracy comparison.
- `bond_types/folds.csv` file contains the cross-validation fold assignment.

## `platform` directory
This contains data concerning evaluation of molDiscovery's sensitivity to variation in fragmentation mode.

- `platform/frag_cid.ids` MoNA IDs for CID mode spectra used for this test.
- `platform/frag_hcd.ids` MoNA IDs for HCD mode spectra used for this test.
- `platform/dereplicator+_platform.csv` raw outputs for Dereplicator+, while the `platform/dereplicator+_platform_results.csv` file contains accuracies.
- `platform/train_cid.csv` raw outputs for molDiscovery retrained on the CID spectra, while the `platform/train_cid_results.csv` file contains accuracies.
- `platform/train_hcd.csv` file contains raw outputs for molDiscovery retrained on the HCD spectra, while the `platform/train_hcd_results.csv` file contains accuracies.

## `charge2` directory
This contains data concerning evaluation of molDiscovery's performance on doubly charged spectra.
- `charge2/charge2.ids` MoNA IDs for spectra with charge +2 used as an evaluation dataset.
- `charge2/raw_dereplicator+_outputs.txt` raw Dereplicator+ outputs on this charge +2 dataset.
- `charge2/raw_moldiscovery_outputs.txt` raw molDiscovery outputs on this charge +2 dataset after model fine-tuning using high-confidence Dereplicator+ identifications from AntiMarin.
- `charge2/charge2_results.csv` accuracies for both methods.

## `lipid` directory
This contains data concerning evaluation of molDiscovery's ability to correctly identify lipids using the PNNL lipid library in GNPS and searching against LipidMaps.

- `lipid/gnps_lipidmaps_map.csv` file maps GNPS spectrum IDs to LipidMap IDs.
- `lipid/splits/` GNPS IDs and MGF files for four splits of the PNNL data, with PEPMASS modified from a [M]+ adduct to a [M+H]+ adduct. These splits were just made for parallelism.
- `lipid/raw_outputs/` raw molDiscovery outputs for each of the above splits.
- `lipid/topn.csv` a per-spectrum evaluation of accuracy (with binary indidcators for each spectrum indicating if the correct molecule was in the top 1, 3, 5, or 10 scoring candidates).
- `lipid/accuracy.txt` accuracies for molDiscovery.


## `bgc` directory
This directory contains antismash results of three putative biosynthetic gene clusters reported in the paper. 

- `bgc/bgc.info.txt` bgc information
- `bgc/antismash/` antismash searching results of the three BGCs.

## `large_scale_spectral_search` directory
This directory contains the large scale spectral datasets searching results of 46 GNPS spectral datasets by molDiscovery.
- `large_scale_spectral_search/NIST17/`: NIST17 spectral library search results 
- `large_scale_spectral_search/Dereplicator+/`: Dereplicator+ search results 
- `large_scale_spectral_search/molDiscovery/`: molDiscovery search results. 

## `large_molecular_databases_search` directory
This directory contains the searching results against large scale spectral datasets by molDiscovery and magma+.
- `moldiscovery`
- `magma` magma searching results 
- `metadata` information of spectra from Vaniya/Fiehn Natural Products Library obtained on Q-Exactive HF instruments, bio-pubchem molecules and MoNA molecules.

## `human_plant`
This directory contains molDiscovery search results of human serum spectra and plant spectra. 
- `human_plant/human/` molDiscovery results on MSV000084092 dataset
- `human_plant/plant/` molDiscovery results on MSV000086427 dataset

## `negative` directory
This directory contains molDiscovery search results of negative mode spectra in GNPS spectral library. 
- `negative/all_matches.tsv` molDiscovery search results.
- `negative/final_neg_mode.ids`  negative mode spectra id.

## `pseudomonas` directory
Search results of pseudomonas dataset MSV000079450.
- `Pseud.molDisc.top100.annotated.tsv` top 100 identifications by molDiscovery
- `Pseud.Dereplicator+.top100.annotated.tsv` top 100 identifications by Dereplicator+
