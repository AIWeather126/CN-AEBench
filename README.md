![WeatherAirSN Dataset](./static/title.png)

This is the official repository for the paper "WeatherAirSN: A Multi-Source Sparse Spatiotemporal Dataset Integrating Weather Observations, Air Quality Monitoring, and NWP for Meteorological and Environmental Applications".

---

Dataset validity (extreme events) research and visualization, benchmark test for details, please visit: https://aiweather126.github.io/WeatherAirSN/pages

To download the dataset & code, please visit: https://huggingface.co/datasets/AIWeather126/WeatherAirSN

---

*WeatherAirSN* is a comprehensive multi-source atmospheric & environmental dataset integrating ground observations, air quality monitoring, and ECMWF NWP data. 

![WeatherAirSN Station Distribution](./static/distribution.png)

📊 Data Coverage: 2023-2025-Future

🌍 Stations: 2,250+

⏱️ Resolution: 1 Hour

## 1. Variable Information
#### Static Descriptive Information Table

| No. | Variable Name | Unit | Description |
|-----|--------------|------|-------------|
| 1 | altitude | m | Station elevation |
| 2 | lon | degree | Station longitude |
| 3 | lat | degree | Station latitude |
| 4 | station_province | -- | Province where station is located |
| 5 | station_city | -- | City where station is located |
| 6 | station_id | -- | Station identifier |
| 7 | type | -- | Land use type at station location |


#### Multi-source Variable Description Table

| No. | Variable Name | Unit | Description |
|-----|--------------|------|-------------|
| 1 | ws_2min | m/s | 2-minute average wind speed |
| 2 | ws_10min | m/s | 10-minute average wind speed |
| 3 | wd_2min | degree | 2-minute average wind direction |
| 4 | wd_10min | degree | 10-minute average wind direction |
| 5 | wd_instant | degree | Instantaneous wind direction |
| 6 | ws_instant | m/s | Instantaneous wind speed |
| 7 | vis | m | Horizontal visibility |
| 8 | t | °C | Air temperature |
| 9 | dt | °C | Dew point temperature |
| 10 | precipitation | mm | Hourly precipitation |
| 11 | rh | % | Relative humidity |
| 12 | p | hPa | Atmospheric pressure |
| 13 | slp | hPa | Sea level pressure |
| 14 | vapor | hPa | Vapor pressure |
| 15 | phenomena | -- | Weather phenomena |
| 16 | ec_vis | m | NWP horizontal visibility |
| 17 | ec_sh2 | kg/kg | NWP 2m specific humidity |
| 18 | ec_t2m | °C | NWP 2m air temperature |
| 19 | ec_d2m | °C | NWP 2m dew point temperature |
| 20 | ec_sp | hPa | NWP surface pressure |
| 21 | ec_msl | hPa | NWP mean sea level pressure |
| 22 | ec_u10 | m/s | NWP 10m u-component of wind |
| 23 | ec_v10 | m/s | NWP 10m v-component of wind |
| 24 | ec_rh | % | NWP relative humidity (diagnostic variable) |
| 25 | ec_ws | m/s | NWP wind speed (diagnostic variable) |
| 26 | ec_wd | degree | NWP wind direction (diagnostic variable) |
| 27 | AQI | -- | Real-time AQI value |
| 28 | PM2.5 | μg/m³ | Hourly mean PM2.5 concentration |
| 29 | PM10 | μg/m³ | Hourly mean PM10 concentration |
| 30 | SO2 | μg/m³ | Hourly mean SO2 concentration |
| 31 | NO2 | μg/m³ | Hourly mean NO2 concentration |
| 32 | O3 | μg/m³ | Hourly mean O3 concentration |
| 33 | CO | mg/m³ | Hourly mean CO concentration |

## 2. Experiment Settings and Information
The experiment was conducted on WeatherAirSN-L3. 
To standardize the conditions, we set the time interval for the first version of L3 to 2023.09.01–2025.07.31. You may also choose to run your experiments on this version.

### 2.1 Research Area
We selected four representative regions across China for comprehensive evaluation:

🏔️ Lanzhou Urban Agglomeration
- Northwest China
- Characterized by arid climate, complex terrain, and frequent dust events influenced by the Gobi Desert.

🌺 Kunming Urban Agglomeration
- Southwest China
- Located in the Yunnan-Guizhou Plateau with mild climate year-round and unique monsoon patterns.

❄️ Harbin Urban Agglomeration
- Northeast China
- Features extreme continental climate with harsh winters and significant seasonal variations.

🌊 Shanghai
- East Coast
- China's economic hub with subtropical monsoon climate, urban heat island effects, and typhoon influences.

Each region is trained and tested independently to ensure robust regional performance.
### 2.2 Data Split Strategy
Overall ratio - Training:Validation:Test = 7:1:2

Validation Set: Days 1-10 of Oct 2023, Jan/Apr/Jul/Sep/Dec 2024, Mar/Jun 2025

Test Set: Days 14-end of the same months

Training Set: All remaining data

### 2.3 Experimental Setup
- Short-term Prediction

Configuration: 24 steps → 1\4\12\24 steps

Evaluation: Lead times at 1h (nowcasting), 4h, 12h, 24h (short-term), and overall performance

- Long-term Prediction

Configuration: 48 steps → 1\24\48\72\96\120 steps

Evaluation: Lead times at 1h (nowcasting), 24h, 48h, 72h, 96h, 120h (extended range), and overall performance

The training configuration was as follows: maximum epochs were set to 500 with 
an early stopping patience of 30 epochs. We employed the Adam optimizer with an 
initial learning rate of 0.001, coupled with a MultiStepLR scheduler for learning 
rate decay. The batch size was set to 512. All reported results were obtained by 
selecting the checkpoint with the lowest validation loss and evaluating it on the 
held-out test set to ensure unbiased performance assessment.

All experiments were conducted on a single server equipped with 4× NVIDIA A100 GPUs, an Intel Xeon Ice Lake processor (32 cores, 64 threads at 2.6GHz), 
and 188GB RAM. The system runs Ubuntu Linux with CUDA 11.7 and PyTorch 1.13. 

Experiment results: https://aiweather126.github.io/WeatherAirSN/pages

## 3. Data Availability
We will make the dataset and code available for download once the paper is completed(L3 has been made public). Please wait for further updates.


---
Domain:
- weather & climate
- Air quality and environment
- NWP
- Assimilation
