# Delivery Performance Analysis

A Python script that reads shipment data from a CSV file, cleans it, runs data-quality checks, and prints a complete delivery performance report in the console.

## Features

- Cleans dates, numeric fields and order status text
- Calculates delivery duration (`Delivery_Days`) per shipment
- Detects **duplicate shipment IDs** and **invalid delivery records** (negative delivery days)
- Computes overall KPIs (delivery rate, average delivery days, average rating, shipping costs)
- Generates summaries by **status, city, region, delivery partner and shipping method**
- Reports missing values per column

## Requirements

- Python 3.8 or later
- pandas

```bash
pip install pandas
```

## Input File

Place `delivery_data_set.csv` in the same folder as the script. It must contain these columns:

| Column | Description |
|--------|-------------|
| `Shipment_ID` | Unique shipment identifier |
| `Order_Date` | Date the order was placed |
| `Delivery_Date` | Date the order was delivered |
| `Shipping_Cost` | Cost of shipping |
| `Customer_Rating` | Customer rating for the delivery |
| `Order_Status` | Status, e.g. `Delivered` |
| `Customer_City` | Customer's city |
| `Region` | Delivery region |
| `Delivery_Partner` | Courier or delivery company |
| `Shipping_Method` | Shipping method used |

## Usage

```bash
python your_script_name.py
```

Replace `your_script_name.py` with the name of your Python file.

If the CSV is missing, the script prints `Error: delivery_data_set.csv not found.` and stops.

## Report Sections

1. **KPI Summary** - total shipments, delivered shipments, delivery rate, average delivery days, average rating, total and average shipping cost, duplicate IDs, invalid records
2. **Status Summary** - shipments per order status
3. **City Summary** - shipments, delivered count, average shipping cost
4. **Region Summary** - shipments, delivered count, average shipping cost
5. **Delivery Partner Summary** - shipments, delivered count, average delivery days, average rating
6. **Shipping Method Summary** - shipments, delivered count, average cost, average delivery days
7. **Missing Values Summary** - null count per column
8. **Duplicate Shipments** - full list of duplicate rows
9. **Invalid Delivery Records** - rows where delivery date is before order date

## KPI Definitions

| Metric | Formula |
|--------|---------|
| Delivery Rate (%) | Delivered shipments / Total shipments x 100 |
| Average Delivery Days | Mean of `Delivery_Days` (delivered shipments only) |
| Average Customer Rating | Mean of `Customer_Rating` (delivered shipments only) |
| Total / Average Shipping Cost | Sum / mean of `Shipping_Cost` (all shipments) |

## Notes and Limitations

- Duplicate and invalid records are reported but **not removed** from the calculations.
- The `Delivered` status match is case-sensitive.
- Output is console only; results are not saved to a file.

## Possible Improvements

- Accept the input file path as a command-line argument
- Export results to Excel or CSV
- Add charts with matplotlib
- Add delivery rate per city, region, partner and method
- Add an on-time delivery metric

## Documentation

See `Neelam_onlineshoping_srs.pdf` for the Software Requirements Specification.

## License

Add your preferred license here (e.g. MIT).
