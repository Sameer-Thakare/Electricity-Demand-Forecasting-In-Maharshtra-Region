# Electricity Demand Forecasting with Prophet for Maharshtra Region

This project demonstrates how to forecast electricity demand using Facebook's Prophet library in Python. The project utilizes historical demand data to predict future demand, making it useful for energy management, planning, and operational efficiency.

## Table of Contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Installation](#installation)
- [Data Preparation](#data-preparation)
- [Usage](#usage)
- [Results](#results)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)

## Overview

Forecasting electricity demand is crucial for the efficient management of power resources. This project provides an end-to-end guide on how to:

1. Prepare time series data for Prophet.
2. Train the model on historical demand data.
3. Generate and visualize demand forecasts.

Prophet, a forecasting tool developed by Facebook, is particularly effective for time series data with daily or weekly seasonal patterns and missing data.

## Requirements

- Python 3.7 or later
- Libraries:
  - `prophet`
  - `pandas`
  - `matplotlib`
  
## Installation

1. **Clone this repository**:
    ```bash
    git clone https://github.com/your-username/electricity-demand-forecasting.git
    cd electricity-demand-forecasting
    ```

2. **Set up a virtual environment** (recommended):
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install required packages**:
    ```bash
    pip install -r requirements.txt
    ```

*Note: You may need to install `prophet` separately depending on your platform.*

## Data Preparation

The data should be in CSV format with two columns:
- `ds`: Date column in `YYYY-MM-DD HH:MM:SS` format.
- `y`: Numeric column representing electricity demand values.

Rename your columns if they don’t match this format, as Prophet requires `ds` and `y` for time series forecasting.

Example of data format:
```plaintext
ds,y
2023-01-01,450
2023-01-02,460
...
```

## Usage

1. **Load and prepare your data**:
    ```python
    import pandas as pd
    from prophet import Prophet

    data = pd.read_csv('electricity_demand.csv')
    data['ds'] = pd.to_datetime(data['ds'])  # Ensure date column is in datetime format
    ```

2. **Train the model**:
    ```python
    model = Prophet()
    model.fit(data)
    ```

3. **Forecast future demand**:
    ```python
    future = model.make_future_dataframe(periods=30)  # Forecasting for the next 30 days
    forecast = model.predict(future)
    ```

4. **Visualize the results**:
    ```python
    model.plot(forecast)
    ```

Run the notebook `electricity_demand_forecasting.ipynb` for a step-by-step guide.

## Results

The model outputs a forecast of electricity demand along with components showing the trend, daily, and weekly seasonality.

## Customization

- **Forecast Period**: Modify `periods` in `make_future_dataframe()` to set the number of days.
- **Seasonality**: Prophet allows custom seasonality adjustments. Refer to the [Prophet documentation](https://facebook.github.io/prophet/) for details.

## Contributing

Contributions are welcome! Please submit a pull request or open an issue if you have suggestions or improvements.

## License

This project is licensed under the MIT License.
