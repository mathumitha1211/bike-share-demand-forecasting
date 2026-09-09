# Bike-Share Demand Forecasting with STGCN

This repository contains the reproducibility materials for a Deep Learning and Decision Making project on station-level bike-share demand forecasting.

The project investigates whether a geographic distance-based graph improves forecasting performance compared with an identity-graph STGCN under the same experimental setup.

## Research question

Does connecting bike-share stations according to geographic distance improve station-level demand forecasting?

The central comparison is between:

- An STGCN using an identity graph.
- An STGCN using a geographic distance graph.

The project also includes persistence, historical hour-of-week, and shared LSTM baselines.

## Experimental setup

- Approximately 200 bike-share stations.
- Hourly pickup-demand data.
- Forecast horizons of 5, 10, and 15 hours.
- A 168-hour historical lookback.
- Station-level demand forecasting.
- Controlled comparison between identity and geographic-distance graphs.

The two STGCN variants use the same general modelling and forecasting setup. The main experimental difference is the graph structure used to represent relationships between stations.

## Main result

In this experimental setting, the geographic distance graph did not improve forecasting performance.

The distance-graph STGCN achieved higher MAE than the identity-graph STGCN at the evaluated forecast horizons. This suggests that physical proximity alone was not sufficient to represent the functional relationships between bike-share stations.

This result does not imply that graph-based forecasting is ineffective in general. It indicates that richer relationships—such as trip flows, demand correlations, or learned dynamic connections—may be more useful than geographic distance alone.

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
├── stgcn_real_distance_15h_best.keras
├── stgcn_real_distance_10h_best.keras
├── stgcn_real_distance_5h_best.keras
├── stgcn_identity_15h_best.keras
├── stgcn_identity_10h_best.keras
├── stgcn_identity_5h_best.keras
├── shared_lstm_15h_best.pt
├── shared_lstm_10h_best.pt
└── shared_lstm_5h_best.pt

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

This folder contains final evaluation outputs, predictions, station-level metrics, baseline results, and aggregated comparison tables.

### `02. Notebooks`

This folder contains the notebooks used for data validation, preprocessing, graph construction, baseline forecasting, LSTM training, and STGCN graph ablation.

The recommended execution order is:

1. `01_data_validation_and_preprocessing.ipynb`
2. `02_build_adjacency_matrices.ipynb`
3. `03_baseline_forecasting.ipynb`
4. `04_shared_lstm_baseline.ipynb`
5. `05_stgcn_graph_ablation.ipynb`

### `03. Models`

This folder contains the saved trained model checkpoints for the evaluated forecast horizons and graph variants.

The `.keras` files contain STGCN models. The `.pt` files contain the shared LSTM model checkpoints.

### `04. Graphs`

This folder contains the distance, flow, and adjacency-array files used to construct graph relationships between stations.

### `05. Figures`

This folder contains figures used to inspect training behaviour, compare forecasting errors, and illustrate the graph variants.

### `06. Data`

This folder contains station ordering, station metadata, and the processed hourly pickup-demand data used in the experiments.


## Report

The final report is submitted separately through Moodle and is therefore not included in this repository.

## Reproducibility note

The notebooks document the main data-processing, graph-construction, baseline, and modelling steps. The saved results and model files are included to support inspection of the reported experiments.

Exact reproduction may depend on the Python environment, package versions, random seeds, hardware, and available input data.

## Author

Mathumitha

Deep Learning and Decision Making
