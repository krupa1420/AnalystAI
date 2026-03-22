# LA Metro Bike-Share 2024

Real LA Metro Bike-Share data for 2024.
Clean and ready to use.

## Contents
- `bikeshare_2024.sqlite` - SQLite database with 3 tables

## Tables

### trips (519,235 rows)
| Column | Description |
|--------|-------------|
| trip_id | Unique trip identifier |
| start_time | Trip start timestamp |
| end_time | Trip end timestamp |
| duration_minutes | Trip duration in minutes |
| start_station | Start station ID |
| end_station | End station ID |
| bike_type | Electric or Standard |
| passholder_type | Monthly Pass, Walk-up, Flex Pass |
| trip_route_category | One Way or Round Trip |

### stations (226 rows)
| Column | Description |
|--------|-------------|
| station_id | Unique station identifier |
| station_name | Station name |
| region | Area (DTLA, Venice, etc.) |
| lat | Latitude |
| lon | Longitude |

### weather (8,784 rows)
| Column | Description |
|--------|-------------|
| timestamp | Hourly timestamp |
| temp_c | Temperature in Celsius |
| rel_humidity | Relative humidity % |
| precip_mm | Precipitation in mm |
| wind_speed_mps | Wind speed m/s |
| pressure_hpa | Pressure in hPa |
| weather_code | Weather condition code |

## Usage
```python
import sqlite3
import pandas as pd
from huggingface_hub import hf_hub_download

db_path = hf_hub_download(
    repo_id   = "Krupa1420/la-metro-bikeshare-2024",
    filename  = "bikeshare_2024.sqlite",
    repo_type = "dataset"
)

conn = sqlite3.connect(db_path)
df = pd.read_sql("SELECT * FROM trips LIMIT 5", conn)
print(df)
```

## Source
LA Metro Bike Share Open Data
