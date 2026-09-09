# Bike-Share Demand Forecasting with STGCN

This repository contains the supporting materials for a Deep Learning and Decision Making project on station-level bike-share demand forecasting.

The project investigates whether a geographic distance-based graph improves forecasting performance compared with an identity-graph STGCN under the same experimental setup.

## Research question

Does connecting bike-share stations according to geographic distance improve station-level demand forecasting?

The central comparison is between:

- An STGCN using an identity graph, where stations are treated independently.
- An STGCN using a geographic distance graph, where nearby stations share information.

The project also includes persistence, historical hour-of-week, and shared LSTM baselines.

## Experimental setup

- Approximately 200 bike-share stations
- Hourly pickup-demand data
- Forecast horizons of 5, 10, and 15 hours
- A 168-hour historical lookback
- Station-level demand forecasting
- A controlled comparison between identity and geographic-distance graphs

The two STGCN variants use the same general modelling and forecasting setup. The main experimental difference is the graph structure used to represent relationships between stations.

## Main result

In this experimental setting, the geographic distance graph did not improve forecasting performance.

The distance-graph STGCN achieved higher mean absolute error (MAE) than the identity-graph STGCN at the evaluated forecast horizons. This suggests that physical proximity alone was not sufficient to represent the functional relationships between bike-share stations.

This result does not imply that graph-based forecasting is ineffective in general. It suggests that richer relationships—such as trip flows, demand correlations, or learned dynamic connections—may be more useful than geographic distance alone.

## Repository structure

```text
01. Results/
├── stgcn_real_distance_15h_test_predictions.csv
├── stgcn_real_distance_10h_test_predictions.csv
├── stgcn_real_distance_5h_test_predictions.csv
├── stgcn_identity_15h_test_predictions.csv
├── stgcn_identity_10h_test_predictions.csv
├── stgcn_identity_5h_test_predictions.csv
├── shared_lstm_results.csv
├── shared_lstm_5h_test_predictions.csv
├── shared_lstm_5h_station_metrics.csv
├── master_results_final.csv
└── baseline_test_results.csv

02. Notebooks/
├── 01_data_validation_and_preprocessing.ipynb
├── 02_build_adjacency_matrices.ipynb
├── 03_baseline_forecasting.ipynb
├── 04_shared_lstm_baseline.ipynb
└── 05_stgcn_graph_ablation.ipynb

03. Models/
└── Omitted because trained checkpoint files exceed GitHub's file-size limit

04. Graphs/
├── pairwise_distance_km.npy
├── flow_counts_top_200.npy
├── adjacency_flow_knn10.npy
└── adjacency_distance_knn10.npy

05. Figures/
├── shared_lstm_5h_learning_curve.png
├── mae_four_models_cividis_style.png
├── mae_five_hour_cividis_style.png
└── graph_variants_comparison_report.png

06. Data/
├── top200_station_order.csv
├── top200_station_metadata.csv
└── processed_hourly_pickup_demand_top200.csv
```

## Folder descriptions

### `01. Results`

This folder contains final evaluation outputs, test predictions, station-level metrics, baseline results, and aggregated comparison tables.

### `02. Notebooks`

This folder contains the notebooks used for data validation, preprocessing, graph construction, baseline forecasting, shared LSTM training, and STGCN graph ablation.

Recommended execution order:

1. `01_data_validation_and_preprocessing.ipynb`
2. `02_build_adjacency_matrices.ipynb`
3. `03_baseline_forecasting.ipynb`
4. `04_shared_lstm_baseline.ipynb`
5. `05_stgcn_graph_ablation.ipynb`

### `03. Models`

Trained model checkpoint files are not included because some `.keras` and `.pt` files exceed GitHub's standard file-size limit.

The notebooks, processed data, graph arrays, final predictions, result tables, and figures are included so that the experimental workflow and reported results can be inspected.

### `04. Graphs`

This folder contains pairwise distance, flow-count, and adjacency-array files used to construct graph relationships between the top 200 stations.

### `05. Figures`

This folder contains figures used to inspect LSTM training behaviour, compare forecasting errors, and illustrate the identity and geographic-distance graph variants.

### `06. Data`

This folder contains the station ordering, station metadata, and processed hourly pickup-demand data used in the experiments.

## Report

The final report is submitted separately through Moodle and is therefore not included in this repository.

## Reproducibility note

The notebooks document the primary data-processing, graph-construction, baseline, and modelling steps. The included results, graph files, figures, and processed data support inspection of the reported experiments.

Exact reproduction may depend on the Python environment, package versions, random seeds, available hardware, and availability of the original input data.

## Author

Mathumitha

Deep Learning and Decision Making
