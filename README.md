These are the scripts to reproduce figures in the paper "How learning reweights the decision dynamics of cortico-basal ganglia-thalamic pathways from deliberation to commitment" https://doi.org/10.64898/2026.02.17.706272

The CBGT network codebase (**CBGTPy**) utilized in this study is publicly available at https://github.com/CoAxLab/CBGTPy. Detailed installation instructions and a comprehensive list of implemented functions can be found in the README.txt file within the repository.

`Data/` is organized by learning stage in Post-0, Post-1, Post-3, Post-8, Post-15, and Post-30, corresponding to the number of training trials. Within each stage, `slow/network_N/` contains saved simulation results (via CBGTPy), 10-ms firing rates, binary activity, and CLAW state labels. Stage-level `W_time_all_onset.csv` files contain control ensemble and DDM parameter time courses; `traj_classes.pickle` maps trajectory types to (network, trial) pairs. In particular,

| Path | Use |
| --- | --- |
| `manuscript/F_matrix.npy` | Neural feature matrix used to fit CCA; 18 columns |
| `manuscript/D_matrix.npy` | Matching stored DDM parameter matrix; columns `a, v, t, z` |
| `manuscript/slow_indices.pickle` | Indices of the 100 SLOW networks; read by the main data loader |
| `Data/Post-i/slow/network_N/binned_firing_rates.csv` | Binned firing rates for learning stages `0, 1, 3, 8, 15, 30` |
| `Data/Post-i/slow/network_N/binarized_firing_rates.csv` | Corresponding binary activity |
| `Data/Post-i/slow/network_N/data_conf.csv` | Corresponding state identifiers |
| `Data/Post-0/slow/network_N/network_N.pickle` | Pre-learning network results and behavioral tables |
| `Data/Post-i/slow/network_N/network.pickle` | Post-learning network results for `i > 0` |
| `Data/Post-i/W_time_all_onset.csv` | Control ensemble and DDM parameter time courses for learning models, at `i = 0, 1, 3` |
| `Data/Post-i/traj_classes.pickle` | Trajectory memberships; required at `i = 0, 1, 3, 30` |
| `DDM/Post-i/slow/traj_R_static_all.csv` | Static posterior draws for all eight main trajectories at `i = 0, 1, 3`; `R` is the trajectory-type code (for example, `traj_123_static_all.csv` corresponds to I→II→III) |
| `DDM/Post-0/slow/traj_123_static_mean.csv` | Static posterior means for the Figure F.11 example |

All stored data were generated using the methods described in our previous work (https://doi.org/10.1371/journal.pcbi.1012966) with the code provided in https://github.com/zhuojunyu-appliedmath/CLAW

The notebook `manuscript/data_analysis.ipynb` analyzes CBGT simulations and static DDM fits, using Python **3.8.20** in the **cbgtpy_env** environment. The CBGT network codebase (CBGTPy) is publicly available at https://github.com/CoAxLab/CBGTPy. Detailed installation instructions and a comprehensive list of implemented functions can be found in the README.txt file within the repository.

Calculations and plotting functions specific to this manuscript are in `manuscript/analysis.py`. 
CLAW diagrams, schematics, formatted text tables, and horizontal significance bars are not plotted in the notebook. The underlying CLAW statistics and significant learning-effect bins are exported for plotting.
Run the notebook from top to bottom to generate the CLAW and learning data and the manuscript figures.
