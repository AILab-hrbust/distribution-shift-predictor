# Long Horizon Forecasting Experiments with Distribution Shift Prediction

<br>

## Introduction

This repository contains the code for the paper "To See the Big Picture: Time Series Forecasting with Distribution Shift Prediction".

The code is based on the [NeuralForecast]
https://github.com/nixtla/neuralforecast

## Key Points

This paper starts by addressing the issue of performance degradation in Transformer when dealing with non-stationary sequences, aiming to enhance the predictive performance of the current Transformer approach. The proposed solution is a universal Transformer framework that can be aware of the dynamical changes of the input's distribution. It comprises two plug-and-play modules. The Moving Normalization Kernel (MNK) separates features expressing distribution shifts from the input sequence. The Distribution Shift Predictor (DSP) models the patterns of distribution shift through it.
Implementation of these two modules is in the `./neuralforecast/models/dsp.py` and `./neuralforecast/models/mnk.py` folder. The overall structure's implementation is in the `./neuralforecast/models/patchtst_with_dsp.py` folder.
![alt text](https://github.com/Houyikai/distribution-shift-predictor/blob/main/pics/overall%20structure.png)

## Main Results

forecasting accuracy:
![alt text](https://github.com/Houyikai/distribution-shift-predictor/blob/main/pics/results.png)

computation and memory efficiency:
![alt text](https://github.com/Houyikai/distribution-shift-predictor/blob/main/pics/efficiency.png)

## Reproducibility

1. Create a conda environment `neuralforecast` using the `environment.yml` file.

```shell
conda env create -f environment.yml
```

3. Activate the conda environment using

```shell
conda activate dsp
```

then install the `datasetsforecast` package using pip:

```shell
pip install git+https://github.com/Nixtla/datasetsforecast.git
```

4. Run the experiments for each dataset and each model using with

- `--horizon` parameter in `[96, 192, 336, 720]`
- `--dataset` parameter in `['ETTh1', 'ETTh2', 'ETTm1', 'ETTm2']`
  <br>

```shell
python run_dsp.py --dataset 'ETTh1' --horizon 96 --num_samples 10
```

You can access the final forecasts from the `./data/{dataset}/{horizon}_forecasts.csv` file. Example: `./data/ETTh1/96_forecasts.csv`.

Or run the example in notebook `test_dsp.ipynb`.

<br><br>
